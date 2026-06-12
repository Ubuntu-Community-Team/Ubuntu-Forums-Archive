---
title: "Trouble with Jack and friends"
date: 2007-12-07
forum: Multimedia Production
---

### Post by hanspb on 2007-12-07
Hi, I've searched for hours now without result. I have different kinds of trouble related to Jack and sound applications. I am running Gutsy with the rt kernel, and my sound card is ATI IXP AC97, this is on a laptop.
Now if I first start Jack Control and then use the "Start" button to run jackd, I get this :

```
23:46:11.131 Patchbay deactivated.
23:46:11.159 Statistics reset.
JACK tmpdir identified as [/dev/shm]
23:46:11.503 MIDI connection graph change.
23:46:11.508 MIDI connection change.
23:46:14.251 Startup script...
23:46:14.251 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Link points to "/tmp/ksocket-hpb"
23:46:14.894 Startup script terminated with exit status=256.
23:46:14.895 JACK is starting...
23:46:14.895 /usr/bin/jackd -R -p128 -dalsa -r48000 -p128 -n3 -D -Chw:0,0 -Phw:0,0 -i1 -o2
23:46:14.901 JACK was started with PID=5882 (0x16fa).
23:46:14.913 Could not connect to JACK server as client. Please check the messages window for more info.
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210410304, from thread -1210410304] (1: Operation not permitted)
cannot create engine
23:46:15.088 JACK was stopped successfully.
23:46:15.094 Post-shutdown script...
23:46:15.099 killall jackd
JACK tmpdir identified as [/dev/shm]
jackd: drepte ingen prosess
23:46:15.405 Post-shutdown script terminated with exit status=256.
```

This is if I have checked the "Realtime" option in "Setup". If not, the last bit is somewhat different:

```
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|128|3|48000|1|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: cannot set channel count to 1 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
23:55:20.745 JACK was stopped successfully.
23:55:20.749 Post-shutdown script...
23:55:20.752 killall jackd
jackd: drepte ingen prosess
23:55:20.997 Post-shutdown script terminated with exit status=256.
```

This is my first question: How can I get Jack started from Jack Control?


Then the next question: I can however start Jack with

```
jackd -d alsa
```

But then I don't get any sound in my sound applications like Rosegarden, Hydrogen and more. If I run them without Jack, There is sound and all is fine. So how can I get sound when I am running Jack?
:guitar:

---

### Post by Stochastic on 2007-12-08
what happens when you run jackd and get jack running, then open qjackctl?  it should say that jack is running and then allow you to connect rosegarden etc.. through the patchbay to your soundcard output etc...

This is a workaround but your problem looks to be that you've got bad settings in qjackctl.  I've got the same setup, including the same built-in soundcard so here are my qjackctl settings:
Realtime: yes
Everything else on the leftmost column: no
Priority: 0
Frames/Period: 1024
Sample Rate: 44100
Periods/Buffer: 3
Port Maximum: 512
Timeout: 500
Dither: None
Input & Output devices: hw:0
everything else either greyed out or 0

