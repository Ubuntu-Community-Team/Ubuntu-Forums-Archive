---
title: "[SOLVED] spdif out no slider action in alsamixer"
date: 2008-01-13
forum: Mythbuntu
---

### Post by volkswagner on 2008-01-13
I am trying to get spdif out to my 5.1 receiver.

```
eric@FamilyRoom:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Do I need .asoundrc?  If so what do I call my sound card based on the info above.  I can see ALC882 Digital but there is not any mention of iec958.

In alsamixer I have unmuted IEC958 but I can not move the slider as in the analog controls.  I have tried all listed sound devices in audio settings.  I also tried listing as posted on forum, ALSA:spdif and others.

Created the .asoundrc in this thread

[http://ubuntuforums.org/showthread.php?t=630533&highlight=spdif]("http://ubuntuforums.org/showthread.php?t=630533&highlight=spdif")

> 
I'm not going to say this solution will necessarily work for you, but it works for me.

~$ cat .asoundrc
Here is the ~/.asoundrc i'm using
Code:

pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}

It forces all audio out spdif all the time. Seems to work consistently and in all apps i've tried.
__________________
Thanks


This gave me the visual volume slider while playing musici via f11 and ], but not sound and no action in alsamixer for IEC958

Is this a partial file?

---

### Post by volkswagner on 2008-01-14
Realized my syntax, needed captial -L.

```
eric@FamilyRoom:~$ aplay -L
front:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
iec958:CARD=HDMI,DEV=0
    HDA ATI HDMI
    IEC958 (S/PDIF) Digital Audio Output
```

What does the null mean?  Is this related to the spdif or the HDMI?

What should my sound device read in myth audio settings?

---

### Post by volkswagner on 2008-01-14
Well I got it working, I set the sound output device to default, DUH! 

I added the following line to .asoundrc


format S16_LE

So it is exactly as in this post

[http://ubuntuforums.org/showthread.php?t=654288&highlight=spdif]("http://ubuntuforums.org/showthread.php?t=654288&highlight=spdif")

It is working in music and live TV.

:)

---

