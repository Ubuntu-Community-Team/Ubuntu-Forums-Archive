---
title: "Setting proper volume levels for line recording"
date: 2013-07-18
forum: Multimedia Software
---

### Post by cscj01 on 2013-07-18
My current configuration is Ubuntu 12.04.2 x64 and Audacity 2.0.0 with an on-board sound card, an Intel Panther Point High Definition Audio Controller with a Realtek ALC898 CODEC.

I am digitizing my LP collection (have been for several years now) using Audacity, and I find that pavucontrol is not adequate to control line-in volume to prevent overloading. So I have to use either alsamixer or gnome-alsamixer. This problem did not start until 12.04.

gnome-almixer has no markings to indicate volume amount, so I have to guess at what I am setting except for 0% or 100%. On the other hand, alsamixer seems to not be in synch with what the volume actualy is. That is, if I have the volume for Line-in at 81%, it overloads my Audacity waveform. The Audacity wave form shows many flat tops and bottoms, although there is no clipping and the meters are well below the maximum.  If I run the same source (turntable through receiver to tape out) to my tape decks, I have no problems with sound levels.  I have to set the alsamixer volume at about 50% to aviod overdriving my sound waves when sending my source to the sound card.  At this setting, the wave form is so small as to be barely detectable (appears as a straight line with small protubances on it) and is usually anywhere from -20 to -30db.  It is very hard to tell whether the wave is "clean" with it being so small.

So is there one application I can (should) use to set my volume levels so that I don't have to use 3 different ones? Or, is there a way I can set one of the above mixer apps so that the other is controlling what is actually happening?

---

### Post by ajgreeny on 2013-07-18
How are you actually transferring the audio by line-in; are you using the output direct from a turntable or output from your amplifier?

The latter ought to work OK but if you're trying to use the direct turntable output it is likely that the problem will continue, as output will not be appropriate for a line-in input system.

Have a read through [http://ubuntuforums.org/showthread.php?t=2154383](http://ubuntuforums.org/showthread.php?t=2154383) a thread which I replied to with a little knowledge; dangerous, I know, and I learned a lot about audio recording from a turntable.  You might find a tip or two that help you do the same.

Good luck!  Let is know what works.

---

### Post by cscj01 on 2013-07-19
> **ajgreeny said:**
> How are you actually transferring the audio by line-in; are you using the output direct from a turntable or output from your amplifier?

The latter ought to work OK but if you're trying to use the direct turntable output it is likely that the problem will continue, as output will not be appropriate for a line-in input system.

Have a read through [http://ubuntuforums.org/showthread.php?t=2154383](http://ubuntuforums.org/showthread.php?t=2154383) a thread which I replied to with a little knowledge; dangerous, I know, and I learned a lot about audio recording from a turntable.  You might find a tip or two that help you do the same.

Good luck!  Let is know what works.

I am feeding the source through the receiver, not directly from the turntable.  However, I have finally resolved this issue.  Here's my solution.

[LIST=1]
[*]In Audacity, I chose Pulse as my output device and Pulse Line 1 as my input device.
[*]In alsamixer, I set the three Capture devices to 50%.
[*]I can then set the Recording and Input Volumes in pvacontrol to what I need to get a good wave without clipping.
[/LIST]

Why this is such a hassle in Linux, I'll never understand.  It seems to me if someone sets the System Volumes in Sound Preferences, that should be the only place required to set it other than minor tweaking in the application.  But no, there are all these different snippets that mess with volumes both out and in.  I know that I don't really know the architecture and processes of ALSA, but shouldn't there be a way to tame this monster?

Okay, my rant is done.  I really love Linux and would never go back to Windows, so perhaps I should do a little exploratory reading on ALSA and Pulse.  Does anyone have any suggestions for clear and concise presentations of these two subjects on the web?  With that last question, I'll mark this thread as solved.

---

