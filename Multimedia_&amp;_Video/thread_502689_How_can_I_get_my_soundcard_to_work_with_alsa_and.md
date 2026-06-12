---
title: "How can I get my soundcard to work with alsa and"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by jazzman14 on 2007-07-16
I can't get jack to run with my soundcard. I keep changing the period but still get this message:

13:25:29.862 Patchbay deactivated.
13:25:30.065 Statistics reset.
13:25:30.420 MIDI connection graph change.
13:25:30.425 MIDI connection change.
13:26:20.142 Startup script...
13:26:20.143 artsshell -q terminate
sh: artsshell: not found
13:26:20.580 Startup script terminated with exit status=32512.
13:26:20.612 JACK is starting...
13:26:20.622 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p64 -n2 -m
13:26:20.658 JACK was started with PID=8884 (0x22b4).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
13:26:22.498 JACK was stopped successfully.
13:26:22.507 Post-shutdown script...
13:26:22.516 killall jackd
jackd: no process killed
13:26:22.745 Could not connect to JACK server as client. Please check the messages window for more info.
13:26:24.401 Post-shutdown script terminated with exit status=256.

After running lshw -class sound i get this:

*-multimedia            
       description: Multimedia audio controller
       product: Vortex 2
       vendor: Aureal Semiconductor
       physical id: d
       bus info: pci@01:0d.0
       version: fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=au8830 latency=64 maxlatency=12 mingnt=4
       resources: iomemory:f4200000-f423ffff ioport:3028-302f ioport:3020-3027 irq:9 



Any ideas? Thanks!

---

### Post by jazzman14 on 2007-07-17
anybody?

---

### Post by fredj on 2007-07-18
First check that your soundcard is set to work through Alsa. Open the alsa mixer, go to the File->
Change Device menu and make sure that the Aureal Vortex (Alsa Mixer) is selected. It may not be called 
that exactly but you should be able to see which one it is. Then from the System -> Preferences menu 
select Sound and check that Alsa is selected there also and that you can play the test and system sounds etc.
See if you can play music i.e. wav or mp3 files etc. Then let us know the result here.

---

### Post by fredj on 2007-07-18
I notice reading your jack error mesages again that one of them says
'Cannot use 2 periods for capture' so try increasing the periods in the setup screen to 4.

---

