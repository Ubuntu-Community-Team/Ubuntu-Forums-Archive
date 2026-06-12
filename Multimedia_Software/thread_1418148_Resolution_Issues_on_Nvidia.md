---
title: "Resolution Issues on Nvidia"
date: 2010-02-28
forum: Multimedia Software
---

### Post by nexoncore on 2010-02-28
I have just bought a brand new acer monitor with a maximum resolution of  1900 x 1080 ( something like that ) but ubuntu is only allowing a max  of 1300 x 700 ( approx ).

My graphics card is an onboard nvidia geforce 7100 / nForce 630i and is  capable of the monitors max resolution.

I have tried using both the Gnome Display Configuration and the Nvidia  Settings, but I cant get the desired higher resolution.

---

### Post by nexoncore on 2010-02-28
Can someone help please

---

### Post by Henery on 2010-02-28
I am a newbie but do you have the drivers installed if so what version I have never run into this trouble before!
Are you detecting the proper display? You could download the latest driver from nvidia and install them but that is a pain in itself lol! My guess is you have a configuration problem or the monitor does not display 1080p!

---

### Post by Henery on 2010-02-28
Ps in the nvidia gui you can create custom resolutions But if it does not show the res I would not recommend it! There is also a detect display button try that maybe it is remembering the setting from your last monitor!

---

### Post by nexoncore on 2010-03-23
I am using the latest driver from nvidia as the ubuntu ones just wont do the job. 

1) Although the monitor is detected, its noted down as unknown ( its a brand new acer monitor, the model has only just been replaced. The max resolution of the monitor is 1920 x something widescreen.

2) I have tried manually setting the resolution but it wont work.

To be safe I decided to try on windows vista, again I had to set the resolution manually, but it was rather easy and worked. So I am now in an issue of which OS to use, windows is winning just because of the resolution capabilities, apart from that I wouldnt even have windows installed.

---

### Post by my_wan on 2010-03-23
You should be able to use nvidia-settings to change and save settings to   xorg.conf.

Try typing
```
sudo /usr/bin/nvidia-settings
```into a console (also under System>Administration>NVIDIA X Server Settings) and setting it there. Under "X Server Display Configuration" change your resolution to what you want, then hit "Save to X Configuration File".

It'll may fail. If so type:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```to back up just in case. Then try:
```
sudo /usr/bin/nvidia-settings
```and retry the nvidia-settings above.

If you need the old config back type:
```
sudo mv /etc/X11/xorg.conf_old /etc/X11/xorg.conf
```and your back where you started.

---

