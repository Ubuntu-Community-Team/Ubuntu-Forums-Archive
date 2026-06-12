---
title: "[SOLVED] which driver is best for legacy NVIDIA?"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by streamsanddragonflies on 2007-12-25
Hello!


Before I pass out - I mean sleep, I wanted to figure out the best approach for supporting my Quadro 4 pro 900 XGL AGP video card.  I had the general NVIDIA driver automatically installed when I installed Ubuntu but I had to switch to a restricted driver in the packages to enable accelerated 3D effects.  When I rebooted I found that I couldn't access any advanced visual settings from Cmpiz fusion.  I thought that I did download the compiz settings via synaptic but maybe it's not installed properly.  What is the sudo command for verifying an installation?  is it sudo apt get or sudo -i then install? I'm still confused with the command line.
  
AIso, NVIDIA has a recent driver for my video card.  Is this one better?
Version: 96.43.01   
Linux Display Driver - x86
Operating System: Linux x86
Release Date: September 18, 2007 

Release Highlights 
Improved compatibility with recent versions of X.Org X servers.
Fixed a TV-OUT corruption problem on some GeForce 4 GPUs.
Fixed a bug that resulted in the generation of incorrect EDIDs on some notebooks.
Improved power management support with some GeForce 4 based notebooks.
Improved compatibility with recent Linux 2.6 kernels.
Fixed an 'nvidia-installer' bug that was causing the installer to treat some of its temporary files as conflicting.

I am wondering if it is the same one as what was in the synaptic packages, but I'm sure the version sounded diffrent.
I also want to try some video editing so a good driver is important.:)

---

### Post by eggdeng on 2007-12-25
There is a list of nvidia cards supported by different drivers at
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")
which recommends the legacy 1.0-96xx  driver for your card. There are installation instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

