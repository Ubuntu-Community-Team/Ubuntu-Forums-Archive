---
title: "No iec958 in Alsamixer"
date: 2008-07-13
forum: Mythbuntu
---

### Post by larsolav on 2008-07-13
Hi,
I just got a new audio receiver with an optical sound input, and I am now trying to configure SPDIF for the first time. I am not coming very far...

I am following the Configuring Digital Sound wiki, at [http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound) .
```
aplay -L

```
Results in:
> front:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

So iec958 is there somewhere.
But neither in alsamixer or xfce4-mixer is there a iec958 to unmute. In xfce4-mixer I don't see it in file>options either.

The audio is on a Foxconn 955x7aa motherboard.
I am running 7.10. 

I have Google searched and searched this forum, but I can't find out how to get the digital sound to work. I see no light in the cable either...

I'd be very happy if someone would know what to do.

Thanks!

---

### Post by nickrout on 2008-07-13
what does

```
aplay -l
```

tell you? (note the lower case -l)

---

### Post by larsolav on 2008-07-13
nickrout, thanks for the reply!
```
aplay -l
```
Gives:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Is this what it is supposed to be?

---

### Post by nickrout on 2008-07-13
mine give

```
nick@media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

You can see it recognises two devices on the card, one of which is the IEC958 stuff.

Maybe you are using the wrong driver, or the driver doesn't fully support that card yet?

---

### Post by larsolav on 2008-07-13
Ah, bummer...

I did some more searching, and found this wiki about what I think is my sound chip: [http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x)

I did a "find" command for modprobe.conf, but could not find any. Where do I put this file? In /etc? And where does the asound.conf  go?

Also, how do I download this snd-hda-intel driver they talk about. I am very new to linux so I have never manually installed a driver before...

Thanks!

---

### Post by nickrout on 2008-07-13
I believe both files go in /etc

---

### Post by Randall311 on 2009-03-04
> **larsolav said:**
> Ah, bummer...

I did some more searching, and found this wiki about what I think is my sound chip: [http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x)

I did a "find" command for modprobe.conf, but could not find any. Where do I put this file? In /etc? And where does the asound.conf  go?

Also, how do I download this snd-hda-intel driver they talk about. I am very new to linux so I have never manually installed a driver before...

Thanks!

in your /etc/modprobe.d/alsa-base try adding:


```
options snd-hda-intel model=6stack-digout
```

If the model 6stack-digout doesn't work, there are several others to try for the Realtek ALC880 chipset:

```

ALC880
------
3stack        3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack        5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack        6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810          3-jack
z71v          3-jack (HP shared SPDIF)
asus          3-jack (ASUS Mobo)
asus-w1v      ASUS W1V
asus-dig      ASUS with SPDIF out
asus-dig2     ASUS with SPDIF out (using GPIO2)
```

Good luck!

---

