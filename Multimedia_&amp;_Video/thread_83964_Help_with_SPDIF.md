---
title: "Help with SPDIF"
date: 2005-10-30
forum: Multimedia &amp; Video
---

### Post by Kadafi on 2005-10-30
OK - video's working perfectly...

Now my problem is with SPDIF. I'm using ATI IXP AC97 - sound works through headphone jack perfectly, but for some reason I'm not getting sound through SPDIF.

Have unmuted the SPDIF, but still not getting any sound... any suggestions?


EDIT: For the sake of reference, have disabled the ATI IXP modem using the advice I found on this forum... also, I get: 

aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Perhaps there's some sound configuration file I need to set to play to card 0, device 1?

---

### Post by KrystoferRobin on 2005-11-12
I'm having roughly the same problem.  Sound works great over the headphones, but the speakers... nadda.  Can't find anything in reference to the problem, though strangely enough the sound DID work under Hoary, and under gentoo and fedora... something isn't right somewhere, if I peg it, I'll post a followup.  If anyone else has an idea, feel free to followup as well.

---

### Post by duvel on 2005-11-14
Add me to the list. I've got the same hardware as the OP with the same problem. The only thing I can add is that I installed kmix (I'm running Gnome) and in the switches window, I saw that the IEC958 has a red light. If I click it, the red light turns "on" (it's brighter). I have no idea what this means (it's not exactly intuitive, is it?), but, so far, this is the only "clue" I have that something is not quite right.

---

### Post by mcduck on 2005-11-14
Well, I don't have the same sound chip, so things might work differently to you. But I'll share this anyway as it might help you..

I use ALSA for sounds, and if I want some program to output to S/PDIF instead of analog outputs, I go to that program's sound settings, enter the ALSA configuration and then set audio device to 'hw0,2'. For me, 'hw:0,0' is analog. (I haven't even tried what 'hw:0,1' would do ;) )

This way the same program doesn't sound through both S/PDIF and analog, but I can select individual programs to play through my amplifier. So no system sounds or flash animations playing over my music :D

---

### Post by duvel on 2005-11-14
Thanks for your helpful reply, mcduck. I will try it and see what happens.

However, in the meantime, I found something rather interesting. I looked at the asound.state file (from Alsa).  Most of the settings seemed fairly normal. However, when I got to the IEC 958 Playback, it looked like this:
```
control.38 {
                comment.access 'read write'
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Default'
                value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }

```

It seems to me something is definitely wrong here!

---

### Post by duvel on 2005-11-14
mcduck, I tried the hw:0,2  in xmms and got an error ("Is your sound card properly configured?"). So, no luck there either.

---

