---
title: "Movie Player, PitVi apps disappear when load clip and enlarge window"
date: 2011-06-18
forum: Multimedia Software
---

### Post by rreyes3713 on 2011-06-18
I just installed 10.04 Ubuntu and allow the Manager Updates.

Movie Player and PitVi apps seems to disappear when I load a clip and enlarge the window. 

Movie Player will allow a smaller window and the clip to be played but once I stretch the window, it disappear Nope, its not as though I "floored" that window. It's gone.completely.

PiitVi, when loading a clip, once its full loaded, it disappears.

I did try installing and re-installing but same results.

Anyone experience this phenomena? 

Other applications seems fine.

Help!

---

### Post by rreyes3713 on 2011-06-21
I'm pretty sure Its a video driver issue. I un-installed the "recommende"d Nvidia driver on the hardware list and now these video apps are able to run full screen ....

... but the graphics are low resolution.

... I went to the Nvidia dowload driver website and download the proper driver. (Its GeForce FX Go5200 graphic card). 

I tried to do a run the download file but but I get an xTerm error or something or rather. The Readne file on executing this download file is with the other Linux system not Ubuntu. 

... I check the other posts on installing Nvadia driver on Ubuntu system. 

I'm getting close.

Just a bump.

---

### Post by rreyes3713 on 2011-06-22
Yes, it was a video card driver problem

So I used this method.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It works but curious if this is the proper driver so II went to the Nvidia website and download the driver for my card:

NVIDIA-Linux-x86-173.14.30-pkg1.run

and I did the following to run this file

sudo sh NVIDIA-Linux-x86-173.14.30-pkg1.run

It gave me an error. Got to read up on how to run this file.

---

