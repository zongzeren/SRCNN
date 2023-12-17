# SRCNN

## Differences from the original

- Added the zero-padding
- Used the Adam instead of the SGD
- Removed the weights initialization

## Requirements

- PyTorch 1.0.0
- Numpy 1.15.4
- Pillow 5.4.1
- h5py 2.8.0
- tqdm 4.30.0



## Train

The 91-image, Set5 dataset converted to HDF5 can be downloaded from the links below.

| Dataset | Scale | Type | Link |
|---------|-------|------|------|
| 91-image | 2 | Train | [Download](https://www.dropbox.com/s/2hsah93sxgegsry/91-image_x2.h5?dl=0) |
| 91-image | 3 | Train | [Download](https://www.dropbox.com/s/curldmdf11iqakd/91-image_x3.h5?dl=0) |
| 91-image | 4 | Train | [Download](https://www.dropbox.com/s/22afykv4amfxeio/91-image_x4.h5?dl=0) |
| Set5 | 2 | Eval | [Download](https://www.dropbox.com/s/r8qs6tp395hgh8g/Set5_x2.h5?dl=0) |
| Set5 | 3 | Eval | [Download](https://www.dropbox.com/s/58ywjac4te3kbqq/Set5_x3.h5?dl=0) |
| Set5 | 4 | Eval | [Download](https://www.dropbox.com/s/0rz86yn3nnrodlb/Set5_x4.h5?dl=0) |

Otherwise, you can use `prepare.py` to create custom dataset.

```bash
python train.py --train-file "SRCNN/91-image_x3.h5" \
                --eval-file "SRCNN/Set5_x3.h5" \
                --outputs-dir "SRCNNH/outputs" \
                --scale 3 \
                --lr 1e-4 \
                --batch-size 16 \
                --num-epochs 400 \
                --num-workers 8 \
                --seed 123                
```



## Test

After training, you will get a best.pth under the corresponding output folder

```bash
python test.py --weights-file "SRCNN/output/x3/best.pth" \
               --image-file "SRCNN/data/1.bmp" \
               --scale 3
```

## Results

We used the network settings for experiments, i.e., $f_1=9,f_2=5,f_3=5,n_1=64,n_2=32,n_3=1$ 

PSNR was calculated on the Y channel.

### Set5

| Eval. Mat | Scale | SRCNN | SRCNN (Ours) |
|-----------|-------|-------|--------------|
| PSNR | 2 | 36.66 | 36.87 |
| PSNR | 3 | 32.75 | 33.36 |
| PSNR | 4 | 30.49 | 30.69 |

<table>
    <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/butterfly_GT.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/butterfly_GT_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/butterfly_GT_srcnn_x3.bmp"></center>
    	</td>
    </tr>
    <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/zebra.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/zebra_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/zebra_srcnn_x3.bmp"></center>
    	</td>
    </tr>
    <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/ppt3.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/ppt3_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/ppt3_srcnn_x3.bmp"></center>
    	</td>
    </tr>
        <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/2.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/2_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/2_srcnn_x3.bmp"></center>
    	</td>
    </tr>
        <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/3.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/3_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/3_srcnn_x3.bmp"></center>
    	</td>
    </tr>
        <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/4.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/4_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/4_srcnn_x3.bmp"></center>
    	</td>
    </tr>
        <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/5.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/5_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/5_srcnn_x3.bmp"></center>
    	</td>
    </tr>
        <tr>
        <td><center>Original</center></td>
        <td><center>BICUBIC x3</center></td>
        <td><center>SRCNN x3</center></td>
    </tr>
    <tr>
    	<td>
    		<center><img src="./data/6.bmp""></center>
    	</td>
    	<td>
    		<center><img src="./data/6_bicubic_x3.bmp"></center>
    	</td>
    	<td>
    		<center><img src="./data/6_srcnn_x3.bmp"></center>
    	</td>
    </tr>
</table>


​        



