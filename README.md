# PixelArtistry Trellis2 GGUF

One-click installer for the GGUF versions of Trellis2 and Pixal3D in ComfyUI Easy-Install. These are the GGUF workflows from my 6 GB videos. They run on cards with 6 to 8 GB of VRAM.

Part of the PixelArtistry Trellis2 + Pixal3D Workflow Pack. The handbook covers the workflows in Chapter 9.

## What you need

- Windows 10 or 11 and an NVIDIA RTX 30-series card or newer
- [ComfyUI Easy-Install](https://github.com/Tavris1/ComfyUI-Easy-Install/releases/latest) with Python 3.12, PyTorch 2.8.0 and CUDA 12.8 (run `Add-Ons\Torch-Pack\Torch 2.8.0+cu128.bat` first)
- visualbruno's [ComfyUI-Trellis2](https://github.com/visualbruno/ComfyUI-Trellis2), installed with the Trellis2 file in your `Add-Ons` folder. The GGUF workflows use its nodes for everything except the model loader, so install it first.

## Install

1. Download both `.bat` files from this repo.
2. Put them into your `ComfyUI-Easy-Install\Add-Ons` folder.
3. Close ComfyUI.
4. Run `Trellis2 GGUF (requires Torch 2.8.0+cu128).bat`. It checks your Python, PyTorch and CUDA versions first and stops if they don't match.
5. Run `Trellis2_gguf_model_downloader.bat`. It downloads the Trellis2 Q4_K_M models into `ComfyUI\models\Trellis2`. Run it even if you only use Pixal3D, because the Pixal3D GGUF workflows read one Trellis2 decoder file.
6. Start ComfyUI.

The Pixal3D GGUF models download by themselves the first time you run a Pixal3D GGUF workflow.

## What the installer does

- Installs [ComfyUI-Trellis2-GGUF by Aero-Ex](https://github.com/Aero-Ex/ComfyUI-Trellis2-GGUF) into `ComfyUI\custom_nodes`
- Installs the precompiled parts (CuMesh, nvdiffrast, nvdiffrec_render, FlexGEMM, O-Voxel) from visualbruno's Python 3.12 wheels
- Downloads DINOv3 ViT-L/16 into `ComfyUI\models\facebook\dinov3-vitl16-pretrain-lvd1689m`
- Sets NumPy back to 1.26.4

It's safe to run again. It removes the old install and puts everything back.

## Models

| Model | Size | Folder |
|---|---|---|
| Trellis2 GGUF Q4_K_M | 6.7 GB | `ComfyUI\models\Trellis2` |
| Trellis2 GGUF Q8_0 | 9.9 GB | `ComfyUI\models\Trellis2` |
| Pixal3D GGUF Q4_K_M | 5.9 GB | `ComfyUI\models\Pixal3D-GGUF` |
| Pixal3D GGUF Q8_0 | 8.6 GB | `ComfyUI\models\Pixal3D-GGUF` |
| DINOv3 ViT-L/16 | 1.2 GB | `ComfyUI\models\facebook\dinov3-vitl16-pretrain-lvd1689m` |

Pick one quant per model. Q4_K_M is the low-VRAM choice, Q8_0 is closer to the full model. The GGUF folders have to sit in the main `ComfyUI\models` folder. A shared model folder from `extra_model_paths.yaml` is not searched.

## Tested with

| What | Version |
|---|---|
| ComfyUI | 0.39.2 |
| Python, PyTorch, CUDA | 3.12.10, 2.8.0, 12.8 |
| ComfyUI-Trellis2 (visualbruno) | commit `1459741` |
| ComfyUI-Trellis2-GGUF (Aero-Ex) | commit `b3b9e95` |
| GPU | RTX 5080 16 GB |

## Credits

- The installer is based on the add-on scripts from [ComfyUI Easy-Install](https://github.com/Tavris1/ComfyUI-Easy-Install) by ivo (Tavris1), MIT License, Copyright (c) 2024 ivo (Tavris1).
- [ComfyUI-Trellis2-GGUF](https://github.com/Aero-Ex/ComfyUI-Trellis2-GGUF) and the GGUF models by Aero-Ex
- [ComfyUI-Trellis2](https://github.com/visualbruno/ComfyUI-Trellis2) and the precompiled wheels by visualbruno
- TRELLIS.2 by Microsoft, Pixal3D by Tsinghua University and Tencent ARC, DINOv3 by Meta (DINOv3 License)

Each node pack and model keeps its own license.
