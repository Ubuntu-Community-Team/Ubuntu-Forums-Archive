---
title: "[Audio] Volume keys acts for HDM while mouse for analog"
date: 2013-04-16
forum: Multimedia Software
---

### Post by e-San on 2013-04-16
Hi!

I have problem that i can not resolve.

I'm on Samsung Series 5 notebook (AMD/ATI GPU with HDMI and Realtek ALC269VC) and Xubuntu.

I made some research, and, at least (but nearly useless as i can see now) forced alsa to load my analog out as first card. I provide my setup if someone looks for this:

```
san@sammie:~$ cat /etc/modprobe.d/alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1

[...] Default config [...]

# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

[...] my adds [...]
[...] this does NOT work [...]

#Niech analogowe b&#281;dzie pierwsze
#options snd-hda-intel model=laptop-amic index=0
#A HDMI drugie:
#options snd-hda-intel model=auto index=1

#options snd-hda-intel index=1,0 

[...] this one works [...]

options snd-hda-intel id=00:14.2 index=0
options snd-hda-intel id=00:01.1 index=1
```

You can get Your ID's from:
```
san@sammie:~$ lspci -nn|egrep 'ultimedia|udio|sound|AC97|ac97|EMU'
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Device [1002:9902]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
```

To check:
```
san@sammie:~$ head -n 1 /proc/asound/card*/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269VC

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```
[CENTER][B]OK, lets go find solution for my problem
[/B][/CENTER]
So, i setup proper first and second device, but now,
when i hit volume on keyboard - it changes volume for hdmi
when i scroll on volume applet - it changes volume for analog

how to change it to analog only?

Regards!

---

