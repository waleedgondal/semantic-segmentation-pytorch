# Semantic Segmentation on MIT ADE20K dataset in PyTorch

This is a PyTorch implementation of semantic segmentation models on MIT ADE20K scene parsing dataset.

Follow the link below to find the repository for our dataset and implementations on Caffe and Torch7:

https://github.com/CSAILVision/sceneparsing

<img src="./teaser/validation_ADE_val_00000278.png" width="900"/>
<img src="./teaser/validation_ADE_val_00001519.png" width="900"/>

## Supported models:
- vgg16_dilated
- vgg19_dilated
- resnet34_dilated16
- resnet34_dilated8
- resnet50_dilated16
- resnet50_dilated8


## Training
1. Download the ADE20K scene parsing dataset:
```bash
chmod +x download_ADE20K.sh
./download_ADE20K.sh
```
2. Train a network: (default: ResNet34-dilated8)
```bash
python train.py
```

3. Input arguments: (see full input arguments via ```python train.py -h ```)
```bash
usage: train.py [-h] [--id ID] [--arch_encoder ARCH_ENCODER]
                [--arch_decoder ARCH_DECODER]
                [--weights_encoder WEIGHTS_ENCODER]
                [--weights_decoder WEIGHTS_DECODER] [--fc_dim FC_DIM]
                [--list_train LIST_TRAIN] [--list_val LIST_VAL]
                [--root_img ROOT_IMG] [--root_seg ROOT_SEG]
                [--num_gpus NUM_GPUS]
                [--batch_size_per_gpu BATCH_SIZE_PER_GPU]
                [--num_epoch NUM_EPOCH] [--optim OPTIM]
                [--lr_encoder LR_ENCODER] [--lr_decoder LR_DECODER]
                [--lr_step LR_STEP] [--beta1 BETA1]
                [--weight_decay WEIGHT_DECAY] [--fix_bn FIX_BN]
                [--num_val NUM_VAL] [--workers WORKERS] [--imgSize IMGSIZE]
                [--segSize SEGSIZE] [--segDepth SEGDEPTH] [--flip FLIP]
                [--seed SEED] [--ckpt CKPT] [--vis VIS]
                [--disp_iter DISP_ITER] [--eval_epoch EVAL_EPOCH]
                [--ckpt_epoch CKPT_EPOCH]
```


## Evaluation
1. Evaluate a trained network on the validation set:
```bash
python eval.py --id MODEL_ID
```

2. Input arguments: (see full input arguments via ```python eval.py -h ```)
```bash
usage: eval.py [-h] --id ID [--suffix SUFFIX] [--arch_encoder ARCH_ENCODER]
               [--arch_decoder ARCH_DECODER] [--fc_dim FC_DIM]
               [--list_val LIST_VAL] [--root_img ROOT_IMG]
               [--root_seg ROOT_SEG] [--num_val NUM_VAL]
               [--batch_size BATCH_SIZE] [--imgSize IMGSIZE]
               [--segSize SEGSIZE] [--segDepth SEGDEPTH] [--ckpt CKPT]
               [--visualize VISUALIZE] [--result RESULT]
```


## Test/Inference
1. Do inference on a single image:
```bash
python test.py --id MODEL_ID --test_img TEST_IMG
```
2. Input arguments: (see full input arguments via ```python test.py -h ```)
```bash
usage: test.py [-h] --id ID [--suffix SUFFIX] [--arch_encoder ARCH_ENCODER]
               [--arch_decoder ARCH_DECODER] [--fc_dim FC_DIM] --test_img
               TEST_IMG [--num_val NUM_VAL] [--batch_size BATCH_SIZE]
               [--imgSize IMGSIZE] [--segSize SEGSIZE] [--segDepth SEGDEPTH]
               [--ckpt CKPT] [--visualize VISUALIZE] [--result RESULT]
```

## Reference

If you find the code or pre-trained models useful, please cite the following paper:

Scene Parsing through ADE20K Dataset. B. Zhou, H. Zhao, X. Puig, S. Fidler, A. Barriuso and A. Torralba. Computer Vision and Pattern Recognition (CVPR), 2017. (http://people.csail.mit.edu/bzhou/publication/scene-parse-camera-ready.pdf)

    @inproceedings{zhou2017scene,
        title={Scene Parsing through ADE20K Dataset},
        author={Zhou, Bolei and Zhao, Hang and Puig, Xavier and Fidler, Sanja and Barriuso, Adela and Torralba, Antonio},
        booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
        year={2017}
    }
    
Semantic Understanding of Scenes through ADE20K Dataset. B. Zhou, H. Zhao, X. Puig, S. Fidler, A. Barriuso and A. Torralba. arXiv:1608.05442. (https://arxiv.org/pdf/1608.05442.pdf)

    @article{zhou2016semantic,
      title={Semantic understanding of scenes through the ade20k dataset},
      author={Zhou, Bolei and Zhao, Hang and Puig, Xavier and Fidler, Sanja and Barriuso, Adela and Torralba, Antonio},
      journal={arXiv preprint arXiv:1608.05442},
      year={2016}
    }
