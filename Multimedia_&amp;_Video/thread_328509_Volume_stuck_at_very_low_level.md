---
title: "Volume stuck at very low level"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by broughcut on 2006-12-31
I have the Intel AC 97 ICH4 soundcard in a Panasonic Toughbook Cf-29 using the intel8x0 driver.

Sound is just barely audible from headphone jack and it responds to volume controls/mute. Nothing from speakers (too low to register perhaps).

I have tried  all the obvious, alsamixer etc (everything is max, including pcm), tried most the  solutions in the various AC97 threads to no avail... understandable as my soundcard is  recognised,.

When I was dual booting Windows and using Ubuntu, I noticed I was always stuck with the volume set by the keyboard hotkeys in the previous Windows session. If I had muted it in windows I would need to unmute from Windows and reboot in order to get sound in Ubuntu. Although I have now got the hotkeys working (including LCD brightness), I have a feeling the volume buttons are now acting as software shortcuts but previously adjusted the hardware directly--in which case I'm stuck with the min volume setting from my old windows installation when the hotkeys were working off the official Panasonic drivers. Is that possible?  

I never got the hotkeys working in Linux when I was dual booting windows so I don't know if their behaviour is different using the Linux drivers. Installing the official Panny drivers on XP in VMware fails as they do not recognise the machine as a CF-29.

Any ideas? If I'm stuck at this volume level, is there any software to boost the volume without distortion above 100%?

---

### Post by broughcut on 2007-01-04
no sound at all in VectorLinux. Soundcard is recognised though.

There must be a way of resetting the hardware???

---

### Post by jake3988 on 2007-01-05
You sure EVERYTHING is turned up?  That was my initial problem was that the bar for 'center' was too low.

---

### Post by broughcut on 2007-01-05
yup, everything is maxed out.

I could really do with some sound....  Crazy that Panasonic don't have linux drivers.

---

### Post by Wartooth on 2007-02-17
I'm apparently going through the same thing.  [http://www.ubuntuforums.org/showthread.php?p=2171033#post2171033](http://www.ubuntuforums.org/showthread.php?p=2171033#post2171033)

I've only heard sound a few times, with EVERYTHING cranked up, and it's a tiny whisper of sound, only enough to let you know that some sort of sound is being made, but not much else. :(

I'm going through more threads and trying everything I can.  :/

---

### Post by idlewild on 2007-02-25
My panasonic pc has an acpi based mute built in that linux can't control. It's possible your experiencing this. To disable it you have to boot into windows and unmute everything then return to linux.

---

