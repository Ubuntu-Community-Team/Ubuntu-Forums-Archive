---
title: "Audio problems in VLC of UBUNTU 9.10"
date: 2009-10-14
forum: Multimedia Software
---

### Post by eaglelord on 2009-10-14
Hello friends....

After upgrading to Karmic Koala... the audio from VLC is having some problems with some tap sounds for every 5 seconds while playing a movie.

Totem is also having some problem in seeking while playing a video
How to over come this problem?

Thanks in advance...

---

### Post by xjerryx on 2009-10-15
> **eaglelord said:**
> 
After upgrading to Karmic Koala... the audio from VLC is having some problems with some tap sounds for every 5 seconds while playing a movie.


same problem here....

---

### Post by mkngl84 on 2009-11-01
Same problem here while using ALSA or OSS in VLC.

Using ALSA in MPlayer does not skip, however.

---

### Post by Slippery on 2009-11-04
> Same problem here while using ALSA or OSS in VLC.
Using ALSA in MPlayer does not skip, however. 
Same situation , but after "clean installation" with old "/home" partition .

**SOLUTION:**
I've fixed it by removing VLC plugin for Pulse Audio
```
sudo apt-get remove --purge  vlc-plugin-pulse
```

---

### Post by stefano_to on 2009-11-08
same problem here! :( 
I've also tried to disable compiz, reroute video and audio output (strange, rerouting the video output on X11 doesn't make me have another window for the video... bohh) , but nothing helps: I've always interferences, and neither of this happened yesterday, on 9.04.

ah, removing pulse-audio plugin just made things worse for me ;)

---

### Post by stefano_to on 2009-11-08
ok, found a solution (at least it worked for me! :D )

so, go in the vlc preferences-->advanced (all)-->audio-->output-->ALSA , do a refresh if necessary and select the "hw:0,0" option. Then make sure also in the "simple" visualisation you are using ALSA hw:0,0 device as audio output. I had to do it twice to make it understand (don't know why!) but in the end it worked! 
):P

---

### Post by CaSt on 2009-11-13
Thank you very much! Worked perfectly for me, too... Had the same issue (mille grazie, fratello!)

---

### Post by bikodog on 2009-12-19
Stefano_to, that fixed it for me also

9.10 64 bit

---

### Post by jbraswell on 2010-03-11
Worked for me, too, 9.10 64-bit.  Although, I don't know what you're talking about with the visualization option; I don't appear to have it.  Anyway, though, changing the main audio setting worked.

Thanks!

---

### Post by Sylchat on 2010-05-01
Tried various things (removing pulse audio, choosing ALSA with hw:0,0, choosing OSS, etc) and I still had the problem under 9.10 64-bit with HD Audio (on an Asus P7P55D). Error messages with vlc -vvvv were always the same type: "audio output is starving (20171), playing silence"

Upgrading to 10.04 solved the issue!!! I'm happy :D

edit: Upgrading also solved the sensors issue with sensors-applet/lm-sensors4 showing only the GPU temperature. Now it detected CPU Fan & temp and other things.

---

