---
title: "ALC861VD: screen microphone or headphones, but not both"
date: 2009-04-18
forum: Multimedia Software
---

### Post by lazyfirecloud on 2009-04-18
Hi:
I have a HP TX1499 and I cannot get both the microphone and the headphones to work properly. I'm running Intrepid Ibex 8.10 and I have the latest ALSA on aptitude (v1.0.17). Actually, my system is fully updated.
Here is my hardware info:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
```


I have tried setting the ALL following models (and more) as for options snd-hda-intel model=<MODEL> in /etc/modprobe.d/alsa-base
```

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

```
I've noticed 2 cases:
1) model=hp: front mic (the one with the jack) seems to work (playing music from an pm3 player), and headphones work, but I cannot use the ATAPI microphone (the microphone in the screen). There is no microphone boost and I cannot hear anything even with all volumes put to max (no feedback even when I yell into the microphone). It seems the capture and digital keep getting that little red x on the mic no matter how many times I remove it.  But I don't think it should be a big deal, as I said I hear it fine from my front mic. I think it's just not loud enough to work with the ATAPI one. There is no boost option for either microphones. All volumes are set to max (everything checked in preferences). Changing input source between front and ATAPI doesn't make a difference. 
2) model=3-stack-digout: there is a mic boost option for both mic (jack??) and front mic (this time, that's the one on my screen).  If I set all the boost to 100% I can get the screen mic to work properly. But then nothing happens when I plug in my headphones (no sound in the headphones, still playing on speakers). Also in those cases, it seems that the regular jack mic doesn't work properly, I can hear some noise when plugging it in but no real music.

I've thoroughly played with hp and 3-stack-digout, and have just tested the screen mic and headphones on the others (and didn't find any cases where both were working).
case 1: hp, hp-laptop, 3-stack-dig, 6-stack-dig, and I think lenovo and dallas (can't quite remember), auto, basic
case 2: 3stack, 3stack-digout, 6stack, 6stack-digout 
others I've tested but can't recall which of the 2 cases it fell in:
will, w810, z71v, hp-3103, toshiba, asus, and probably a few more.

The way I've been trying them has been to change the file then run the following:
```

sudo killall pulseaudio
sudo alsa force-reload
pulseaudio -D

```

Then I can go into the gnome sound mixer and play around with settings. They do change when I change the model, so I assume it successfully changes the settings.

Anyone has any clue? It would be nice to have both the headset and the microphone working for skype (PS: with the mic boost, skype sounds great, but yeah no headsets means everyone's got to listen to the whole conversation).

thanks in advance

---

### Post by markbuntu on 2009-04-19
These are all the options I found for HP laptops. You could also try upgrading alsa, they are up to 1.0.19 

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)


HP model=hp
tx1000
tx2000z
3013 model=hp-3013
nx6325 model=toshiba
6535b model=laptop
6735s
TX2635us (tx2500 series) model=toshiba position_fix=1
xw4400/6400 model=hp-bpc
8400/9400
BPC D7000 model=hp-d7000
Thin Client T5735 model=hp-tc-t5735
dv4-1120us enable_msi=1
dv4-1124nr
dv4-1124cl
dv4-1150
dv4-1000ea
dv7
dv5 model=dv5
dv4z

---

### Post by lazyfirecloud on 2009-04-20
Thanks for looking up the extra models.

I'm trying not to upgrade ALSA since it seems this may give me trouble later when new versions are released in the official ubuntu packages, and I've had enough trouble already =). In fact, I probably won't upgrade to Jaunty for a while (nvidia drivers, touch screen, etc...)

I'll try some of the other models and let you know. Technically, mine should be "hp" (tx1000) but that doesn't quite work fully. Is there anyway to force a boost of 100% even if there is no boost on the mixer? If so, then it would be the perfect solution =)

---

### Post by lazyfirecloud on 2009-04-20
Well this is really odd, but I still can't hear myself when I set all volumes including ATAPI mic playback to max, and I can't here anything back on the test call on skype, but a real person said they heard me just fine. So I guess my issue is solved =). I'm still a little perplexed I can't record anything, or hear playback, but what the heck, the only reason I would use my mic is skype so I'm considering myself happy =)

---

