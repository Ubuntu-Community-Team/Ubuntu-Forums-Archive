---
title: "Problem with saving NVIDIA settings."
date: 2009-11-14
forum: Multimedia Software
---

### Post by mdatye on 2009-11-14
I have a Nvidia GeForce 6200 and I promptly shifted to Karmic Kola on the day of release!! 

Problem:
When I do x server settings as required by my monitor/what suits me and try to save, the nvidia-settings application simply crashes. 

I was not able to find anything useful in /etc/X11/xorg.conf it just looks like this: 
<snip> 
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
EndSection

</snip> 


How do i make my settings permanent? Any clues ? Ideas ? where is the x config stored now ? 

~Moh

---

### Post by norwoods on 2009-11-14
ordinarilly you can change xserver setting with nvidia-settings if you run it in root mode.
open a terminal and type 
gksu nvidia-settings<ENTER> and, if asked, your password<ENTER>

---

### Post by HappyFeet on 2009-11-14
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

