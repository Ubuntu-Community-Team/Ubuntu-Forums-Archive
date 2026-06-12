---
title: "Audacity and Hardy"
date: 2008-08-31
forum: Multimedia Software
---

### Post by boomcat on 2008-08-31
Here are my experiences with Audacity.

I have a Dell Dimension E520 desktop with a clean install of Hardy Heron.

I installed Audacity 1.3.4 to digitize some old 1/8” audio cassettes. I connected the cassette player outputs (stereo RCA plugs) to a “siamese” stereo miniplug cable and into the “Line Input” of the onboard stereo card. I started the cassette playing and started working on adjusting the mixer (from the Hardy desktop) until I could hear audio. There are so many available combinations of mixers (ALSA/OSS/STAC 97XX and several others) and inputs (PCM/Capture/Capture-1/Capture-2/Line-In and others) and outputs (Master Out/Mono Out) and Switches (Mic-In/Analog Audio Loop-Through) that this process took some time. It was thirty minutes before I could hear anything at all, and a full hour before I could adjust the audio input to a comfortable level for both listening and recording.

When I pressed the “Record” button on Audacity it recorded for two seconds, then hung. I had to “Force-Quit” it. I rebooted the desktop (Ctrl-Alt-Bksp) and tried again. Force-Quit. I restarted the computer several times and tried recording after each reboot; Force-Quit.

I read on the Ubuntu forum about disabling Pulse Audio, so I did that and tried recording again. After two seconds, freeze. Force-Quit. Rebooted and re-tried. Force-Quit.

I read on the Ubuntu forum about suspending Pulse Audio, so I tried that. Force-Quit.

I read on the Ubuntu forum about dropping back from Audacity 1.3.4 to 1.2.6, so I did that: I installed 1.2.6 from a DEB file on my desktop. The Audacity control panel on 1.2.6 is very difficult to read; the text is condensed and jammed together. But on this attempt Audacity began to record and I can't tell you how thrilling it was to watch the indicator pass the 2-second mark! The recording went on for over twenty minutes before crashing and locking the computer. Force-Quit would not work. I had to power down and restart. The audio file being recorded was lost.

Also, there is an “Update-Available” icon in the upper right trying to get me to update Audacity from 1.2.6 to 1.3.4. Annoying little thing!

And throughout all of this, I was never able to find any audio input adjustment that would affect the level shown in the Audacity “Input” window; it was as if it were stuck on “Preset” or “Auto”. It just wouldn't move.

So my evaluation is that this program is a little too buggy to use for recording.

---

### Post by boomcat on 2008-09-01
After using it for playback and editing, I have to add that Audacity is not ready there, either. It freezes, locks the computer, loses data and hangs. When restarting it tries to repair or recover damaged project files and puts a "progress" display window up; but after an hour of waiting it has made no progress at all.

Too bad, really, because it has a nice set of features and the control layout is good. The program itself though, is just not stable.

---

### Post by Tibor60 on 2008-09-07
I have also problems with Audacity, it hangs after converting 2-3 files to wav. Really, linux is useful only for fun and playing, but for doing my real work I need every time to reboot to windows. In every distro, as older problems solved, new problems occure.

---

### Post by bones16v on 2008-09-09
i used to use audacity in windows all the time with no problems what so ever, windows xp and windows vista, but i can't seem to get it to ******* work on ubuntu.  i can record one track and thats it, thats the only problem i have

---

