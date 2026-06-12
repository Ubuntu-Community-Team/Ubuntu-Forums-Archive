---
title: "USB Soundcard for recording MIDI and audio via RCA connection"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by djxcon on 2007-10-16
I know that there have been a few posts about recommended sound cards but I still have a few questions about what is currently supported.  

**Here is what I am looking for:**
Must connect via USB
Must have Midi support (inputs at least and hopefully outputs)
Must have RCA inputs to record audio
Must have RCA outputs to playback audio

After reading various posts, the ALSA web page, and the Ubuntu wiki for supported sound cards, I believe that I may have some luck with the Edirol UA-4FX.  I don't believe the effects will be necessary for my recording purposes but if they work, great!   Has anyone used this card with Ubuntu and successfully recorded Midi events as well as audio? 

If not the Edirol, please let me know if you have found a USB card that does have this functionality.

Currently, I am using an M-Audio 2496 PCI card and it does exactly what I need but now I am looking to go mobile.  For anyone looking for a great PCI card, the M-Audio 2496 is outstanding!

---

### Post by djxcon on 2007-11-15
Well here is what I have found using the Edirol UA-4FX soundcard on UbuntuStudio Gutsy (lowlatency kernel)

Features that work out of the box:
RCA Input
RCA Output
Input knob
Output Knob
Advanced Effects
Headphone Jack
Sample Rate 44.1
Analog Recording Source

Features not yet working:
MIDI (Have only tried Rosegarden)

Features not yet tested:
Digital In/Out
Mic In
Guitar In
Sample Rate other than 44.1
Recording Source other than analog

---

### Post by steevc on 2007-12-04
The UA-4FX looks to be pretty much what I want in order to do some basic recording. Have you had a chance to test the other inputs? Is it just a matter of flicking switches to use them?

I've not found much other detail on using it with Linux, but this post on the ALSA list seems promising

[http://article.gmane.org/gmane.linux.alsa.devel/50060](http://article.gmane.org/gmane.linux.alsa.devel/50060)

My main requirements are to record some guitar and acoustic instruments, e.g. violin. MIDI would be handy to let me do some keyboard work. I've only got a cheap microphone for now, but if I get something that needs phantom power then this should handle that too.

---

### Post by djxcon on 2007-12-09
UPDATE:
MIDI may not work on this device in Linux...still trying.

REASON:
After reading the manual for this device, it seams that midi is only available when the driver switch is set to "advanced."  This switch requires the advanced driver to be installed which I don't believe is available in Linux. If I set the switch to advanced, the JACK audio server will not start.

---

