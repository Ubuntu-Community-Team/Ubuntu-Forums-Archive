---
title: "Sound Not Working"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Eman64 on 2007-08-26
I have just recently acquired a new computer and I have set it up, but now that I finally have the speakers in I get no sound at all.
The Sound is coming out of my motherboard, not another sound card. I have a Intel Core 2 Duo.
Somebody Please Help, I can't live without my music

---

### Post by deadgobby on 2007-08-26
Go into BIOS and disable the on board sound device. Check for the sound after it boots up. You may need to do some work to get the sound device working. To get what sound device you have if the sound is not working. Open up the terminal and  type in 

aplay --list-devices

or 

lspci -v 

Gobby

---

### Post by Eman64 on 2007-08-26
Maybe I stated this wrong. I don't have a sound card, so I am forced to used the Onboard Sound, but it won't work for me

---

### Post by Gwasanaethau on 2007-08-26
> **deadgobby said:**
> Go into BIOS and disable the on board sound device…

Just to let you know, I had a problem with intermittent sound after installing a new graphics card (ASUS nVidia GeForce 7600 GS): at boot-up there was a 50/50 chance as to whether I had sound or not. Disabling the on-board sound seems to have fixed the problem. Thanks Gobby!\\:D/

P.S. For the record, I have a PCI sound card…

---

### Post by Eman64 on 2007-08-26
These are what I get after running the commands

lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 820d
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

aplay --list-devices
```
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by deadgobby on 2007-08-26
Have you played with the ASLA mixer settings? If you have not installed ASLA mixer, you can install the  GUI version in synaptic. What  version of ubie are you running?
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by Eman64 on 2007-08-26
I am currently running Feisty and already have had alsa installed and played with.

---

### Post by deadgobby on 2007-08-27
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Eman64 on 2007-08-27
Gobby, you are a life saver! Thank you so much!

---

### Post by deadgobby on 2007-08-28
You are very welcome. I am glad it worked for you and now you have sound to enjoy your ears and mind with.
Gobby

Ugg I need to get a new keyboard.

---

### Post by firestryke on 2007-08-30
Ok, so I tried doing all of that on the link that you sent since I was in the same situation, but I've got a problem now...  When I get to the end and have to "Manually Specify Module Parameters" I get lost. I don't know what to put for a model and the cat command won't work. I don't have the directory they talk about apparently. Nor do I have an ASLA-Configuration.txt file. I did a search for the file and came up empty. All I want is my sound to work again. It worked fine when I first installed ubuntu, but then I touched the sound preferences under default mixer tracks and it hasn't worked since, even after going back to what it was before...

---

