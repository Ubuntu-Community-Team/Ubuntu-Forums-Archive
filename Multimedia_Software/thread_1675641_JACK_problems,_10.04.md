---
title: "JACK problems, 10.04"
date: 2011-01-25
forum: Multimedia Software
---

### Post by SuperDupes on 2011-01-25
Hi,

I am sort of new to this, but I'm trying!

I am currently running 10.04 on my semi-old desktop and on my netbook.
Just bought the Yamaha audiogram6 to do some home recording.  So far, it's going decently on my netbook, but jack isn't working for me on my desktop.

In Ardour, i just get feedback noise if I try to run it with realtime unchecked.  When I try to run realtime in JACK I get: either a frozen JACK or, error messages.  What does realtime do exactly anyways?  Is that what's causing my ardour noise?

I already added myself to the audio group, edited the limits.conf and limits.d/audio.conf files and I am still crashing and burning.

O kind ubuntu community!  please help me!

I sometimes can see the messages with jack, but othertimes it just crashes after the hw:1 line.  I can post the message if it ever decides to tell me again.

Thanks!!!

---

### Post by SuperDupes on 2011-01-25
p, li { white-space: pre-wrap; }  [COLOR=#999999]21:34:38.558 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:34:40.117 Statistics reset.[/COLOR]
 [COLOR=#999999]21:34:40.186 JACK is starting...[/COLOR]
 [COLOR=#990099]21:34:40.187 /usr/bin/jackd -p128 -dalsa -dhw:1 -r48000 -p64 -n2 -Xraw[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]21:34:40.208 JACK was started with PID=6103.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... hw:1|hw:1|64|2|48000|0|0|nomon|swmeter|-|32bit
 control device hw:1
 [COLOR=#999999]21:34:51.592 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]21:34:51.686 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:34:51.687 killall jackd[/COLOR]
 [COLOR=#cc3366]21:34:51.688 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]21:34:52.325 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]21:34:54.273 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info[/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#ff0000][COLOR=Black]not much to work on...at least with my level of knowledge[/COLOR]
[/COLOR]

---

### Post by SuperDupes on 2011-01-30
Could it have to do with the sound card in my computer?

---

### Post by cchhrriiss121212 on 2011-01-30
Could you post the result of this from a terminal window:
aplay -l

---

### Post by SuperDupes on 2011-02-04
aplay -l gives:

card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Card 1 is my audiogram.  Its still working on my laptop as USB Audio Codec, but my desktop....



By the way, LOVE the Bootsy.

---

### Post by cchhrriiss121212 on 2011-02-04
Can you verify that you are using the exact same jack settings on the desktop and the netbook?
Does jack work with the on board desktop card, hw:0?
Can you use the USB device with any other software on the desktop? Audacity for example.

---

### Post by SuperDupes on 2011-02-07
I will test that stuff out. later today.

I don't know how to test if the hw:0 will work on my desktop.  I don't have a mic that works in the mic jack (I think my motherboard is getting too old), so even if JACK starts up (with no xruns hopefully) I don't know how to see if it can record anything....

Other than that, Audacity is a good idea.  I'll let you know.

---

### Post by cchhrriiss121212 on 2011-02-09
> I don't know how to test if the hw:0 will work on my desktop.  I don't  have a mic that works in the mic jack (I think my motherboard is getting  too old), so even if JACK starts up (with no xruns hopefully) I don't  know how to see if it can record anything....
You can test it out with Hydrogen or something else that makes noise, just hook it up to ardour/qtractor or timemachine. All I really need to know is whether jack starts or not.

---

