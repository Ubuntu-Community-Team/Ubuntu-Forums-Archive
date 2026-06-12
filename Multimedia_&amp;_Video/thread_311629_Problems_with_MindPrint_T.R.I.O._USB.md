---
title: "Problems with MindPrint T.R.I.O. USB"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by ReinaDelSur on 2006-12-03
Hi,

I'm utterly new to Linux but I have great hope that, in time, it can replace Windows and all the things I have to do with it still.

One of these things is editing my sound files: I'm a teacher and I'm constantly recording WAV files to burn onto CDs to go with a lesson plans a colleague and I create. I need a multi-track recorder with effects capability (noise reduction, reverb, the lot).

I thought I had found all this using Ubuntu Edgy amd64 (I have a Intel E6400) with my USB MindPrint T.R.I.O. sound card and Ardour.

However, I ran into several problems since the beginning and the installation is still not functional.

I'll list everything down here, not even knowing whether these things are related and I hope you guys can tell me about them...

1. When I hit System/Preferences/Sound and I test the sound card for playback, I either get the test tone or distorted sound, depending on the day I test it  The setting that seems to work best is neither USB audio not ALSA but ESD (whatever that means!)

2. When I hit Test for the last setting, Sound Capture (which I think is equivalent to Mic In, isn't it?), I get the following error message:

"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource."

and of course the Mic In input is not working (I can't capture any sound in Ardour  I loved buying a $110 condenser mic for zilch...)

3. When I go to the ALSA website, there are no drivers for MindPrint TRIO (the company name isn't even listed in there...) Of course, as you might have guessed there are no Linux drivers from MindPrint either [http://www.mindprint.com/cms.php?scr..._id=&pr_id=118](http://www.mindprint.com/cms.php?scr..._id=&pr_id=118)
There a Windows, a Mac OS and an Intel Macs driver (whatever the last one is!)

4. When I start Jack, even though I followed all the advice I read in the UbuntuStudio wiki, it closes unexpectedly, and I see messages such as

"08:30:35.873 Patchbay deactivated.
08:30:35.882 Statistics reset.
08:30:35.893 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:457snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
08:30:45.542 Startup script...
08:30:45.542 artsshell -q terminate
sh: artsshell: not found
08:30:45.747 Startup script terminated with exit status=32512.
08:30:45.748 JACK is starting...
08:30:45.749 jackd -R -t5000 -dalsa -r48000 -p64 -n2 -D -Chw:1 -Phw:1
08:30:45.759 JACK was started with PID=7218 (0x1c32).
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|64|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 64 frames, buffer = 2 periods
Note: audio device hw:1 doesn't support a 32bit sample format so JACK will try a 24bit format instead
nperiods = 2 for capture
Note: audio device hw:1 doesn't support a 32bit sample format so JACK will try a 24bit format instead
nperiods = 2 for playback
ALSA: cannot set hardware parameters for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
08:30:46.053 Could not connect to JACK server as client. Please check the messages window for more info.
could not attach as JACK client (server has exited)
08:30:46.065 JACK was stopped successfully."

Or, when I force 16-bit in the settings, Jack tells me that 16-bit is not supported, so it'll attempt 24-bit, but I still end up getting the same result, which I don't understand, as my sound card supposedly supports 24-bit / 96 kHz.

In a nutshell, I'm helpless. Anyone can help?

Thx a zillion times!

---

### Post by ReinaDelSur on 2006-12-13
Please, you guys, could somebody help me out there? Or is my sound card totally out of the Linux game?

Thanks,

Ari  ;o)

---

### Post by rekado on 2008-05-15
This thread has been dead for a long time - but I still encounter the very same problem in Ubuntu 8.04.

I cannot get the recording/capture test done with my Mindprint TRIO connected. Sound output works flawlessly, though.

Any hints?

---