These may not be the best settings (I use a different card for recording & proper monitoring so I don't care), but they work for me.

---

### Post by hanspb on 2007-12-08
I tried your settings, but it did not help. I got the same complaint about realtime scheduling, and it also gives me a latency of 69.7 ms, which of course is not acceptable.

> what happens when you run jackd and get jack running, then open qjackctl? it should say that jack is running and then allow you to connect rosegarden etc.. through the patchbay to your soundcard output etc

Like I said, jack runs and I can connect Rosegarden and the others, but I get no sound at all. I only get sound if I don't use jack.

---

### Post by Stochastic on 2007-12-08
Yeah, those settings are not meant for recording obviously, but I figured it would help to get it setup and running.

What happens when you run ```
uname -r
```?
You can't get sound out even after making connections from Rosegarden to alsa output 1 and 2 inside qjackctl?  That's very strange.  Does this happen with all jack apps?

---

### Post by hanspb on 2007-12-09
uname -r:
2.6.22-14-rt.

It's the same with 2.6.22-14-generic. Rosegarden connects automatically to alsa_pcm in jack.
This happens with Rosegarden, Hydrogen and Noteedit, which are the ones I have tried. And without Jack, they all have sound.

---

### Post by Stochastic on 2007-12-09
can you get jack started from the command line with the -R (realtime) flag on?
can you try playing some audio out of ardour once jack is loaded?
What are your audio settings in Hydrogen?  What happens when you try to manually connect instead of having it auto-connect?
I'm having troubles getting rosegarden to play out jack myself now that I try it, but I'm no expert in Rosegarden.  Infact when I tried to play a midi file through my firewire soundcard with jack running on it, it came out of my onboard soundcard suggesting that Rosegarden is still trying to use alsa even though jack is running and qjackctl says rosegarden L+R are connected.  My guess is that Rosegarden relies on Timidity for midi playback so Timidity is the culprit on that one.  If that's the case I'd assume Noteedit issues would be tied to the same thing.

---

### Post by hanspb on 2007-12-10
Now a new week is beginning and I guess I won't have too much time to try things the next few days but I'll look into yor suggestions when I get some time. And you might be right in assuming something regarding Timidity, since I have that running for midi. Maybe Timidity and Jack is not a good combination?

---

### Post by Stochastic on 2007-12-10
I think that if you run ```
timidity -Oj -iA
``` it sets timidity up to use jack as an output device (and alsa sequencer as an input).
Not sure if you'll need to run this on a regular basis or not, probably altering a config file or two would fix your problem permanently (assuming timidity is the issue).

As for getting qjackctl running, if you're able to get jackd running from command line interface then qjackctl should be able to start it with the same settings.  It still puzzles me as to why you're not able to get realtime working on jack if you've got the realtime kernel.  I'd look into what the default settings for jackd are when you run "jackd -d alsa" and try to transfer those to qjackctl.  Then once it's working, you'll have time to play around with latency issues and tweaks.

---

### Post by hanspb on 2007-12-11
Hi again,
I can not run jackd with the -R option as a normal user, it gives me this:
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210041664, from thread -1210041664] (1: Operation not permitted)
cannot create engine
hpb@HPlaptop:~$
```
but it turned out I can do it as root (sudo jackd -R). That does not help much, though because then I guess I have to run everything else as root as well...

Now off to check your Timidity suggestions:)

Edit: No luck with changing Timidity options. Everything is jus the same. :(

And I tried to reproduce the default settings from "jackd -d alsa" in the Jack Control settings window. Then I actually was able to start jackd from there, although most of the time I get a message about Could not connect to Jack server as client". But Jack starts, and still there is no sound when JAck is running.

---

### Post by eric71 on 2007-12-11
In addition to running the realtime kernel, did you also create a group called "audio" and add your user to it? This is required for realtime access for a normal user.  That would explain why you can't start jackd in realtime mode except as root.

---

### Post by hanspb on 2007-12-11
Yes, there is an audio group: 

```
hpb@HPlaptop:~$ groups
hpb adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
hpb@HPlaptop:~$ 
```

I also believe that my user belongs to that group, otherwise I would never have any sound at all. Funny thing is, that in the System>Administration>Users and Groups dialog there is no audio group at all.

---

### Post by Stochastic on 2007-12-11
how did you go about getting the realtime kernel (ubuntustudio install or ubuntu install, meta packages or single kernel install)? does it have audio as its group of allowed users?

---

### Post by hanspb on 2007-12-11
Linux-image-rt from standard Ubuntu repos. Guess this is a meta package, the comment in Synaptic says it always depends on the latest kernel image.

> **Stochastic said:**
> does it have audio as its group of allowed users?

How do I find out?

---

### Post by Drunky on 2007-12-12
I'm certainly not an expert but I suspect you may also need to install linux-restricted-modules-rt.

When I installed upgraded from Ubuntu 7.10 to Ubuntu Studio 7.10 I used this [Ubuntu Help:UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") wiki page.

The code to accomplish this is:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

Notice this last item:  [linux-rt]("http://packages.ubuntu.com/gutsy/metapackages/linux-rt").    

This metapackage contains:  [linux-image-rt]("http://packages.ubuntu.com/gutsy/metapackages/ds_linux-image-rt.html") and [linux-restricted-modules-rt]("http://packages.ubuntu.com/gutsy/metapackages/linux-restricted-modules-rt").

I hope this helps.

---

### Post by hanspb on 2007-12-12
I have linux-restricted-modules-rt installed, so that is not the solution either. I suspect I'll have to give up this project soon. it's no big deal, really, it's just for fun that I try. So thank you, Stochastic, for all your efforts. but unless something really new happens I'll just have to live without midi in jack.:(

---

### Post by gordebak on 2007-12-16
hanspb, you can use midi with jack. You need two packages.

```
sudo apt-get install qjackctl qsynth
```

Qsynth is a frontend for fluidsynth. First run qjackctl, start jack, then run Qsynth, and click the Setup button. Load your soundfont and quit setup. Click restart. Then turn back to Qjackctl, click Connect -> Midi, and connect your midi device to FluidSynth. You're ready.

---

### Post by gordebak on 2007-12-16
BTW, both programs have system tray icon option.

---

### Post by hanspb on 2007-12-17
I don't think you read the thread properly. I have Jack installed, I also have Timidity. It still doesn't work.

---

### Post by surfdoc on 2007-12-19
Well noticed on root working! You need realtime-lsm (linux security module). It allows non root users to have access to the realtime controls. 

Unfortunately the set-up of this is a bit long winded; see:

[http://ubuntuforums.org/showthread.php?t=30388](http://ubuntuforums.org/showthread.php?t=30388)

I did get a FATAL on the module-assistant BUILD bit, but it still worked.

Only difference for me was that installing realtime-lsm allows you to run:

sudo /etc/init.d/realtime start

the config file /etc/defaults/realtime has the authorised GID as 29 which is "audio" on my system

Hope this helps

---

