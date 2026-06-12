---
title: "Help understanding MIDI, JACK, and ALSA"
date: 2013-02-03
forum: Multimedia Software
---

### Post by JoelAV on 2013-02-03
Hey all,

I need some help understanding how JACK, ALSA, and MIDI interact.  Specifically, I want to understand why I'm having so much trouble routing MIDI traffic between different devices and programs.  

Even more specifically:  I have an ancient MIDI keyboard.  Well, it's sort of a MIDI keyboard.  It was originally designed to be used with some wretched old keyboard training software for MS-Something 95, and instead of a real MIDI port, it plugs into a SoundBlaster Game port, gets its power from that, and sends MIDI signals to the PC that way, without any need for the r@re proper MIDI adapter for the Game port.  It's an odd-ball device, I know, but that isn't the problem.  Really.  I can hook it up to the sound card's Game port, and find it in Qjackctl's MIDI tab as midi_capture_1.  I can route this to midi_playback_2, which is apparently the USB MIDI adapter I have plugged in, and get sounds out of my Meeblip Micro.  Cool.

What I don't understand is why I don't seem to be able to connect midi_playback_2 to, for example, Zynaddsubfx.  It does not appear on the MIDI tab.  It does show up under the ALSA tab in Qjackctl, but midi_capture_1 (the keyboard) does not, and nothing that shows up under the ALSA tab seems to be connected or connectable to the MIDI keyboard at all.  The only thing that appears to show up in both tabs is the USB MIDI adapter cable.  

I have also tried patchage.  There I can get midi_playback_2 and Zynaddsubfx to show up on the same page, but if I try to connect the two, I get an error message:  "WARNING: cannot make connection, incompatible port types".  So, MIDI out and MIDI in are incompatible port types...

I gather that there are two layers at work here:  ALSA and JACK.  But both Qjackctl and patchage are aware of, and can control both.  So why on earth can't they bridge the two.  Isn't that what software is for?  Or am I missing something more fundamental in my understanding of how these subsystems relate?  Is there some other program that I should be using that will allow me to get all these MIDI devices to interoperate?  Can anyone here provide a more clear explanation of how MIDI, JACK, and ALSA are supposed to be used together?

FWIW, the machine in question is running Lubuntu 12.04 on a P4.

In gratitude for any additional insight,

Joel Ewy

---

### Post by JoelAV on 2013-02-19
So, does anybody here understand this stuff better than I do?  Surely somebody must know how this is supposed to work.

---

### Post by JoelAV on 2013-03-06
The only sound to be heard was the wind whistling across the desolate and empty plain...

Seriously, nobody who reads this forum has any more idea than I do how this stuff is supposed to work?  :)

JCE

---

### Post by su:bhatta on 2013-07-05
try this thread, has some useful stuff...
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

