---
title: "USB turntable direct output to speakers"
date: 2009-12-26
forum: Multimedia Software
---

### Post by crtbt on 2009-12-26
I just got an Ion TTUSB turntable and it works fine for recording audio in Audacity (all I have to do is set the recording device to "ALSA: USB Audio CODEC : USB Audio (hw:1,0)"), but I can't figure out how to just play music from the turntable through the computer speakers.  Maybe there's something really obvious that I'm overlooking, but I can't seem to find anything.  I'm running Jaunty and audio playback is through ALSA and onboard NVidia nForce2.  I searched around and couldn't really find anything to help me, which isn't too surprising, since most of the marketing for these turntables seems to be aimed at people who want to turn their records into mp3s and never play them again.  Though the same problem seems to come up sometimes with USB microphones (ex. [this thread]("http://ubuntuforums.org/showthread.php?t=879331"), no replies).

Thanks,
Alex

---

### Post by nerdy_kid on 2009-12-26
could use JACK.... u might be able to do it with PulseAudio, but not sure.  In Karmic, just open the volume mixer and you might be able to get something going. JACK will work but most of the other sound apps wont work.

---

### Post by RaumTrug on 2009-12-26
Hi there!

it all depends on the latency you want, i.e. how fast you want the audio react from the turntable to the speakers!

I don't know about pulseaudio as I deinstalled it, maybe there's an option somewhere for software play-through from one device to another...but maybe that's only available for 9.10.

if you just want to playback and don't care about latency, you could try setting up jack with the hw of the turntable as capture device and the hw of the soundcard as playback device, and set a way high latency...you'll probably have certain x-run issues, but it can work, for my usb-mic it did at latency > 40ms (which is pointless for a mic...).

if you want to scratch/live mix, you'll need some fiddling with jack, like trying to get alsa_in and alsa_out for the jack version in ubuntu from somewhere (those sounded real icky when I last tried them). what I did for my usb mic was compiling jack2 myself & using the netjack audioadapter: that works pretty well, and the latency is near to being acceptable for life monitoring. both, the alsa_xx and audioadapter are normally used to slave a pc via network connection to jack and load & synchronize the soundcard there, but they are also handy for using multiple soundcards/devices on a single machine, which is what you'll want to do when trying to playback an usb device via the soundcard. you only have to keep in mind that the audio will be resampled for the adapter devices, so they loose a little crispness eventually.

---

### Post by crtbt on 2009-12-26
Thanks for the quick replies.  I'm just interested in playing records, so I don't have to worry about latency.

I'm trying to use JACK, since it sounds like it might be my best bet, but I don't really have any idea what I'm supposed to be doing.  Do I just set the input and output devices and start the JACK server, and then sound should start coming out of my speakers?  Or is there something else I need to do?  I'm using qjackctl, if that matters.

Here are the messages I get when I use the settings in the attached image below...

```
[COLOR=#999999]19:11:43.520 Startup script...[/COLOR] [COLOR=#990099]19:11:43.522 artsshell -q terminate[/COLOR]
 [COLOR=#cc9966]sh: artsshell: not found[/COLOR]
 [COLOR=#999999]19:11:43.925 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:11:43.927 JACK is starting...[/COLOR]
 [COLOR=#990099]19:11:43.928 /usr/bin/jackd -R -dalsa -r44100 -p1024 -n2 -D -Chw:1,0 -Phw:0,0 -Xseq[/COLOR]
 [COLOR=#999999]19:11:43.968 JACK was started with PID=5597.[/COLOR]
 [COLOR=#cc9966]no message buffer overruns[/COLOR]
 [COLOR=#cc9966]jackd 0.116.1[/COLOR]
 [COLOR=#cc9966]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#cc9966]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#cc9966]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#cc9966]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#cc9966]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#cc9966]loading driver ..[/COLOR]
 [COLOR=#cc9966]apparent rate = 44100[/COLOR]
 [COLOR=#cc9966]creating alsa driver ... hw:0,0|hw:1,0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#cc9966]control device hw:0[/COLOR]
 [COLOR=#cc9966]configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods[/COLOR]
 [COLOR=#cc9966]ALSA: final selected sample format for capture: 16bit little-endian[/COLOR]
 [COLOR=#cc9966]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#cc9966]ALSA: final selected sample format for playback: 16bit little-endian[/COLOR]
 [COLOR=#cc9966]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#66cc99]19:11:44.598 ALSA connection graph change.[/COLOR]
 [COLOR=#999933]19:11:46.015 Server configuration saved to "/home/alex/.jackdrc".[/COLOR]
 [COLOR=#999999]19:11:46.017 Statistics reset.[/COLOR]
 [COLOR=#999999]19:11:46.019 Client activated.[/COLOR]
 [COLOR=#9999cc]19:11:46.020 JACK connection change.[/COLOR]
 [COLOR=#cc9966]19:11:46.063 JACK connection graph change.[/COLOR]


[.....I click stop here.....]

[COLOR=#999999]19:12:45.110 Client deactivated.[/COLOR]
[COLOR=#999999]19:12:45.111 JACK is stopping...[/COLOR]
[COLOR=#cc9966]jack main caught signal 15[/COLOR]
[COLOR=#66cc99]19:12:45.231 ALSA connection graph change.[/COLOR]
[COLOR=#999999]19:12:45.232 JACK was stopped successfully.[/COLOR]
[COLOR=#999999]19:12:45.233 Post-shutdown script...[/COLOR]
[COLOR=#990099]19:12:45.233 killall jackd[/COLOR]
[COLOR=#cc9966]jackd: no process killed[/COLOR]
[COLOR=#999999]19:12:45.649 Post-shutdown script terminated with exit status=256.[/COLOR]
```
All that time there is no sound, of course.

hw:1,0 is "USB Audio" (the turntable) and hw:0,0 is "NVidia nForce2".

---

### Post by crtbt on 2009-12-27
OK, I got it! :D

All I had to do was click on "Connect" in qjackctl and connect "capture_1" to "playback_1" and "capture_2" to "playback_2".

---

