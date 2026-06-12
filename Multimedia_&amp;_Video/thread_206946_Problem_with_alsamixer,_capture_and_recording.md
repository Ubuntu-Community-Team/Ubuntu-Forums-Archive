---
title: "Problem with alsamixer, capture and recording"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by elims on 2006-06-30
Hi there,

i have a probleme with the sound. Nearly everything worked out of the box. Except one detail. As i tried Skype (1.3 beta with ALSA) the other part heared a very annoying echo. I figured out that this comes from capturing the output of my soundcard and pipeing it to the input. If i deselect capuring from the capture slider in the gnome ALSA mixer i won't have the the output mixed with the input. Unfortunately i'm also not able to record with the Mic anymore. 

Recording with capturing (other part hears echo)
Mic: capture on
Capture: capture on

Mic not working:
Mic: capture on
Capture: capture off

Is there a way to have only the Mic as input and not only the captured output?

I have a Dell Inspiron 8200 with a Intel 82801CA-ICH3 Sound card (according to the mixer).

Thats the only reason why i have to boot in windows every morning and i realy would like to throw windows of the laptop. 

Many thanks!

---

### Post by joehill on 2006-07-01
I'm having the same problem.  I've been skyping without problem for some time now.  I don't know what I changed, but now the other party hears an echo and I've gone back to expensive land-lining for the moment.

One thing I've noticed is that while controlling the mic volume on alsa-mixer works, controlling the "capture" settings (the slider, selecting/deselecting input and playback) doesn't seem to have any effect, even though I can go through the motions of changing settings.

---

