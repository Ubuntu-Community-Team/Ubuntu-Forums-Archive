---
title: "M-Audio Audiophile USB problems..."
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by danielfretto on 2006-09-24
Audiophile USB works great with Quod and other media players as well as with system sounds and has since the moment i installed Dapper.

After following all the steps on Ubuntu Studio site I'm not getting signal to or from Audiophile.  PCs keyboard input triggers software synths as the meter lights show.  

Seems as though Audiophile is seen by Jack in device dropdowns.

Can only start Jack with Dummy driver...no other works.  Here's the errors:

21:42:09.417 Startup script...
21:42:09.419 artsshell -q terminate
can't create mcop directory
Creating link /home/d/.kde/socket-shedd.
21:42:09.737 Startup script terminated with exit status=256.
21:42:09.739 JACK is starting...
21:42:09.741 /usr/bin/jackd -R -dalsa -r44100 -p64 -n2 -D -Chw:1 -Phw:1 -S
21:42:09.755 JACK was started with PID=9993 (0x2709).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|64|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:1
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
Note: audio device hw:1 doesn't support a 16bit sample format so JACK will try a 24bit format instead
Note: audio device hw:1 doesn't support a 24bit sample format so JACK will try a 32bit format instead
Sorry. The audio interface "hw:1" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
21:42:09.872 Could not connect to JACK server as client. Please check the messages window for more info.
could not attach as JACK client (server has exited)
21:42:10.020 JACK was stopped successfully.

I've scoured the forums all night with no luck.

Any ideas?

---

### Post by CapnWhizBang on 2006-10-10
I am in the exact same situation. Any help out there?

Thanks

---

### Post by hendrikwout on 2006-10-25
I've had the same problem with my usb audio interface and just solved it:

try the command: jackd -d oss -C /dev/dsp -P /dev/dsp

with realtime-lsm-module: jackd --realtime -d oss -C /dev/dsp -P /dev/dsp

So I used the oss-driver instead of alsa-driver. I can get to very low latency (see jackd --help)
Note you might replace /dev/dsp with /dev/dsp1 if you want to use your second audio card. 

I hope this helps also for you

---

### Post by CapnWhizBang on 2006-10-27
Thanks very much for your idea.
It has gotten me half way there.

I can now get sound to come out of the Audiophile USB.
However, I cannot sample anything.

I have used this command in terminal:
jackd --realtime -d oss -r 44100 -C /dev/dsp1 -P /dev/dsp1

and I can play a track in ardour and it comes out the audiophile. Great!
But it won't record anything. :( 

if I start jackd using a qjackctl configuration for oss I get:
22:15:02.787 Startup script...
22:15:02.790 artsshell -q terminate
22:15:03.138 Startup script terminated with exit status=256.
22:15:03.142 JACK is starting...
22:15:03.145 jackd -R -t5000 -doss -r44100 -p64 -n2 -w16 -C/dev/dsp1 -P/dev/dsp1
22:15:03.181 JACK was started with PID=11034 (0x2b1a).
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
oss_driver: /dev/dsp1 : 0x10/2/44100 (256)
22:15:03.483 Server configuration saved to "/home/kschmitt/.jackdrc".
22:15:03.487 Statistics reset.
22:15:03.538 Client activated.
22:15:03.580 Audio connection change.
22:15:03.599 Audio connection graph change.
oss_driver: indevbuf 256 B, outdevbuf 256 B
oss_driver: using barrier mode, (dual thread)
22:15:20.728 XRUN callback (1).
delay of 1906.000 usecs exceeds estimated spare time of 1394.000; restart ...
delay of 9618.000 usecs exceeds estimated spare time of 1394.000; restart ...
22:15:21.906 XRUN callback (1 skipped).
22:15:45.835 XRUN callback (3).
delay of 3972.000 usecs exceeds estimated spare time of 1396.000; restart ...
delay of 9508.000 usecs exceeds estimated spare time of 1396.000; restart ...
22:15:46.360 XRUN callback (1 skipped).
22:15:47.862 XRUN callback (5).
delay of 1494.000 usecs exceeds estimated spare time of 1389.000; restart ...

I can play a file in ardour but still no input.

I am guessing that these "delay" messages indicate some problem.
Hopefully someone can help me figure it out.

---

### Post by CapnWhizBang on 2006-10-28
Just to make sure there wasn't something going on with OSS and sampling, I ran 
jackd --realtime -d oss -r 44100 -C /dev/dsp -P /dev/dsp
I am able to get a signal to ardour from the on board intel chip. (mono though)
I am considering opening up my laptop and trying to replace the mic input jack with a stereo input jack and trying to re-wire it to create a "line-in". My last Toshiba laptop had a line in. I can't imagine why they left it off of this model (A10 S177)

---

### Post by JonasLJ on 2007-12-30
Hi,

I'm currently struggling with ardour2 and Audiophile USB. I got playback working (also throug alsa), but I have no clue how to get recording working.

I've tried to set the Inpu Device to be the Audiophile in Jack-control, but i doesn't seem to work. And I cannot find a place in Ardour to select what channel to use. Any ideas?

---

### Post by CapnWhizBang on 2007-12-30
I ended up returning the Audiophile and getting a Tascam US-144 which I got working somehow or other. Then my 8 channel mixer bit the dust and I opted to replace it with a Presonus Firepod so I could record 8 tracks at a time but which I couldn't get to work in Ubuntu. When the Vista drivers for the Firepod came out and it worked flawlessly I removed the Ubuntu partition. I have gone to the dark side. Good Luck.

---

### Post by Aurora on 2007-12-30
You mean you went back to Windows just because it works way better?  You're not willing to spend  dozens of hours trying to get your hardware to work with Ubuntu, simply because it works out of the box with The Evil OS? How could you be so fickle?

<sigh> Such is the Open Source world.  If you're not committed to it for some moral or philosophical reason, it's hard to justify the time spent.  If you just want it to work,  and you have the money to spend, I really can't think of a practical reason why you would use Linux for audio production. Come back in a couple years after us stubborn zealots have worked on it awhile.

If you're a stubborn zealot, try helping out in this thread:

[http://ubuntuforums.org/showthread.php?t=148467&page=5](http://ubuntuforums.org/showthread.php?t=148467&page=5)

I've been in USB Audio hell for a long time...

Paul in Seattle

---

