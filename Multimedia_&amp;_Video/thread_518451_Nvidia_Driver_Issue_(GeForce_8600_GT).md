---
title: "Nvidia Driver Issue (GeForce 8600 GT)"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by Fiki on 2007-08-05
I recently put together a computer with an Nvidia GeForce 8600 GT video card. I tried to install the ubuntu nvidia-glx driver through the synaptic package manager but it failed - I later realized this is because that driver does not support the 8600 GT. Is there any way to install a driver for this video card? I tried downloading the driver from the Nvidia website but I could not get out of Xserver to install it (I tried researching how to do it but no method worked, ctrl+alt+backspace logged me out but didnt get me out of X). I am also worried that the Nvidia website driver for linux won't support the 8600 GT either. Does anyone have any suggestions? I think I'm gonna cry.

Note: I'm using the latest version of Ubuntu Feisty

---

### Post by soniclava on 2007-12-18
Any resolution on this?  I am in the same boat.

/bump!

---

### Post by talon95 on 2007-12-18
Control-Alt-F1 dumps you out to the single command line.  If it complains about X still running, you might try:

sudo /etc/init.d/gdm stop

Then run the installer.  This is a pretty good guide:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

