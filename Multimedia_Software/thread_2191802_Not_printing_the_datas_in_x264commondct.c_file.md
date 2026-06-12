---
title: "Not printing the datas in x264/common/dct.c file"
date: 2013-12-04
forum: Multimedia Software
---

### Post by vswathi149 on 2013-12-04
Hi ,
I installed the x264 encoder by giving the following
 
git clone git://git.videolan.org/x264.git


I enabled x264 encoder in ffmpeg.And also confiured the libraries For knowing the code flow i am debuging the code in linux by writing printfs in all files.

Its printing internally in macroblock.c file.
But in x264/common/dct.c file is not printing.
dct.c conatains sub4x4_dct() function and also other functions.Its not going internally in dct.c file funcitons.I dont no the reason.can anyone please suggest me..

---

