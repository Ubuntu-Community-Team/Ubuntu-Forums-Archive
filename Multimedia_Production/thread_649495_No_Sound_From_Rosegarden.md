---
title: "No Sound From Rosegarden"
date: 2007-12-25
forum: Multimedia Production
---

### Post by ejacka on 2007-12-25
My sound card is working in Dynebolic. I configured the audio settings for my card & opened an .rg file in Rosegarden but can hear no sound, even though the meters are pumping. I don't understand JACK but when I start it, I get the output log below* & in the window it says Started or Active then Stopped.

Sound card: M-Audio Audiophile 2496
RAM: Crucial 1GB
CPU: AMD Sempron 3200+
Motherboard: ABIT AN7

*
03:49:47.117 Patchbay deactivated.
03:49:47.148 Statistics reset.
03:49:47.153 Startup script...
03:49:47.153 artsshell -q terminate
03:49:47.190 MIDI connection graph change.
sh: artsshell: command not found
03:49:47.393 Startup script terminated with exit status=32512.
03:49:47.395 JACK is starting...
03:49:47.396 jackd -R -dalsa -dhw:0 -r48000 -p1024 -n2
03:49:47.408 JACK was started with PID=9879 (0x2697).
jackd 0.100.0
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
03:49:47.609 MIDI connection change.
03:49:49.621 Server configuration saved to "/root/.jackdrc".
03:49:49.622 Statistics reset.
03:49:49.674 Client activated.
03:49:49.675 Audio connection change.
03:49:49.677 Audio connection graph change.

---

### Post by Pocadotty on 2007-12-25
Does JACK work for you with other programs?... if JACK isnt working you wont get anything out of rosegarden or any other app that requires JACK (ie hydrogen).

Also make sure that rosegarden's "master out" channels are connected to alsa_PCM.  If you dont know how to do this, try Patchage, which is a graphical way to manage JACK connections.

---

### Post by ejacka on 2007-12-26
I am fairly new to Linux, how do you install Patchage, is it a part of the OS? I can stream audio from the web, when I try to stream with StreamTuner, XMMS audio player pops up with the message: "couldn't open audio - please check that: your soundcard is configured properly, you have the correct output plugin selected, no other program is blocking the soundcard".

Audacity: Error Initializing Audio - There was an error initializing the audio i/o layer. You will not be able to play or record audio. Error: Host error. (Audacity doesn't show up in JACK)

Hydrogen drum machine = working
Amarok audio player = working

---

### Post by stmiller on 2007-12-27
Is the rosegarden song only MIDI? Then you'll need to have some sort of soft synth or timidity installed and running to have sound. MIDI is only data, so Rosegarden is only sending out the MIDI data.

And don't run jack as root. Just use the qjackctl as a normal user.

---

### Post by ejacka on 2008-01-01
The file I ran was "bogus-surf-jam.rg" from a Rosgarden folder. I open JACK by right clicking on the desktop & selecting it from the audio menu, then clicking the start button to run it.

---

