---
title: "video playback jerky with nvidia 8200"
date: 2009-11-24
forum: Multimedia Software
---

### Post by twidget on 2009-11-24
hi,
I'm trying to play an avi file but i keep getting lines and jerkyness when there is a great deal of motion on screen.the screen is currently set to 1280x720 but 1024x 768 didn't  help either. specs on computer: Asus M3N78-VM motherboard with geforce 8200 chipset, Athlon 2 620 quad core, 4gb ddr2 1100. the file I'm using to test with played fine on a much lower speced pc using an older version of Kubuntu. I'm assuming its some sort of configuration error or bug but I have no idea how to track it down at this point. any help in figuring this out would be appreciated.

---

### Post by twidget on 2009-12-05
actually it looks like it might be a codec problem. video playback had problems under windows 7 also but after i Installed different codecs everything worked fine. so at least the hardware appears to check out. does anyone know if there's a way to update/get new codecs for mplayer?

---

### Post by xc3RnbFO8P on 2009-12-05
Just try to reinstall codecs again:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Uncle Spellbinder on 2009-12-06
I had the same issue of jerky playback/lines. Do you have desktop effects enabled? Seems to be an issue with Compiz and video playback.

What I did was install the 190 nVidia driver using this PPA repo:

```
#### Nvidia Vdpau Team PPA
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
``` 

[[IMG]http://content.imagesocket.com/thumbs/video_nvidia18d5.png[/IMG]](http://imagesocket.com/view/video_nvidia18d5.png) 

Once the 190 driver was installed, rebooted and did the following...

* Open nVidia settings: under "Xserver Xvideo Settings", make sure "Sync to VBlank" is checked. Do the same for "OpenGL Settings".

* Open CompizConfig Settings Manager: Under *General > General Options > Display Settings*, make sure to check "Sync To VBlank"

* Reboot.

Worked wonders for me. All video (avi/divx/mkv as well as online flash)  has been free of jerky playback/lines/flicker.

---

### Post by twidget on 2009-12-08
I can't seem to find the CompizConfig Settings Manager but turning off desktop effects doesn't seem to help. does it have to be the 190 driver? I'm not having much luck getting the code to run. also how do I kill the codecs that mplayer automatically installs? I assume they are different from w64codecs since iirc that's what I had installed on my old machine.

---

