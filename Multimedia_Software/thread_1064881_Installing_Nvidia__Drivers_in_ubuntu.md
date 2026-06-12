---
title: "Installing Nvidia  Drivers in ubuntu"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Sojurner on 2009-02-09
I am trying to install the downloaded drivers from the nvidia website. The file name is NVIDIA-Linux-x86-180.22-pkg1.run.

I cant for the life of me figure out how to install it and i need some help. I have searched all over the internet and cant find any solution that works. Any help would be greatly appreciated.

My goal is to have my multiple monitors working with Ubuntu. My graphics card is an 8800 GTS 640MB

---

### Post by overdrank on 2009-02-09
> **Sojurner said:**
> I am trying to install the downloaded drivers from the nvidia website. The file name is NVIDIA-Linux-x86-180.22-pkg1.run.

I cant for the life of me figure out how to install it and i need some help. I have searched all over the internet and cant find any solution that works. Any help would be greatly appreciated.

My goal is to have my multiple monitors working with Ubuntu. My graphics card is an 8800 GTS 640MB

Hi and welcome, if you would like to try and install the nvidia driver you have downloaded then you can use the keys alt, ctrl, F1 keys at the same time and this will bring you to the command prompt and login.
The use this command to stop X
```
sudo /etc/init.d/gdm stop
```
Then change to the directory that you downloaded the driver to
```
cd ~/Desktop
```
Then you can use the command to install the nvidia drivers 
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```
If that is the name of the driver you have downloaded.
Then you should be able to start x again 
```
sudo /etc/init.d/gdm start
```
If all works as plan then you should have the new driver installed.

---

