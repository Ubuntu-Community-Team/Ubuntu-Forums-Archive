---
title: "Switching drivers ATI --&gt; Nvidia"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by Dubbayoo on 2007-08-11
Right now I am using the free ATI driver "ati" with my Radeon 8500. I just got a 	Geforce FX 5500 that I'm about to install. How should I proceed? Should I switch to the free nvidia driver in xorg.conf then install the card or install the binary Nvidia driver first?

---

### Post by RomeReactor on 2007-08-11
Hi. You should install the **nv** driver first:
```
sudo apt-get install xserver-xorg-video-nv
```
then shutdown, insert the nVidia card, boot up (which will likely take you to the command line) and run:
```
sudo dpkg-reconfigure xserver-xorg
```
when it asks you which driver to use, choose **nv**.

---

