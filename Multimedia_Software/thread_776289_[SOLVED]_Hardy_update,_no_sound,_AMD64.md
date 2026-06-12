---
title: "[SOLVED] Hardy update, no sound, AMD64"
date: 2008-04-30
forum: Multimedia Software
---

### Post by impert on 2008-04-30
Hi all,

I've just upgraded to Hardy and lost my sound. I've followed the instructions in the Comprehensive Sound Guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

which worked perfectly for me under Gutsy, but not with Hardy.
I've removed and re-installed  linux-sound-base alsa-base alsa-utils as suggested in the Guide.  And I've rebooted more times than I can count.
My sound card shows up with aplay -l
My user name is listed in the audio group
grepping  /etc/group gives

```
cam@cwpc:/$ grep 'audio' /etc/group
audio:x:29:cam,camw,cw


```


```
cam@cwpc:/$ cat /etc/modprobe.d/alsa-base
```
gives:
.```

.
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-ca0106 index=0
options snd-hda-intel index=-2
cam@cwpc:/$ 
```

I've put the -2 for the Intel on-board card because it burnt out a year or so ago. The Sound Blaster card works because I get the drumbeat at login

/etc/modules has 
> fuse
lp
rtc
snd-ca0106

as the only uncommented lines.

I've tried selecting alsa in all three choices in the System>Preferences>Sound menu in order to disable Pulse.

I'm running the 2.6.22-14-generic kernel (the 2.6.24 won't boot) on an AMD 64 3700+

Any help would be appreciated.

---

### Post by impert on 2008-05-01
Update:
I no longer have the drumbeat at login.
I've removed and re-installed pulseaudio and its modules.

aplay -L gives:
> cam@cwpc:~$ aplay -L
front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
.
.(followed by a lot of stuff on speakers and the ca0106 card, and then:
.
> .
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, AD198x Analog
    Front speakers


The VT82xx died long ago in mid-symphony. Could this be the problem, and if so, how do I fix it?
Anyone?

---

### Post by buzzmandt on 2008-05-01
is the vt82 on board sound?  if so make sure it's dissabled in bios.  if not do so and it should fix the problem.

---

### Post by impert on 2008-05-01
buzzmandt:
Thanks for your reply, but I haven't touched the bios settings for yonks, and it worked before the upgrade to Hardy. Also I've just found that the sound works in (shudder!) Windows.

Update: Tried your suggestion. No difference, I'm afraid. Sound still works in Windoze, not in Ubuntu.

---

### Post by impert on 2008-05-03
Anyone there?

---

### Post by Zorael on 2008-05-04
See if anything over at [http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649) applies.

---

### Post by impert on 2008-05-04
Thanks Zorael, for your reply. My sound card (the only one that works) is a Sound Blaster Audigy LS. It shows up with aplay -l
> card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ca0106 is the correct driver for this card, and it worked under Gutsy.
Following your suggestion on the other thread, I'm going through ALSA-Configuration.txt now.
Cheers.

Didn't find anything I could use.

---

### Post by impert on 2008-08-09
Oops. Should have marked this as solved long ago. From memory, it was done by removing and re-installing the Alsa stuff, several times, as it didn't work the first time around.

---

