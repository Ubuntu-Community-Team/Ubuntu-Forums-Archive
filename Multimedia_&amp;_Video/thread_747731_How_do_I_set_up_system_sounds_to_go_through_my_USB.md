---
title: "How do I set up system sounds to go through my USB audio?"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by Playa1313 on 2008-04-06
I can't seem to find a solution on the forums, however I can imagine it is relatively simple to solve.

I have all of my sound outputs set to USB audio like this:

[IMG]http://img390.imageshack.us/img390/161/usbaudiojs1.png[/IMG]

Yet, when I go to the system sounds tab and test the sounds or even when I log in, etc, it all comes through my on-board sound card.

All of my other apps work with my USB audio

I tried using **sudo asoundconf set-default-card Audio**, but that didn't work.

Any suggestions?

Also, I have taken a look at PulseAudio.. but it scared me by looking too complicated.  I understand it can be used to set up two soundcards to work at once.  Is this possible in any other way?

---

### Post by Riverine on 2008-04-11
I have the same or a very similar problem.   I have both on-board and usb audio processors.  When I set my system sound preferences to the usb audio some programs (rhythmbox, totem, system sounds) use the usb audio as expected, but others (totem browser plugin, last.fm) continue to use the on-board sound.

---

### Post by Playa1313 on 2008-04-11
> **Riverine said:**
> I have the same or a very similar problem.   I have both on-board and usb audio processors.  When I set my system sound preferences to the usb audio some programs (rhythmbox, totem, system sounds) use the usb audio as expected, but others (totem browser plugin, last.fm) continue to use the on-board sound.

I found that installing "padevchooser" and using pulseaudio solved ALL my problems.  Excellent utility.  I LOVE IT.

---

### Post by Riverine on 2008-04-12
Thanks for the pulse audio device chooser tip.  It does the job.  One note to anyone else who tries it:  make sure the options on the devices tab at System => Preferences => Sound are set to PulseAudio Sound Server.

---

### Post by Playa1313 on 2008-04-13
> **Riverine said:**
> Thanks for the pulse audio device chooser tip.  It does the job.  One note to anyone else who tries it:  make sure the options on the devices tab at System => Preferences => Sound are set to PulseAudio Sound Server.

Yes, that is an important note.

Thanks.

---

