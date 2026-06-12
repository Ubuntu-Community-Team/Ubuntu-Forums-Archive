---
title: "video driver issue (asus a6jc, nv go 7300)"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by xianthax on 2006-08-28
i've just installed ubuntu 6.0 (latest) on my laptop, an asus a6jc (core duo, nvidia go 7300)  everything seems fine except the video.  the driver that was installed is the legacy nvidia driver i think (nv is the designation given in the conf file, not 'nvidia') as such the nvidia-glx package does not work.  i had to manually add the resolution of my screen to the x conf file, whcih seems to work now (the desktop is running at my screen native res), however i think its in 16bit color mode not 24, even tho 24 is listed in the conf file as there is pretty obvious banding in smooth color changes.   how do i check if the proper driver driver is installed?   i need opengl support as well for cedega(not yet installed, want to sort the driver first), is there a way to check for this?

there may be an issue with the design of the laptop itself as the drivers from nvidia don't work under windows either, the chipset is not recignized. i have to use the ones from asus.

anyone have any expirience with this laptop or this chipset?  any help would be great

-xian

---

### Post by xianthax on 2006-08-29
if it helps:

lspci -v | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d7 (rev a1) (prog-if 00 [VGA])



-xian

---

### Post by xianthax on 2006-08-30
just to update this thread incase others have the isssue.

changing the entry in X11.conf from 'nv' to 'nvidia' allowed the nvidia-glx driver package to work.  the system now operates in 24bit color and acceloration seems to be correct as well as moving windows is much smoother, there are, however a few bugs, the most notable is that the driver seems to have trouble shutting down.  for instance when shutting down the system the ubuntu shutdown screen does not appear, the screen simply goes blank.  the shutdown occurs correctly, just with no video.

purhaps this can be added to the list of issue with the go 7300 chipset or with this laptop inparticular.

-xian:mrgreen:

---

### Post by Clanman on 2006-08-30
I have the same problem. i have a 7900 GT card
Im running the glx driver and
cat /var/log/Xorg.0.log
Gives indication of that the server runns 24 bit. but the images that are produced are crap. 

It looks just like when I change it to run in 16 bit depth.

And i think you mean the /etc/X11/xorg.conf file

---

