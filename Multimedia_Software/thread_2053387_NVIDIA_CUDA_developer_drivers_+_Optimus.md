---
title: "NVIDIA CUDA developer drivers + Optimus?"
date: 2012-09-05
forum: Multimedia Software
---

### Post by funcrusher on 2012-09-05
OK, I have a pretty specific Optimus/CUDA/drivers question:
  
[LIST]
[*]I'm running Ubuntu 12.04 on an Acer Aspire 5750G. This laptop has  a CUDA-capable GT540M GPU, but it also has Optimus, so in order to make  use of it I need to use bumblebee
[*]Following [these instructions]("https://wiki.ubuntu.com/Bumblebee#Installation") I installed more recent NVIDIA drivers from ppa:ubuntu-x-swat/x-updates, then installed bumblebee
[*]I can now run stuff on the GPU just fine (optirun glxspheres works as expected)
[*]However, I'm trying to compile something (OpenCV-2.4.2) with CUDA  runtime support, and I hit a compiler error that seems to be to do with  not having the NVIDIA CUDA developer drivers installed
[/LIST]
  What I want to know is whether it's possible to use bumblebee in  combination with the NVIDIA developer drivers. Is it safe to use the  installer downloaded from NVIDIA's developer page, or will that totally  mess up my currently working setup with bumblebee? Is there a better way to install the developer  drivers? I looked for an up-to-date PPA but couldn't find one.

---

### Post by BicyclerBoy on 2012-09-05
AFAIK if you install nVidia X server driver outside of Bumblebee you break it.

This looks like a soln:

[http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car](http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car)

& read the linked-to thread
[http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936)

---

### Post by funcrusher on 2012-09-06
Ok, so it turns out that I don't need to use the developer drivers to compile OpenCV after all!

I had somehow messed up my software sources such that I wasn't updating from ppa:ubuntu-x-swat/x-updates any more. When I fixed that I was able to update my NVIDIA drivers to 304.43  from 295.49. I think that might have been the critical factor for getting OpenCV to compile, although I did also have to modify one makefile to make it work.

If anyone's interested in doing the same, I basically followed the instructions [here]("http://jayrambhia.wordpress.com/2012/06/20/install-opencv-2-4-in-ubuntu-12-04-precise-pangolin/"), but I also modified CMakeCache.txt as described [here]("http://answers.opencv.org/question/579/gpu-opencv-242-with-cuda-support-ubuntu-1204/").

---

### Post by BicyclerBoy on 2012-09-07
Sorry
I thought you were trying to compile your own cuda code with the nVidia toolchain stuff.

---

