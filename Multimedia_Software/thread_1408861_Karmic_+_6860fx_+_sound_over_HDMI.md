---
title: "Karmic + 6860fx + sound over HDMI?"
date: 2010-02-16
forum: Multimedia Software
---

### Post by OobNosferatu on 2010-02-16
Hey guys.

I'm on a gateway P-6860FX, which has a 8800M GTS card from nVidia. It has hdmi output but only puts out video on my HDTV. It doesn't provide sound. I googled around a bit but can't figure it out. I don't even know if my hardware even supports HDMI. How do I find that out?

here are the results of aplay -L

```
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

the last part says S/PDIF, but I don't think i have an S/PDIF port...

But I think that implies HDMI, as I assumed by reading this post:

[http://ptspts.blogspot.com/2009/08/asrock-ion-330-nettop-with-jaunty.html](http://ptspts.blogspot.com/2009/08/asrock-ion-330-nettop-with-jaunty.html)

Anyhow, I tried using the following command (as modified from the above website) to no avail:

$ mplayer -ao alsa:device=iec958=intel $FILE

It didn't give me any errors either... it just played the video. 

Anyone know what the next step could be? Or what would you try?

---

### Post by OobNosferatu on 2010-02-18
anyone? 

anyone have an idea what I can do to find out if my hardware is even compatible, using linux?

---

### Post by tekman54000 on 2010-02-25
Hi, 

I'm exactly on the same boat with a GT210... Any solutions found?

---

### Post by OobNosferatu on 2010-05-03
Nope... I have resigned to the fact that it probably won't work... although I have also been unable to confirm that it is physically impossible. :(

---

