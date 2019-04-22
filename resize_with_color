import h5py
import numpy as np
import matplotlib.pyplot as plt
from PIL import Image
from scipy import misc


def get_result_array():
    file_name = "./butterfly_GT.bmp"
    img_no_expand = misc.imread(file_name, flatten=False, mode='YCbCr')
    img_no_expand = img_no_expand / 255.0
    # img_no_expand = np.uint8(img_no_expand*255)
    h, w = img_no_expand.shape[:2]
    print(img_no_expand.shape)
    h *= 2
    w *= 2
    data = list()
    data.append(misc.imresize(img_no_expand[:, :, 0], [h, w], 'bicubic', mode="F")[:,:,None])
    data.append(misc.imresize(img_no_expand[:, :, 1], [h, w], 'bicubic', mode="F")[:,:,None])
    data.append(misc.imresize(img_no_expand[:, :, 2], [h, w], 'bicubic', mode="F")[:,:,None])
    data_out = np.concatenate(data, axis=2)
    data_out[data_out > 1] = 1.0
    data_out = np.uint8(data_out * 255)
    img = misc.toimage(arr=data_out, mode="YCbCr")
    img.save("out_4.jpg")


if __name__=='__main__':
    get_result_array()
