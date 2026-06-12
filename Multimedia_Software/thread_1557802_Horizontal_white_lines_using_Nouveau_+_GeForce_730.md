---
title: "Horizontal white lines using Nouveau + GeForce 7300 GS"
date: 2010-08-21
forum: Multimedia Software
---

### Post by garethbatten on 2010-08-21
Hi,

I've just done a clean install of 10.04.01 (64bit) and am having a few issues with the Nouveau driver.

1. I'm getting a series of horizontal lines across the screen ([ image]("http://www.flickr.com/photos/26678753@N05/4913011404/")). [IMG]http://www.flickr.com/photos/26678753@N05/4913011404/[/IMG]

2. I'm getting, what appear to be, GPU lockups.  This appears to happen after an amount of browsing and rendering images.

My system setup is:
10.04.01 LTS

grep 'Monitor name' /var/log/Xorg.0.log
(II) NOUVEAU(0): Monitor name: EA231WMi

VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

Grateful is anyone has any pointers of where to go from here, I've never had any issues with Ubuntu before.

---

### Post by jmfal on 2010-08-21
Have tried to install the nvidia drivers.

system> administration> hardware drivers

will search for drivers and give you a couple of choices

I did a quick
 look in synaptic and it shows a nvidia-96 for the gt7300

check in synaptic before you try to install (use quick search type in nv then scroll down to find).
if it`s not in synaptic go to software sources and check the box for proprietary drivers then close select reload then try to install the driver

---

### Post by garethbatten on 2010-08-21
Hi,
I tried nvidia-current and nvidia-96; current boots the login screen but all of the text is replaced by thick black bars and 96 hangs at the Ubuntu loading page (with the dots) so I had to 'aptitude remove' from the safe boot, which takes me back to using Nouveau.

---

