---
title: "newbie install JACK connection problems"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by playersgc on 2006-07-30
I just finished following the instructions for Dapper Studio Preparation from the wiki, and I can't get JACK to work properly.  Maybe I missed something?  I searched in the forums, but couldn't find a similar issue.  Here's the message I get:
> 22:43:59.033 Patchbay deactivated.
22:43:59.217 Statistics reset.
22:43:59.385 MIDI connection graph change.
22:43:59.452 MIDI connection change.
22:47:08.597 Startup script...
22:47:08.597 artsshell -q terminate
sh: artsshell: command not found
22:47:08.923 Startup script terminated with exit status=32512.
22:47:08.944 JACK is starting...
22:47:08.945 /usr/bin/jackd -R -t5000 -dalsa -r48000 -p64 -n2 -D -Chw:0,2 -Phw:0,3 -S
22:47:08.972 JACK was started with PID=11228 (0x2bdc).
22:47:08.992 Could not connect to JACK server as client. Please check the messages window for more info.
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,3|hw:0,2|64|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
22:47:12.170 JACK was stopped successfully.

Any suggestions would be greatly appreciated!
SgC

---

### Post by goodmanbrown on 2006-07-31
I don't understand any of this audio stuff yet, but since no one with more expertise is piping up, I can at least report my own experience...

Every time I get this error from Jack it is because some other program has its finger on the sound card.  Most of the time, I forget that I left timidity++ running in server mode.  But some of the time, even Amarok seems to interfere.  If I shut down every conceivable audio application, that error always goes away and Jack starts fine.

---

### Post by dolson on 2006-07-31
Have you been trying other values for the buffers/period? Instead of 64, try 128, and so on. Not all hardware was created equally. Also, you did not specify what your hardware is.

---

### Post by playersgc on 2006-07-31
So this looks like a hardware problem for sure?
I thought the "cannot load driver module alsa" part looked like I hadn't installed it properly.

I am on a Compaq Evo N115, with a SoundMAX Integrated Digital Audio card (by Analog Devices, Inc), driver version 5.12.1.3039.  I've been looking, but I can't find any more specific information about this sound card, like appropriate Periods/Buffer settings.  There are so many variables, surely I'm not expected to figure them out by trial and error?!

Especially cryptic to me are the Input Device and Output Device parameters in the Setup for JACK Audio Connection Kit.  What do I choose?  I entered the values just like in the wiki:
Input Device: hw:0,2
Output Device: hw:0,3

I have no idea what those mean, so that could be the problem.  Did I miss an FAQ somewhere?  If these questions are redundant, I apologize.  Please let me know, so I can refrain from wasting anyone's time.

Thanks again!

---

### Post by dolson on 2006-08-01
That depends.. Try using the defaults. As I put on the wiki page, that is only for my sound card. Nobody else has put in values for their hardware, but it would be nice to collect this kind of info. Even better would be if JACK would handle it all on its own...

Periods and Buffers should be as low as you can get them, because if you look at it when you change it, it increases the latency if you increase them. Basically, get the lowest set that works.

Your soundcard is familiar to me, and I don't think they work too well for stuff like this... I might be wrong though, but I did have a card like this at work before and it was a bit problematic for me with normal audio, nevermind JACK stuff..

I assume this is a laptop system, so you don't have a real option to upgrade, correct?

---

### Post by playersgc on 2006-08-01
Yes, the only thing I could upgrade was RAM, and I did that.  It has 386MB.  I've never had any problems making normal audio work on it, tho.

I just realized that I downloaded the "StudioToGo!" demo a while back, and I think most of that was working.  I'll load it up again and see if I can get some information from that.

---

### Post by playersgc on 2006-08-01
AHA!
I tried a few things and got results!  Now JACK can start, but when I ran amSynth, the JACK Audio Connection Kit messages window filled up with lines like this over and over:
> 
delay of 21343.000 usecs exceeds estimated spare time of 21075.000; restart...
delay of 21360.000 usecs exceeds estimated spare time of 21075.000; restart...

The delays are just barely exceeding the "estimated spare time", whatever they are.

Any suggestions?

---

