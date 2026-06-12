---
title: "HDMI no sound"
date: 2011-07-04
forum: Multimedia Software
---

### Post by Pierrick584 on 2011-07-04
I'm trying since a few days to make my sound with HDMI to work, in the sound preference, when i switch to the hdmi, there is no sound at all, i found a "kind of" fix, to edit the driver used in the alsa.conf file, problem is, not only i gotta reboot everytime i change it (or is there an easier and quicker way to reload the configs?) but anyway, it desactivate my other card completely, witch i do need for my microphone.

i also tried to change the driver output in smplayer, and it does work that way too, yet, i want the whole OS sound on my tv, not only music (well, actualy, some wine app + skype would make me happy to start with)

If anyone got suggestion, i'd be glad to hear them : \

---

### Post by JohnnyC35 on 2011-07-04
I found creating .asoundrc in your /home and putting

```

pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:0,3"
}
}

```

fixed the hdmi sound issue for me. maybe it will work for you too? I found the solution on the xbmc forums many moons ago.

---

### Post by Pierrick584 on 2011-07-04
I tried your fix as it is, and it did not work, i then tried to modify it, figuring it would containt your own driver info, dint work either... but maybe i dint did it right, here's what i gotta change in my alsa.conf so the HDMI work...

```
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
```

i change it to....

```
defaults.ctl.card Nvidia
defaults.pcm.card Nvidia
defaults.pcm.device 1.7
```



and here's the modification of your fix

```
pcm.!default {
type Nvidia
playback.pcm {
type plug
slave.pcm "hw:1.7"
}
}
```


Oh by the way... i were not sure if i had to put it in /home   or /home/user   so i placed it in both...

---

### Post by Pierrick584 on 2011-07-05
Bump . . .

---

### Post by Pierrick584 on 2011-07-06
Still got same problem...

---

### Post by Pierrick584 on 2011-07-08
Yet another BUMP.

---

### Post by BicyclerBoy on 2011-07-08
Some info will be helpful..

I assuming you have a nVidia PCIe graphics with HDMI..and you have an onboard mobo soundcard device 0.

Ubuntu x.xx ?
What video driver are you running ?
alsa version ?
aplay -l
any modprobe probe_mask values in /modprobe.d/*.conf ?


If you want to use pulse-audio (a good idea) you likely need something like:

(re: The nvidia HDMI doc..13.9.1. Adding Extra Outputs To PulseAudio)
/etc/pulse/default.pa
Only add one..& you need this one.
load-module module-alsa-sink device=hw:1,7

This will allow system wide pulse audio to use the hdmi output BUT you need to undo **all** the changes you have previously made.

---

