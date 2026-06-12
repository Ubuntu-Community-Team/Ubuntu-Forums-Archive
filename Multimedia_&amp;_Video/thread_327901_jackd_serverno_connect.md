---
title: "jackd server/no connect"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by deadgobby on 2006-12-29
Hi All,
 OK make a short story short. I reinstall ubuntu studio. The old fashion way is gone and just can installed using synaptic. Ok and bla bla bla. I know I installed Jackd. When I type in jackd in the terminal. I get this
jackd
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --verbose OR -v ]
             [ --silent OR -s ]
             [ --version OR -V ]
         -d driver [ ... driver args ... ]
             where driver can be `alsa', `coreaudio', `dummy',
                                 `oss' or `portaudio'

       jackd -d driver --help
             to display options for each driver
When I type in jackeq to check if it made a connection. I get
desktop:~$ jackeq
jackEQ 0.4.1
(c) 2003 - 2004 S. Harris, P. Shirkey
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.
Registering as jackEQ
jackEQ: Cannot contact JACK server, is it running?

OK now jackd has upgraded to a new version. 0.102.20.
And clue to get the server going. Uggg
Gobby

---

### Post by sproit on 2006-12-30
I never start jackd from the command line, I use jack control. But why don't you use it too? You've used Ubuntu studio before, you said.
Anyway, the command that jack control uses to start the daemon on my laptop:
**jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -S**

---

### Post by deadgobby on 2006-12-30
](*,) Duh!!!! 
OK now I am getting errors
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 32000
creating alsa driver ... hw:0|hw:0|1024|2|32000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 32000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
playback and capture sample rates do not match (48000 vs. 44100)
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.038 msecs
**** alsa_pcm: xrun of at least 0.021 msecs
**** alsa_pcm: xrun of at least 0.031 msecs
**** alsa_pcm: xrun of at least 0.029 msecs
**** alsa_pcm: xrun of at least 0.041 msecs
**** alsa_pcm: xrun of at least 0.024 msecs
09:35:44.144 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by 1002285 on 2006-12-30
> **sproit said:**
> I never start jackd from the command line, I use jack control. But why don't you use it too? You've used Ubuntu studio before, you said.
Anyway, the command that jack control uses to start the daemon on my laptop:
**jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -S**
I think I have a very similar problem. Jackd is not running and I don't know how to do it.
I don't have Ubuntu studio. But I want to try rosegarden and may-be others, if I don't like it.
Rosegarden says in settings "midi ok no audio", and in "details" that "jack server is not running".
How to get jack server running? Would the code you gave work for everybody? 
I installed jackd with synaptic.

---

### Post by deadgobby on 2006-12-30
Now I am thinking if the server is running at all now. I installed the newest version of jack via source. It went smooth at silk. Still no server. So I am going to hang for a day and see if there is any progress. OK I am going to eat and nap now.
Gobby

---

### Post by jakonj on 2007-01-01
see this page:
[http://lau.linuxaudio.org/jack/](http://lau.linuxaudio.org/jack/)

Use just this:
jackd -d alsa -d hw:0

:)

---

### Post by deadgobby on 2007-01-03
Well there we go. Thank you
GObby

---

### Post by sgx on 2007-01-04
Some kernels have midi timing that Rosegarden rejects, if the issue ever arises, fixes are on google...

---

### Post by gordwait on 2008-03-10
> **jakonj said:**
> see this page:
[http://lau.linuxaudio.org/jack/](http://lau.linuxaudio.org/jack/)

Use just this:
jackd -d alsa -d hw:0

:)

Here's what I get:

gordw@gromit:~$ jackd -d alsa -d hw:1
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:1|hw:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns

I've been hunting around, it seems to do with the fact that I have both on board audio and a USB audio device on the system at the same time, but I haven't found that magic bullet to fix it yet. 

I'm running Ubuntu 7.10, with the RT kernel installed. 
Help?

---

### Post by gordwait on 2008-03-10
Ah, I cut an pasted the wrong entry, but trying hw:0 gives me exactly the same result..

---

