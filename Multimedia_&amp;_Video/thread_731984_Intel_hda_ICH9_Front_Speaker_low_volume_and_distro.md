---
title: "Intel hda ICH9: Front Speaker low volume and distrortion"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by ksenos on 2008-03-22
Hello all,

A month ago I bought a new PC that has an on-board audio controller (82801I ICH9 Family HD Audio Controller). Apart from some issues with support in few games I have a big problem with the front microphone. It seems that when I increase the capture gain the DC offset of the input also increases.  So if I set the volume to more that 60% I get a distortion and I set to less the recording volume is very low. 

This could be either a hardware or driver problem. However, I would like to ask if there is a work-around that would perform software amplification (in real time so it would work with Skype for example). Therefore I would set the recording level to 50% and let the software amplifier do the rest with increasing the DC offset. 

Is there any way I could do the above by a special configuration on alsa? Thanks in advance.

P.S. The above effect is illustrated in the following image:

[IMG]http://www.everliving.gr/shared/capturing.png[/IMG]

Notice how the DC offset increases while the recording level is also increased. No microphone was attached.

---

