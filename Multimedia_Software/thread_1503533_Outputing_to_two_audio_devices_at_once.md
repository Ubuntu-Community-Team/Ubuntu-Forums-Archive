---
title: "Outputing to two audio devices at once"
date: 2010-06-06
forum: Multimedia Software
---

### Post by WindriderMetal on 2010-06-06
Hello,

My band play with a backing track running out of my laptop. We have a stereo mix of the backing track running into the PA system, plus another stereo mix of the backing track with a metronome running into headphones worn by our drummer. This means that the laptop is outputting 4 audio channels simultaneously. The catch is, i only have a two channel USB audio device, in addition to the two channel built-in soundcard.
The trick i found to accomplishing what i desire within Windows was relatively simple - i used the ASIO4ALL driver, which effectively allowed me to combine the outputs into one "virtual" ASIO audio device which has 4 output channels, which i could then send audio to using my digital audio workstation software (REAPER).
Luckily this has worked perfectly every time we've done it on stage, however at rehearsals it has on occasion failed as Windows has encountered errors, etc. Naturally it would be devastating for this to happen on stage, and so i've decided to try Linux out, as it has the reputation of being extremely stable (i've heard stories about machines being switched on for years without crashing).

Now, i've tried for a couple of days to get this to work, messing around with JACK, ALSA, and PortAudio, and using a range of programs such as Qtractor, Ardour, and MusE; however, i've only ever been able to get stereo audio to come out of one device at a time. I do however know that it is possible to do what i want, because i found a little DJ application which allowed me to set a different audio device to be in "headphones", whilst my other audio device outputs the currently playing track.

I'm by no means a proficient Linux user, however if something has to be done through a Terminal, with adequate instructions i'm sure i could do it. What i'm after though really, is a simple and clear guide to accomplishing what i want, which to recap is:

A to simultaneously output audio to two separate audio devices at once from within the same program.

Thank you very much to anyone who can help me solve this.

Elliot

---

### Post by Breambutt on 2010-06-07
Well, here's one way of doing it. At first I tried it with Audacity but it pooped out some PortAudio excrement I'm not familiar with, and since I'm improvising as I go along I decided to try our beloved and trustworthy Ardour. There's probably a bunch of workarounds to achieve the same goal, and if anyone has a more trivial ways of achieving this, feel free to educate us all.

I'm also horrible at explaining these things with words and rarely run jackd from the terminal, so here's a somewhat self-explanatory picture: [http://www.nbl.fi/dr.shoe/images/alsa_out.png](http://www.nbl.fi/dr.shoe/images/alsa_out.png)

Basically I created another device called MobilePerse (USB preamp) for JACK with alsa_out and connect the individual tracks to different sound interfaces. The "click/out" is Ardour's built-in metronome which you can assign to any number of outputs as well. *alsa_out -h* displays all the parameters you can run the second device with.

Call me crazy but I think alsa_out and alsa_in came with the default Ubuntu Studio 10.04 installation, so don't kick me in the nads if you don't have them. I think they were part of the netjack package at some point in ancient history if sold separately. Also, go easy on the latency settings since this kind of operation doesn't depend on it - should be guaranteed stability that way.

Hope this works for you, had to revise my moronic advice a dozen times. Almost let out a desperate chuckle at some point.

---

### Post by WindriderMetal on 2010-06-07
That sounds perfect to me, however i'm having some problems setting it up.

I've tried various configurations of alsa_out and sudo alsa_out, among with various options, however i've received the following errors:

elliot@ubuntu:~$ alsa_out
Capture open error: Device or resource busy
elliot@ubuntu:~$ sudo alsa_out
[sudo] password for elliot: 
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0,0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
jack server not running?





elliot@ubuntu:~$ sudo alsa_out
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0,0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa







alsa_out
djack server not running?
elliot@ubuntu:~$ alsa_out
Capture open error: Device or resource busy










elliot@ubuntu:~$ alsa_out -h
alsa_out: invalid option -- 'h'
Unrecognized option: -h
usage: alsa_out [options]

  -j <jack name> - client name
  -d <alsa_device> 
  -c <channels> 
  -p <period_size> 
  -n <num_period> 
  -r <sample_rate> 
  -q <sample_rate quality [0..4]
  -m <max_diff> 
  -t <target_delay> 
  -i  turns on instrumentation
  -v  turns on printouts








HALP? :-)

---

### Post by Breambutt on 2010-06-07
Type *aplay -l* to see a list of your audio playback hardware, you only need to pay attention to the card numbers. I'm guessing your onboard audio chip is card #0 and the USB device #1. Anyway, JACK should be running before you use alsa_out, but don't use sudo.

With the default JACK settings (of course you can configure this) the onboard audio (**hw:0**) is what JACK calls "system" and it's busy because, well, it's in use, and so you need to define alsa_out to use the USB device with *alsa_out -d **hw:1***. See what I did there? 

Try running this:

```
alsa_out -j USBaudio -d hw:1 -c 2 -r 48000
```

It creates the device USBaudio from the card #1 that was listed with *aplay -l* with 2 channels and sample rate of 48000.

I'll hang around online drinking coffee so I'll be around in case I'm not coherent enough.

---

### Post by WindriderMetal on 2010-06-08
That's brilliant! Exactly what i wanted, thank you so much! :-)

There is however one problem - the music stays perfectly in sync through both devices, however the audio from the USB device is rather crackly and jittery, it sounds much like it would if a buffer was set too low or something. The only option i've found within JACK for setting a buffer is "Periods / Buffer" within the JACK setup... but changing this just puts the two audio devices out of sync. Any ideas?

---

### Post by Breambutt on 2010-06-08
> **WindriderMetal said:**
> Any ideas?
None whatsoever!

**LATE EDIT:** Actually, uh huh, since it's the USB device that's snap-crackle-popping, try changing the period size of the *alsa_out* line by adding *-p xxx* (where *xxx* is a value higher than your frames/period for the system) in the parameters. I tried this with 128 frames/period in the JACK setup and *alsa_out -j USBaudio -d hw:1 -c 2 -r 48000 -p 64*. I had to bump the *-p* value up to 256 to get a clean output without jitter.

Skip the rest if this works, unless of course you want to read a bitter rant.

[COLOR="DimGray"]Well, are you running regular Ubuntu or Ubuntu Studio perhaps and which USB device do you have exactly? There's so much you can do and so much that can be misconfigured with JACK and I've heard so many different types of crackle and jitter that it's hard to tell right off the bat. Guess you have a bottleneck somewhere but I'm not familiar with your hardware and just noticed my own crappy budget USB preamp goes up to only 48kHz and probably has some troubles when pushed.[/COLOR]

[COLOR="Gray"]Like I said earlier, this doesn't depend on low latency so you could try increasing frames/period or even lowering the sample rate, make sure the driver is set to ALSA (and not portaudio for example or whatever the stupid PulseAudio might suggest), try playback only if your device(s) can't handle full duplex for some reason, tick or untick the realtime box, yadda yadda. Anyway, periods/buffer should be fine at the lowest value(s)... I think![/COLOR]

[COLOR="Silver"]PulseAudio is really starting to remind me of Windows; the easiest and fastest fix for almost any problem is to format / remove it. I don't like telling people to remove basic functions that come with Ubuntu as a default but honestly I think musicians won't be needing it for anything as JACK is how we roll and ALSA more than satisfies regular desktop needs.[/COLOR]

---

### Post by WindriderMetal on 2011-07-06
I've just had to revisit this thread to find out the settings again, since I had a hard drive die on me... And was shocked to see I hadn't replied!

After experimenting with some of the parameters, I eventually got it to work perfectly and have been using it ever since! So if you see this, thanks a lot man.

Here's a video of it in action, if you're interested!

[http://www.youtube.com/watch?v=0Wjr1VvFoBI](http://www.youtube.com/watch?v=0Wjr1VvFoBI)

---

