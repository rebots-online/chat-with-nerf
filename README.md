# :sauropod: Chat with NeRF

## :bulb: Highlight

- **Open-Vocabulary 3D Localization.** Localize **everything** with language!
- **Dynamic Grounding.** Humans will be able to chat with agent to localize novel objects.

## :fire: News
[2023-05-15] The first version of chat-with-nerf is available now! Please try out demo!
## :star: Explanations/Tips for Chat with NeRF Inputs and Outputs

## :label: TODO

## :hammer_and_wrench: Install

To install the dependencies we provide a Dockerfile:
```bash
docker build -t chat-with-nerf:latest .
```
Or if you want to pull remote image from Dockerhub to save significant time, please try:
```bash
docker pull jedyang97/chat-with-nerf:latest
```

Otherwise, if you prefer build it locally:
```bash
conda create --name nerfstudio -y python=3.8
conda activate nerfstudio
pip install torch==1.13.1 torchvision functorch --extra-index-url https://download.pytorch.org/whl/cu117
pip install ninja git+https://github.com/NVlabs/tiny-cuda-nn/#subdirectory=bindings/torch
pip install nerfstudio

git clone https://github.com/kerrj/lerf
python -m pip install -e .
ns-train -h
```
Note that specific CUDA 11.3 is required. For further information, please check NeRFStudio installation
guide.

Then locally you need to run
```bash
git clone https://github.com/sled-group/chat-with-nerf.git
```
If using Docker, you can use the following command to spin up a docker container with **chat-with-nerf** mounted under workspace
```bash
docker run --gpus "device=0" -v /<parent_path_chat-with-nerf>/:/workspace/ -v /home/<your_username>/.cache/:/home/user/.cache/ --rm -it --shm-size=12gb chat-with-nerf:latest
```
Then install Chat with NeRF dependencies
```bash
cd /workspace/chat-with-nerf
pip install -e .
pip install -e .[dev]
```
(or use your favorite virtual environment manager)

To run the demo:

```
cd /workspace/chat-with-nerf
export $(cat .env | xargs); gradio chat_with_nerf/app.py
```
