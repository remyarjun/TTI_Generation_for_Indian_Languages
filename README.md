# Photo-realistic Image Generation using Text Descriptions in Indian Languages: An Exploration Study
PyTorch implementation for recreating the key results of the TTI_Malayalam and TTI_Hindi models in the paper [Photo-realistic Image Generation using Text Descriptions in Indian Languages: An Exploration Study]() by Remya Gopalakrishnan and Sudeep P V.

Generalized architectures of the TTI generation models and the images generated by the models are given below.

![Figure1](https://github.com/user-attachments/assets/cbaac273-4ee3-462f-a07b-8e1873cd092e)

## Code Setup

Code is implemented in a local workstation NVIDIA DGX Station A100 Version 5.1.0 and our local machine NVIDIA Quadro RTX 8000.

## Dependencies
* `python 3.6.13`
* `Pytorch 1.6.0`
* `python-dateutil 2.8.1`
* `easydict 1.9`
* `nltk 3.5`
  
## Data
* Add our preprocessed metadata of [flower](https://drive.google.com/drive/u/4/folders/1v4E8TsU73HI-3FfcEN_dc_OGjhrW9WvX), [bird](https://drive.google.com/drive/u/4/folders/1vkho36Lva15GhAFoMu9t8q3o6E_ojcYr), and [coco](https://drive.google.com/drive/u/4/folders/1ARlHHIEYx_2bcOH1gOtsf-GLpIqNXEvj) to your directory and save them to data/.
* Download the [flower](https://www.robots.ox.ac.uk/~vgg/data/flowers/102/) dataset and extract them to data/flower/.
* Download the [birds](https://www.vision.caltech.edu/datasets/cub_200_2011/) dataset and extract them to data/bird/birds/.
* Download the [coco](https://cocodataset.org/#download) dataset and extract the images to data/coco/.


## Training
* Pre-train encoder models: Use this [flower](https://drive.google.com/drive/u/4/folders/1G4_YDsRA89dI78_OyTsyS7JJJZPd_ooA?usp=sharing), [bird](https://drive.google.com/drive/u/4/folders/1G4_YDsRA89dI78_OyTsyS7JJJZPd_ooA?usp=sharing), and [coco](https://drive.google.com/drive/u/4/folders/1G4_YDsRA89dI78_OyTsyS7JJJZPd_ooA?usp=sharing) files to train the encoder models.
* Train models: Use this [AttnGAN](https://drive.google.com/drive/u/4/folders/1Q9YeaKjVWWXYoZeQb1Bz0nAChep-9YW7?usp=sharing), [DMGAN](https://drive.google.com/drive/u/4/folders/1Q9YeaKjVWWXYoZeQb1Bz0nAChep-9YW7?usp=sharing), and [DFGAN](https://drive.google.com/drive/u/4/folders/1Q9YeaKjVWWXYoZeQb1Bz0nAChep-9YW7?usp=sharing) files for training the models.
* *.yml files are example configuration files for training/evaluating our models.

## Pretrained Models
### Encoder

* [DMGAN_Malayalam](https://drive.google.com/drive/folders/1bh12Mz3HCx3MqmaP4E5vKIe3Kayv-KFj?usp=sharing), [DMGAN_Hindi](https://drive.google.com/drive/u/4/folders/1bh12Mz3HCx3MqmaP4E5vKIe3Kayv-KFj?usp=sharing) for `flower`.
* [DMGAN_Malayalam](https://drive.google.com/drive/u/4/folders/1bh12Mz3HCx3MqmaP4E5vKIe3Kayv-KFj?usp=sharing), [DMGAN_Hindi](https://drive.google.com/drive/u/4/folders/1bh12Mz3HCx3MqmaP4E5vKIe3Kayv-KFj?usp=sharing) for `bird`.
* [DMGAN_Malayalam](https://drive.google.com/drive/u/4/folders/1bh12Mz3HCx3MqmaP4E5vKIe3Kayv-KFj?usp=sharing), [DMGAN_Hindi](https://drive.google.com/drive/u/4/folders/1bh12Mz3HCx3MqmaP4E5vKIe3Kayv-KFj?usp=sharing) for `coco`.

### Pretrained Models

* [TTI_Malayalam](https://drive.google.com/drive/u/4/folders/1gLZXKaaMagdsI8QpuVe3O2qtAUuQMhhn?usp=sharing), [TTI_Hindi](https://drive.google.com/drive/u/4/folders/1gLZXKaaMagdsI8QpuVe3O2qtAUuQMhhn?usp=sharing) for `flower`.
* [TTI_Malayalam](https://drive.google.com/drive/u/4/folders/1gLZXKaaMagdsI8QpuVe3O2qtAUuQMhhn?usp=sharing), [TTI_Hindi](https://drive.google.com/drive/u/4/folders/1gLZXKaaMagdsI8QpuVe3O2qtAUuQMhhn?usp=sharing) for `bird`.
* [TTI_Malayalam](https://drive.google.com/drive/u/4/folders/1gLZXKaaMagdsI8QpuVe3O2qtAUuQMhhn?usp=sharing), [TTI_Hindi](https://drive.google.com/drive/u/4/folders/1gLZXKaaMagdsI8QpuVe3O2qtAUuQMhhn?usp=sharing) for `coco`.

## Sampling
* For sampling we need to change configurations in cfg file.
* To generate images for the pre-extracted embeddings: Set `cfg.TRAIN.FLAG = False` and `cfg.B_VALIDATION = True`.
* To generate images for custom text input: Set `cfg.TRAIN.FLAG = False` and `cfg.B_VALIDATION = False`.

## Validation
* We compute inception score for models trained on birds using [StackGAN-inception-model](https://github.com/hanzhanggit/StackGAN-inception-model).
* We compute inception score for models trained on coco using [improved-gan/inception_score](https://github.com/openai/improved-gan/tree/master/inception_score).
* We compute FID score for models using [https://github.com/mseitzer/pytorch-fid/tree/802da3963113b5b5f8154e0e27580ee4c97460ab].
 
## Results
The below are the example images generated by AttnGAN, DMGAN, and DFGAN models on the Oxford-102 (left), CUB (middle), and COCO (right) datasets.

* The ground truth images for the given captions are listed in the first row
* The images in the remaining rows represent the TTI model results on English, Hindi, and Malayalam captions, respectively.
  
![Figure2](https://github.com/user-attachments/assets/a6f88c3f-037f-48da-9be5-8abdd342200d)

## Citation
If you find TTI_Generation_for_Indian_Languages useful in your research, please consider citing:
```
@article{
  author    = {R. Gopalakrishnan, P. V. Sudeep},
  title     = {Photo-realistic Image Generation using Text Descriptions in Indian Languages: An Exploration Study},
  Year      = {2025},
  booktitle = {}
}
```

## References

* [AttnGAN: Fine-Grained Text to Image Generation with Attentional Generative Adversarial Networks [code]](https://github.com/taoxugit/AttnGAN)
* [DM-GAN: Dynamic Memory Generative Adversarial Networks for Text-to-Image Synthesis [code]](https://github.com/MinfengZhu/DM-GAN)
* [DF-GAN: A Simple and Effective Baseline for Text-to-Image Synthesis [code]](https://github.com/tobran/DF-GAN)
* [102 Category Flower Dataset [data]](https://www.robots.ox.ac.uk/~vgg/data/flowers/102/)
* [Caltech-UCSD Birds-200-2011 (CUB-200-2011) [data]](https://www.vision.caltech.edu/datasets/cub_200_2011/)
* [COCO Common Objects in Context [data]](https://cocodataset.org/#download)
