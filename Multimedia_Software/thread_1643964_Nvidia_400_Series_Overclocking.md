---
title: "Nvidia 400 Series Overclocking"
date: 2010-12-12
forum: Multimedia Software
---

### Post by Parkournerd on 2010-12-12
Does anyone know how to do this? 
This is my xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "Coolbits" "1"
EndSection

This did not activate CoolBits. 

Also, can anyone show me how to update my Nvidia driver as well? I'm new to Linux and I don't know how to do it.

---

### Post by Parkournerd on 2010-12-12
.

---

### Post by overdrank on 2010-12-12
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Parkournerd on 2010-12-12
I didn't know how to delete the thread.

---

### Post by efflandt on 2010-12-13
I tried setting Coolbits for my GT 430 too and it does not seem to do anything.  I almost thought that I figured out how when I found ~/.nvclock/ that I had not noticed before containing a config file:

```
#This is NVClock's config file. Don't edit the hw and general section!
general.cards=1
hw0.basefreq=13500
hw0.card=2592
```13500 appears to correspond with my minimum memory clock speed 135 MHz.  But **sudo gdm stop**, editing that to 15000, then **sudo gdm start** had no affect on indicated PowerMiser speeds or glxgears (Sync to Vblank disabled).

I did not realize that Maverick was still running nvidia 260.19.06 drivers.  If you want newer (currently 260.19.26) you have to add x-swat repository [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then you can update nvidia-current, nvidia-settings, and nvidia-current-modaliases using Synaptic and reboot.  Coolbits still may not work.

---

