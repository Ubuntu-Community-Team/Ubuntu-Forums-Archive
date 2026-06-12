---
title: "No sound in Hardy (PulseAudio)"
date: 2008-04-24
forum: Multimedia Software
---

### Post by entwoska on 2008-04-24
So I installed the Hardy Heron RC yesterday night only to discover that there is no more sound coming out of my sound card. (Everything else got pretty smoothly actually)



So I checked Ubuntu's wiki concerning PulseAudio ([https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)) and did what was suggested.

Unfortunately, no sound is coming out of my speakers. I returned on my Gutsy Gibbon partition and everything is alright.

I did a test with Amarok and VLC and tried to play a mp3. I then went to the "Volume Meter (Playback)" from the PulseAudio applet and there is some activity on both rows. Alas, no sound.

The volume meter checks signals on ALSA PCM on front:0 (ADC Capture/Standard PCM playback) via DMA, if this is of any help....

Is there something I should configure to get some sound? I'm new to PulseAudio and don't really know were to get started.

What should be my "Default Server" Sink and Source ?


Any help would be greatly appreciated!!
Thanks in advance :)

---

### Post by entwoska on 2008-04-25
Anybody ?

I'm pretty sure I'm not too far from a solution...


I have set all the correct options in the Sound section, my soundcard is detected no problems there.

The only thing that may be troublesome is the PulseAudio Default source, sink and server. Shall I put them all to my localhost ?

Please any input would be greatly appreciated, since using a computer with no sound is greatly infuriating!

If you need any info on my system, don't hesitate and ask.


Thank you!

---

### Post by entwoska on 2008-04-25
Ok hi people, after some hard work I managed to make the sound work.



I figured out that this was a KNOWN bug since 2005 !!
(Why this is not resolved yet is beyond my comprehension....)


[https://bugs.launchpad.net/ubuntu/+bug/25632](https://bugs.launchpad.net/ubuntu/+bug/25632)

---

### Post by ristoid on 2008-04-26
I'm having the same problem, would you mind giving more details on how you solved it?

---

