---
title: "mythbuntu hdmi to tv overscans and no audio"
date: 2010-06-30
forum: Mythbuntu
---

### Post by theshiznojudge on 2010-06-30
i just installed mythbuntu 10.04 on my acer aspire m1100, but the output to my tv (th42px80u) through my geforce 8500 gt (hdmi) and it's overscaning the screen. the audio through hdmi isn't working either. i had i working on vista right before i installed mythbuntu (ironic isn't it?). i installed nvtv, but when i click on it to start, noting happens. i searched the internet for several hours without success. i updated the nvidia driver, but still nothing.

---

### Post by larsolav on 2010-07-01
Did you unmute HDMI in alsamixer?
Did you set the audio to HDMI in Mythtv setup?

Cheers!

---

### Post by theshiznojudge on 2010-07-03
i got the overscan worked out (i installed the other driver shown and the overscan option in nvidia panel worked).  i went to asla mixer and made everything visible and unmuted them all, and unfortunately it's not working. i looked through myth tv front end and back end settings and i couldn't find the relevant setting, am i in the right place?

---

### Post by nickrout on 2010-07-03
Setup - General on the frontend and set your output device to ALSA:hdmi

---

### Post by newlinux on 2010-07-03
does your audio via HDMI work with outside of myth? what does aplay -l return?

---

### Post by theshiznojudge on 2010-07-07
i changed the output device to hdmi and spdif (i remember that was the name of the internal connection i used), but neither of them worked. i do have an old crappy speaker that i plugged into the headphones, so that is working. what's aplay? im a noob.

---

### Post by nickrout on 2010-07-07
> **theshiznojudge said:**
>  what's aplay? im a noob.

it is a command you run in a terminal.

---

### Post by theshiznojudge on 2010-07-09
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by nickrout on 2010-07-09
and aplay -L ? (there is a difference between uppr and lower case "L" in the command.

---

### Post by theshiznojudge on 2010-07-10
jon@linux-pvr:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, ALC888 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output

---

