---
title: "Linux Volume Problem"
date: 2010-01-10
forum: Multimedia Software
---

### Post by ninja togo on 2010-01-10
I have searched and searched through the forum but, finding the solution seems impossible.

My problem is that the output volume on my PC speakers using Linux seems extremely low compared to that found (heard?) in my Windows partition.

30% volume in Windows is equal to 50% in Linux from the external microphone recording tests I ran.

Is there any way to fix this problem or can it be that my sound card (SoundMAX) was fine-tuned by the manufacturer (HP) for Windows?

I have seen this problem come up in posts from the days of Ubuntu 7.10 but not later; they all had responses saying to edit the settings in alsamixer, but some said not to trouble the PCM others said to set it to maximum.

What should I do?

---

### Post by RedSingularity on 2010-01-11
In a terminal type 

alsamixer

Make sure the volume settings are all the way up.

---

### Post by ninja togo on 2010-01-11
Sorry for the late response (Had homework to do).
I have turned up the PCM setting to 100 and still not really a huge boost to the volume. The Linux:Windows ratio is still like 0.6:1. I have to really turn it up to hear anything or use earphones; not really what I want.:(

Is there anything I can do software-wise to make it any louder; I know I can plug in external powered speakers but that is not practical when on the go.

---

### Post by benerivo on 2010-01-11
If you are using pulseaudio then you could try to install the sound mixer to see if you amplify the sound output. See this thread...

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

---

### Post by ninja togo on 2010-01-11
> **benerivo said:**
> If you are using pulseaudio then you could try to install the sound mixer to see if you amplify the sound output. See this thread...

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

OMG!!!:D 
You found the solution! Thank you. No more low audio. (Nearly deafened myself from the volume being set so high)

Also thank you RedSingularity for you help too.


*Now a happy camper:KS*

---

