---
title: "[SOLVED] JACK Error"
date: 2008-02-17
forum: Multimedia Production
---

### Post by Roanoke on 2008-02-17
Hi, when I start QJack ctl and start jack, I get the following error (from the messages window):

18:50:44.552 Patchbay deactivated.
18:50:44.787 Statistics reset.
18:50:45.011 MIDI connection graph change.
18:50:45.086 MIDI connection change.
18:50:48.896 Startup script...
18:50:48.897 artsshell -q terminate
18:50:49.803 Startup script terminated with exit status=256.
18:50:49.803 JACK is starting...
18:50:49.803 /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r48000 -p64 -n2 -S
18:50:49.933 JACK was started with PID=6381 (0x18ed).
18:50:49.938 JACK was stopped with exit status=1.
18:50:49.939 Post-shutdown script...
18:50:49.939 killall jackd
18:50:49.954 Could not connect to JACK server as client. Please check the messages window for more info.
18:50:53.501 Post-shutdown script terminated with exit status=256.

Help?

---

### Post by Roanoke on 2008-02-18
No one at all seems to know?

---

### Post by Stochastic on 2008-02-18
can you post a little more information?  what version of Ubuntu are you running?  what's your soundcard (onboard or pro)?  do you have the realtime kernel installed? etc...

---

### Post by Roanoke on 2008-02-18
As you can see above, I am running Ubuntu 7.10 with onboard SigmaTel audio, and am not sure weather I have the realtime kernel or not, am not sure how to check, but have a strange suspicion the answer is no.

---

### Post by Stochastic on 2008-02-18
To check for the realtime kernel open a terminal and do ```
uname -r
``` and if the number you get ends with -rt then you've got the realtime kernel.

If you don't have such a kernel then you should go into your settings section of qjackctl and uncheck the realtime option, save preferences, and try starting jack again.

---

### Post by Roanoke on 2008-02-18
I have the generic kernel.

---

### Post by Stochastic on 2008-02-18
try unchecking the realtime option in jack's settings and post the result

oh and while you're there, change your frames/period setting to be a bit bigger than 64 as this probably isn't achievable with an onboard soundcard

---

### Post by Roanoke on 2008-02-18
Frames/Period set to 128.

19:30:45.946 Patchbay deactivated.
19:30:46.127 Statistics reset.
19:30:46.179 MIDI connection graph change.
19:30:46.382 MIDI connection change.
19:30:47.406 Startup script...
19:30:47.407 artsshell -q terminate
19:30:47.689 Startup script terminated with exit status=256.
19:30:47.689 JACK is starting...
19:30:47.689 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r48000 -p128 -n2 -S
19:30:47.696 JACK was started with PID=7444 (0x1d14).
19:30:47.873 Could not connect to JACK server as client. Please check the messages window for more info.
19:30:48.100 JACK was stopped successfully.
19:30:48.100 Post-shutdown script...
19:30:48.100 killall jackd
19:30:48.317 Post-shutdown script terminated with exit status=256.

---

### Post by Stochastic on 2008-02-18
try to set your frames/period to 1024 just to get things working, then if you don't get any xruns you can restart with a lower setting

Oh and to help the troubleshooting process check the box to turn on Verbose mode in the settings panel.

---

### Post by Roanoke on 2008-02-18
Done and done.

19:39:01.069 Patchbay deactivated.
19:39:01.247 Statistics reset.
19:39:01.403 MIDI connection graph change.
19:39:01.500 MIDI connection change.
19:39:37.254 Startup script...
19:39:37.255 artsshell -q terminate
19:39:38.527 Startup script terminated with exit status=256.
19:39:38.527 JACK is starting...
19:39:38.527 /usr/bin/jackd -v -p128 -t5000 -dalsa -dhw:0 -r48000 -p1024 -n2 -S
19:39:38.530 JACK was started with PID=7746 (0x1e42).
19:39:38.539 Could not connect to JACK server as client. Please check the messages window for more info.
19:39:38.728 JACK was stopped successfully.
19:39:38.728 Post-shutdown script...
19:39:38.728 killall jackd
19:39:38.958 Post-shutdown script terminated with exit status=256.

---

### Post by Stochastic on 2008-02-18
well now you need to give me more info, can you post all the settings in the setup window (maybe a screenshot)?  and can you check that no other audio apps are running (including say youtube pages etc...)

