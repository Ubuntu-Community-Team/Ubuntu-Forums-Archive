---
title: "Pulling my hair out - Could not connect to jack server - pleaaase help"
date: 2007-11-05
forum: Multimedia Production
---

### Post by Mr.Johnny on 2007-11-05
Hi! 

I've been trying for days to setup jack but without success. I've searched the internet and lots of similar threads here and found no solution at all and don't know what else to do...

- rt kernel 2.6.16
- alsa 1.0.15
- jack 0.103
- qjackctl 3.1a
- jack/qjackctk/alsa compiled and installed with no errors.
- done this (cured the fifo error message):
[http://ubuntuforums.org/showthread.php?t=453486](http://ubuntuforums.org/showthread.php?t=453486)
- I've checked for any running processes.
- I've tried as root also.

I always get this message "Could not connect to jack server". Why? What? How? :(

---

### Post by Mr.Johnny on 2007-11-06
bump :(

---

### Post by deadgobby on 2007-11-06
Are you using Ubie Studio? And yet, what version of it. I got a really bad taste with Ubie studio and for music programming. I have a dual boot of Studio 64. 
 [http://64studio.com/](http://64studio.com/) and regular Ubie
 I do not want to say at least that Ubie Studio is not good. It can use some work compare to Studio 64. Try the live CD of S64 and make your own choice. 
Gobby

---

### Post by Mr.Johnny on 2007-11-06
No, it's the normal ubuntu... I tried UbStudio, but I had more problems, since it already comes with jack and qjackctl installed. When I tried to install the newer versions, it launched the older ones or didn't recognize the newer ones (once the older was removed). I was interested in the midi support of the latest jack release.

I updated the alsa drivers, could it have to do with that (shouldn't they be compiled with the kernel or something like that?).

Also, I noticed I have no readable/writable audio clients (midi, yes) in qjackctl, but the alsa driver is recognized, and so are the cards in ubuntu.

I also tried 7.10, but the rt kernel (2.6.22) crashes my machine, and that is well beyond my little knowledge.

didn't know 64studio... I'll try it later, thanks.

---

### Post by Stochastic on 2007-11-06
In general if you're using software from outside the repos, you shouldn't be asking for troubleshooting tips on these forums (try the mailing lists for the respective software).  But that's just my opinion - I'm not a forum moderator.
A couple places to start your troubleshooting:
What message do you get when you start jack from the command line?
What settings do you have jack set to?
What soundcard are you using?

---

### Post by Drunky on 2007-11-06
> **Mr.Johnny said:**
> Hi! 

I've been trying for days to setup jack but without success. I've searched the internet and lots of similar threads here and found no solution at all and don't know what else to do...

- rt kernel 2.6.16
- alsa 1.0.15
- jack 0.103
- qjackctl 3.1a
- jack/qjackctk/alsa compiled and installed with no errors.
- done this (cured the fifo error message):
[http://ubuntuforums.org/showthread.php?t=453486](http://ubuntuforums.org/showthread.php?t=453486)
- I've checked for any running processes.
- I've tried as root also.

I always get this message "Could not connect to jack server". Why? What? How? :(

Have you tried to adjusting the settings using qjackctl before starting Jack?

I also had trouble running Jack (I got the same error message) until I used this [Configure Jack Tutorial]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") to adjust my settings.

These settings are a good place to start but you still may need to adjust them to match your computer.

Good luck.

---

### Post by Mr.Johnny on 2007-11-06
If it's wrong posting about unsupported versions, I am sorry, I won't post again (just let me know).

I have 2 cards, an audigy and a 1212m.

The settings I am using are the same I was using with ubuntu studio (jack 0.102, alsa 1.0.14, qjackctl 2.something). It worked that way (with the audigy, that is).

*but* I can't use my other card (e-mu 1212m) with any version of alsa below 1.0.15.

I have followed that tutorial, but right now the only error message I get is "Could not connect to jack server as a client". starting jack thru the command line doesn't work too (no timeout is specified, so it keeps trying to connect).

I noticed I have no readable/writable audio clients in qjackctl, could it be related?

---

### Post by Stochastic on 2007-11-06
> **Mr.Johnny said:**
> If it's wrong posting about unsupported versions, I am sorry, I won't post again (just let me know).


It's not wrong, it just might not be that helpful as other channels (as I'm sure you're finding out).


If I were you, I'd forget about working with qjackctl until you can get jack working with the command line.  That'll give you more info in the trouble shooting process and it knocks one possible issue out of the way.

---

### Post by Mr.Johnny on 2007-11-06
But I know how to work with jack using the command line. 

If I do jackd -R -dalsa only, it keeps trying to connect forever. 

If I set the timeout, i'll get the "could not connect..." message. :(

---

### Post by Stochastic on 2007-11-06
what's the full message beyond 'could not connect'?

---

### Post by Mr.Johnny on 2007-11-06
it says:

"Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info."

(er, that's the message window.)

---

### Post by Mr.Johnny on 2007-11-06
I uninstalled jack 0,103 and qjackctl 3.1a and installed jack 0,102 and qjackctl 0.2.21 and now it works.

It seems that the older versions of each can't find the new ones and vice-versa. .. :(

---

### Post by Stochastic on 2007-11-06
> **Mr.Johnny said:**
> it says:

"Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info."

(er, that's the message window.)

I mean what does the FULL command line jack error read when timeout is activated?  Furthermore, you should put verbose mode on if you're planning on troubleshooting anything (qjackctl has this too if you still insist on using that extra layer).  If you can't give me a proper error message I'd highly advise you to stick with what's in the repos.  I don't mean to be rude, but there's a reason why repos don't carry the latest and greatest - it hasn't been tested yet.  If you need a package that's not in the repos yet, don't expect it to work out of the box, plan to be able to lift the hood and start tweaking.  This involves debugging, finding errors,  maybe even fixing code and filing proper bug reports.

For a little more insight try running ```
jackd --help
```

---

### Post by Mr.Johnny on 2007-11-07
I don't think you're being rude, and my point is not upseting anyone. But I must say, not to be rude too, if I wanted a ready-to-go setup i'd be using windows.

I just thought that maybe someone more experienced than me could quickly diagnose a problem that would take hours of hair-pulling for me. 

Personally I don't think there's nothing wrong with that, avoiding to learn it the hard way,  but opinions are different, of course.

Now, it's not my goal to make this thread a win vs. linux or average joe vs. computer genious matter, so let's leave that aside.

I am just an amateur musician that wants to learn how to setup up jack/wine/wineasio to run a few vst's under linux  to play around. (The later two I have managed to setup properly by myself, so I won't be bothering anyone regarding that).

I'll post a more detailed output with "verbose messages on" when I'm in that computer. If no solution can be found, I'll simply leave it aside and come back to it a few months later.

Thanks for the tips so far. ;)

---

### Post by Mr.Johnny on 2007-11-08
Ok, here it is (i was mistaken, it seems jack 0.103 runs in the command line, but wine+wineasio don't "see it"): 

########jack 0.103 (command prompt)##############

johnny@johnny-desktop:~$ jackd -v -R -p512 -t1000 -dalsa -dhw:0 -r48000 -p1024 -n2 -m -i2 -o
getting driver descriptor from /usr/local/lib/jack/jack_oss.so
getting driver descriptor from /usr/local/lib/jack/jack_alsa.so
getting driver descriptor from /usr/local/lib/jack/jack_dummy.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|2|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
7328 waiting for signals
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x8059568 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:monitor_1, offset = 12288
registered port alsa_pcm:playback_2, offset = 0
registered port alsa_pcm:monitor_2, offset = 16384
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
load = 0.0117 max usecs: 5.000, spare = 21328.000
load = 0.0223 max usecs: 7.000, spare = 21326.000
load = 0.0205 max usecs: 4.000, spare = 21329.000
load = 0.0220 max usecs: 5.000, spare = 21328.000
load = 0.0297 max usecs: 8.000, spare = 21325.000
load = 0.0242 max usecs: 4.000, spare = 21329.000
load = 0.0285 max usecs: 7.000, spare = 21326.000
(...)

################################




###jack 0.103 started with qjackctl 0.3.1.a######

15:00:41.283 /usr/local/bin/jackd -v -R -p512 -t1000 -dalsa -dhw:0 -r48000 -p1024 -n2 -m -i2 -o2
getting driver descriptor from /usr/local/lib/jack/jack_oss.so
getting driver descriptor from /usr/local/lib/jack/jack_alsa.so
getting driver descriptor from /usr/local/lib/jack/jack_dummy.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
15:00:41.293 JACK was started with PID=6934.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|2|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
6934 waiting for signals
15:00:41.500 ALSA connection change.
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x8059568 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:monitor_1, offset = 12288
registered port alsa_pcm:playback_2, offset = 0
registered port alsa_pcm:monitor_2, offset = 16384
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
load = 0.0188 max usecs: 8.000, spare = 21325.000
15:00:43.509 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
load = 0.0281 max usecs: 8.000, spare = 21325.000
load = 0.0281 max usecs: 6.000, spare = 21327.000
load = 0.0258 max usecs: 5.000, spare = 21328.000
load = 0.0199 max usecs: 3.000, spare = 21330.000
load = 0.0287 max usecs: 8.000, spare = 21325.000
load = 0.0354 max usecs: 9.000, spare = 21324.000
load = 0.0365 max usecs: 8.000, spare = 21325.000
load = 0.0370 max usecs: 8.000, spare = 21325.000
load = 0.0372 max usecs: 8.000, spare = 21325.000
load = 0.0374 max usecs: 8.000, spare = 21325.000
(...)

###################################


###jack 0.102 started with qjackctl 0.2.2.1#########

14:57:21.716 /usr/bin/jackd -v -R -dalsa -dhw:1 -r48000 -p1024 -n2 -m -i2 -o2
14:57:21.755 JACK was started with PID=5553 (0x15b1).
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|1024|2|48000|2|2|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
5553 waiting for signals
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
required capabilities not available
capabilities: =
new client: alsa_pcm, id = 1 type 1 @ 0x805af28 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:monitor_1, offset = 12288
registered port alsa_pcm:playback_2, offset = 0
registered port alsa_pcm:monitor_2, offset = 16384
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
load = 0.0141 max usecs: 6.000, spare = 21327.000
14:57:23.769 Server configuration saved to "/home/johnny/.jackdrc".
14:57:23.771 Statistics reset.
14:57:23.890 Client activated.
14:57:23.891 Audio connection change.
14:57:23.907 Audio connection graph change.
new client: qjackctl-5545, id = 2 type 2 @ 0xb7f81000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-5545: start_fd=5, execution_order=0.
client qjackctl-5545: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
load = 0.0727 max usecs: 28.000, spare = 21305.000
load = 0.1043 max usecs: 29.000, spare = 21304.000
load = 0.1107 max usecs: 25.000, spare = 21308.000
load = 0.1233 max usecs: 29.000, spare = 21304.000
load = 0.1273 max usecs: 28.000, spare = 21305.000
load = 0.1293 max usecs: 28.000, spare = 21305.000
load = 0.1326 max usecs: 29.000, spare = 21304.000
load = 0.1366 max usecs: 30.000, spare = 21303.000
load = 0.1199 max usecs: 22.000, spare = 21311.000
load = 0.1185 max usecs: 25.000, spare = 21308.000
load = 0.1249 max usecs: 28.000, spare = 21305.000
load = 0.1164 max usecs: 23.000, spare = 21310.000
load = 0.1097 max usecs: 22.000, spare = 21311.000
load = 0.1205 max usecs: 28.000, spare = 21305.000
load = 0.1071 max usecs: 20.000, spare = 21313.000
load = 0.1004 max usecs: 20.000, spare = 21313.000
load = 0.0971 max usecs: 20.000, spare = 21313.000
load = 0.1118 max usecs: 27.000, spare = 21306.000
load = 0.1051 max usecs: 21.000, spare = 21312.000
load = 0.1158 max usecs: 27.000, spare = 21306.000
load = 0.1259 max usecs: 29.000, spare = 21304.000
(...)

###################################

---

