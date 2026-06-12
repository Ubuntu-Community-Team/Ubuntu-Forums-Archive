---
title: "No Audio Devices showing in Sound Options"
date: 2013-12-30
forum: Multimedia Software
---

### Post by brandonmcase on 2013-12-30
Please Help, I booted to my ubuntu 13.11.14 today after 9 days of vacation and i have to audio input or output. all that shows up on my sound settings is "Dummy Output" I tried running 

```
sudo alsa force-reload
```

and got 

```
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

then 

```
[COLOR=#444444][FONT=Arial]sudo apt-get remove --purge alsa-base pulseaudio
[/FONT][/COLOR][COLOR=#444444][FONT=Arial]sudo apt-get install alsa-base pulseaudio
[/FONT][/COLOR]sudo alsa force-reload
sudo reboot
```

i also tried 

```
[COLOR=#444444][FONT=Arial]sudo add-apt-repository ppa:ubuntu-audio-dev
 sudo apt-get update 
sudo apt-get dist-upgrade[/FONT][/COLOR]
```


but no dice, I ran a hardware list and outputed it to html and uploaded it to my server  here's the link.

[http://brandoncasemedia.com/hardwarelist.html](http://brandoncasemedia.com/hardwarelist.html)

please help.

---

### Post by Yellow Pasque on 2013-12-30
What happens when you tryo to manually load a sound module?
```
sudo modprobe -v snd-hda-intel
```

I've seen a few reports of problems with the 3.8.0-34 kernel, so try a different one if that's what you're using. What version of Ubuntu are you using, 13.04 or 13.10? ("13.11.14" is not a valid Ubuntu version...)

---

### Post by brandonmcase on 2013-12-30
> **Temüjin said:**
> What happens when you tryo to manually load a sound module?
```
sudo modprobe -v snd-hda-intel
```

```
libkmod: ERROR ../libkmod/libkmod.c:554 kmod_search_moddep: could not open moddep file '/lib/modules/3.11.0-14-generic/modules.dep.bin'
```

> **Temüjin said:**
> What version of Ubuntu are you using, 13.04 or 13.10? ("13.11.14" is not a valid Ubuntu version...)

13.10

---

### Post by Yellow Pasque on 2013-12-30
Try reinstalling kernel image:
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo depmod -a
```

Reboot.

---

### Post by brandonmcase on 2013-12-30
That fixed it, thank you so much, you rock my world.

---

