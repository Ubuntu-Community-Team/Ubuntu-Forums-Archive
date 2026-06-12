---
title: "im new, i havent sound"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by torohok on 2005-11-09
(sorry for my english, im chilean)
i dont know how to know if the sound card is installed, i have a laptop(dell) and before i have installed windows and the sound uses to work, but now with ubuntu dont. i have this error:


Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.

thanks

---

### Post by zonk on 2005-11-10
Hi torohok.

First of all you should take a look if the modules (driver) you need are loaded. To do this open a Terminal and write:

lsmod

then you'll get a list with the modules that are loaded. Take a look for something like:

snd_pcm_oss            57640  0
snd_mixer_oss          20288  3 snd_pcm_oss
snd_pcm                  104036  2 snd_via82xx,snd_pcm_oss
snd_timer                  26312  1 snd_pcm
snd_page_alloc         13328  2 snd_via82xx,snd_pcm

If there aren't any modules which have to do with sound, you probably need to install alsa. Open Synaptic and search for alsa and install it, if it is not installed. 
This hopefully will already do the trick.



To find out which hardware you have write in the terminal:

lspci

Then you'll see all the hardware in your Computer. Search for something simmilar to:


Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)

If it doesn't work post you soundcard chipset here or  you can look up the hardware at [www.alsa-project.org](www.alsa-project.org) if it is supported.


Good luck.


zonk  

bye the way: which laptop exactly do you have? take a look at: [www.tuxmobil.org](www.tuxmobil.org)
or [www.linux-laptop.net](www.linux-laptop.net)


[QUOTE=torohok](sorry for my english, im chilean)
i dont know how to know if the sound card is installed, i have a laptop(dell) and before i have installed windows and the sound uses to work, but now with ubuntu dont. i have this error:


Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.

thanks[/QUOTE]

---

