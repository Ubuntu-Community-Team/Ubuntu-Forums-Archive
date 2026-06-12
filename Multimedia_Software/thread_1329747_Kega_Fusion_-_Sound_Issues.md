---
title: "Kega Fusion - Sound Issues?"
date: 2009-11-17
forum: Multimedia Software
---

### Post by klikevil on 2009-11-17
Okay so this is kind of weird I'm trying to play this rom on kega fusion and everytime i start kega it says sound disabled, I have sound working on everything else (e.g. can play MP3s etc) and on another emulator i can get sound but it's choppy and I don't think it's just the rom because kega fusion i can't uncheck the 'sound disabled' and upon doing some research i saw that what that means is it can't find my sound card.  Here is my lspci for my sound card and the sound section in fusion.ini

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

``````
;---------------------------------
; Sound Options
;---------------------------------

ALSADeviceName=plughw
OSSDeviceName=/dev/dsp
UsingALSA=1
libmpg123path=/usr/local/lib/libmpg123.so
CurrentWaveFormat=2
SoundOverdrive=1
SoundSuperHQ=0
SoundDisabled=1
SoundFilter=1

```any suggestions? on how to remedy this?

changing sounddisabled=0 doesn't do anything

---

### Post by multitrackdriftu on 2009-11-21
I was having the same issue (have the same sound card), but deleting the Fusion.ini in ~/.Kega Fusion did it for me.

Now it just runs lethargically slow (everything's optimized to run fast, but it still chugs at ~30fps).

It's a shame, because Gens/GS just straight up stopped working for me (it would speed up, take up all of my CPU and crash) so I figured I'd go for the more accurate emulator anyways, but no luck...

Edit: Heh, a couple more restarts and it doesn't detect the sound card again....

---

### Post by klikevil on 2009-12-02
AHA I AM INVINCIBLE

```
sudo apt-get install oss
```reboot

make your sound options reflect this in ~/.Kega\ Fusion/Fusion.ini.

```
;---------------------------------
; Sound Options
;---------------------------------

ALSADeviceName=plughw
OSSDeviceName=/dev/dsp
UsingALSA=0
libmpg123path=/usr/local/lib/libmpg123.so
CurrentWaveFormat=2
SoundOverdrive=0
SoundSuperHQ=1
SoundDisabled=0
SoundFilter=0
```

---

### Post by multitrackdriftu on 2009-12-02
I can't find OSS anywhere in synaptic? And apt-get doesn't work either. The closest thing I found was an ALSA wrapper for OSS, which clearly isn't compatible with Fusion.

Eh, I'm reverting back to Jaunty anyways, since I'm giving Crunchbang a shot.

---

### Post by klikevil on 2009-12-03
[http://www.4front-tech.com/oss.html](http://www.4front-tech.com/oss.html)

---

### Post by multitrackdriftu on 2009-12-04
Fusion works perfectly now, sound and all. Thanks!

Just uhh, I need to get sound back to the rest of my system...

---

### Post by klikevil on 2009-12-04
> **multitrackdriftu said:**
> Fusion works perfectly now, sound and all. Thanks!

Just uhh, I need to get sound back to the rest of my system...

system > prefrences > sound

change the first three to oss4

and the bottom one to oss4 for device.  Time to play some F*ckin shinin force peace out :):popcorn:

---

### Post by multitrackdriftu on 2009-12-04
I don't have anything for the first three tabs except for output, where my only output is dummy stereo and it doesn't let me disable it?

Of course I can't help but wonder why OSS wasn't just included with Karmic to begin with...

---

### Post by klikevil on 2009-12-07
> **multitrackdriftu said:**
> I don't have anything for the first three tabs except for output, where my only output is dummy stereo and it doesn't let me disable it?

Of course I can't help but wonder why OSS wasn't just included with Karmic to begin with...


Hmmm I'd like to see a screenshot this is how mine looks i'm on Jaunty Jackalope (ubuntu 9.04 [IMG]http://i45.tinypic.com/w6zdk7.png[/IMG]

---

### Post by MSoles on 2010-10-09
> **klikevil said:**
> 
[/code]```
;---------------------------------
; Sound Options
;---------------------------------

ALSADeviceName=plughw
OSSDeviceName=/dev/dsp
UsingALSA=1
libmpg123path=/usr/local/lib/libmpg123.so
CurrentWaveFormat=2
SoundOverdrive=1
SoundSuperHQ=0
SoundDisabled=1
SoundFilter=1

```any suggestions? on how to remedy this?

changing sounddisabled=0 doesn't do anything

Try changing the name on ALSADeviceName= from plughw to default, that's what I did and I've finally got sound running.

---

### Post by jessemaurais on 2011-09-24
You don't need to install OSS. I got it to work with just ALSA OSS emulation.

```
sudo apt-get install alsa-oss
```

When that's done you can use

```
aoss fusion <name-of-the-rom-optional>
```

aoss wraps the program state so that it thinks it's using OSS. There's also the possibility of having ALSA make devices such as /dev/dsp but I didn't find this was necessary (probably overkill).

Anyway, it worked for me and was easy to get working. Frankly, I don't like changing system defaults if I don't have to and ALSA is installed by default with Ubuntu 10.10

---

