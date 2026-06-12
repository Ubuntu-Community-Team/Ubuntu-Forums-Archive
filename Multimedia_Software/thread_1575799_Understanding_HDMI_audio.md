---
title: "Understanding HDMI audio"
date: 2010-09-16
forum: Multimedia Software
---

### Post by applegrew on 2010-09-16
Hi All,

Please take a moment to share the facts you have regarding HDMI audio. Sorry for the long post though.

The thing I am trying to understand is that Graphics cards (like my Nvidia Geforce 250GTS) which have HDMI output, are they capable of providing HDMI Audio-out too? Or they actually need other hardware on the motherboard to provide the HDMI audio, and the graphics card simply routes that through itself?

For hours I have been trying to get HDMI audio output but to no avail on my Kubuntu. Is there a way to check if my hardware is capable of HDMI audio?

---

### Post by videodrone on 2010-09-16
Hello Applegrew.

My GT240 sends 5.1 audio over hdmi cable to my receiver. Programs like vlc or XBMC work well.

The speaker-test program can be run to test your card for example :-

speaker-test -D hw:1,7 -c2
or 
speaker-test -D hw:0,7 -c2
or 
speaker-test -D default -c2

try these, you will hear white noise from your front speakers if you are successful.

regards
'drone

---

### Post by applegrew on 2010-09-17
> **videodrone said:**
> Hello Applegrew.

My GT240 sends 5.1 audio over hdmi cable to my receiver. Programs like vlc or XBMC work well.

The speaker-test program can be run to test your card for example :-

speaker-test -D hw:1,7 -c2
or 
speaker-test -D hw:0,7 -c2
or 
speaker-test -D default -c2

try these, you will hear white noise from your front speakers if you are successful.

regards
'drone

Hey thanks for the reply. One question though... What does hw:1,7 hw:0,7 signify? From the man page it seems it is the PCM device name. How do I find the PCM device name of my audio devices?

---