---

### Post by nlz on 2008-02-19
OK, why don't you just install qjackctl, go to setup and play around with frames/period, sample rate and periods/buffer. When you got this done, you can start thinking about realtime.

if you google on jack setup you can also find a lot.

---

### Post by Roanoke on 2008-02-19
Wow, when I tried without apps running, it worked. But I get Xrun callbacks. Attached are my settings.

---

### Post by Stochastic on 2008-02-19
try unchecking the 'force 16-bit' box as this is an unusual setting.

also, the port-maximum is fairly low (from what I know), you may want to increase that to 256 or 512.

Good to hear you have it working (somewhat).  To get rid of the xruns (if they persist after the above adjustments) you could change your frames/buffer setting to a slightly higher number.  The downside of doing this is that you'll increase your latency, but depending on your application that isn't always a bad thing.

---

### Post by Roanoke on 2008-02-19
I found that changing it to 3 gave me no xruns, while keeping a latency of 64 msec.

---

### Post by nlz on 2008-02-20
64 msecs is way too much! you can do much better than that! It's no use running low latency software with so much latency ;)

try putting you frames/period down. below 10 msec is possible for most people, if you choose to install the realtime kernel (which is so much nicer then the generic kernel anyway (sooooooo fast that a generic dekstop feels like being stuck in the mudd)

---

### Post by Roanoke on 2008-02-20
Well, my lowest is two, at which I get xruns, and is more than 10. My laptop isn't exactly new. And about the realtime kernel,

a.) How do I install it?
b.) When I do install it, will it require a new partition or replace my generic one?
c.) If so, will all my files/folders still exist?

---

### Post by Roanoke on 2008-02-20
Strange thing happened, errors anew.

17:01:33.846 Patchbay deactivated.
17:01:33.927 Statistics reset.
17:01:33.956 Startup script...
17:01:33.956 artsshell -q terminate
17:01:33.997 MIDI connection graph change.
17:01:34.675 Startup script terminated with exit status=256.
17:01:34.675 JACK is starting...
17:01:34.675 /usr/bin/jackd -v -p512 -t5000 -dalsa -dhw:0 -r48000 -p1024 -n3
17:01:34.678 JACK was started with PID=5911 (0x1717).
17:01:34.887 Could not connect to JACK server as client. Please check the messages window for more info.
17:01:35.034 JACK was stopped successfully.
17:01:35.036 Post-shutdown script...
17:01:35.036 killall jackd
17:01:35.253 Post-shutdown script terminated with exit status=256.
17:01:37.581 MIDI connection change.

How come?

---

### Post by kayosiii on 2008-02-20
ok I am guessing that your soundcard does not support hardware mixing. This means another application can grab the soundcard and not let jack run.
Life is so much easier on linux with audio when you have a soundcard that supports hardware mixing (though pulseaudio will reportedly make things easier)...

As for the latency settings, how much latency you can live with will depend on what you are doing. Less latency is good but living with a slight delay is better than living with xruns.

The realtime kernel should be in the ubuntu repositories - It is installed by default with ubuntu studio. You can get realtime working with a non realtime kernel (not quite as smooth too). 

You will need to edit /etc/security/limits.conf and add something similar to the following

@audio - rtprio 99
@audio - memlock 512000
to the end of the file
which will allow audio apps to run at a much higher priority than they other wise would.

then you should tick the box in jack control (qjackctl) that says realtime

---

### Post by Roanoke on 2008-02-20
Well I often run other sound apps and connect them with jack like seq24 and hydrogen, and I started jack with no other apps running.

---

### Post by nlz on 2008-02-21
you can either:

> **nlz said:**
> 

1. Install realtime LSM from synaptic package manager, after that you can build a new kernel as described in usr/share/doc/realtime-lsm

2. Try to fix things with rlimits 

3. Install Ubuntu studio and upgrade to the realtime kernel (if you haven't done if before you upgraded it)

I tried the first two, but they didn't really worked out for me, probably because i wanted a quick succes. Installing Ubuntu studio just preconfigures everything for you. 

Go Go Jack-Ranger.

or just install it with the -rt packages in synaptic. don't now if you have to edit rlimits to be able to acces rt with jack without being logged in as root...

---

