---
title: "Help with JACK"
date: 2006-01-03
forum: Multimedia &amp; Video
---

### Post by dawynn on 2006-01-03
Having a couple problems with installing JACK.  I'm running breezy kubuntu with a Turtle Beach Santa Cruz sound card.

First, as requested by the documentation, I've added the following line to /etc/fstab:

shmfs           /dev/shm        shm	defaults	    0	    0

This always causes a "fail" in the startup line for "mounting local filesystems".  Any idea as to why this won't work?

Once my system loads, I start qjackctl, and push the start.  I get the following messages.  What's the deal with alsa_pcm?  What do I need to do to correct this?

05:22:00.964 Patchbay deactivated.
05:22:01.303 Statistics reset.
05:22:01.321 Startup script...
05:22:01.322 artsshell -q terminate
05:22:01.476 MIDI connection graph change.
JACK compiled with System V SHM support
05:22:01.966 Startup script terminated with exit status=256.
05:22:01.968 JACK is starting...
05:22:01.969 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2
05:22:01.987 JACK was started with PID=8079 (0x1f8f).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
05:22:02.192 MIDI connection change.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
05:22:02.374 JACK was stopped successfully.
05:22:02.416 MIDI connection change.
05:22:04.227 Could not connect to JACK server as client.

---

### Post by mpvano on 2006-01-03
What kind of audio card are you using? Is it really the SECOND interface? If not, you need to use hw:0 for the device setting.

You haven't got there yet, but if you don't have a sequencer installed, you'll probably fail to load later in the process. I use "snd_seq_oss" to shut up the error message and get jack to load, but I'm not currently using any midi - you may need to make sure you have the correct driver loaded for your use.

Also, Unless your machine is unbelievably fast, you'll probably never get stable operation with the settings you're using for buffering unless you install the realtime lsm kernel configuration module. That may not be a problem for your application if it can handle greater latency, but you would probably need to use bigger -p and or -n settings (despite the fact that jack supposedly doesn't use settings greater than 3).

On most of my machines that are > 500mhz Pentiums I get pretty stable results with latencyies over 300ms or so without the realtime lsm. (It's confusing to install, but reduces latencies enough to run stably with buffer delays under 50ms).

hope this info helps,

Mario

---

### Post by dawynn on 2006-01-03
Aha!  Yep -- I had messed up my setup.  I'm using a Turtle Beach Santa Cruz card.  Once I changed setup to look for hw:0, I still can't connect, but I receive a different set of messages.  Any ideas?

10:37:01.540 Patchbay deactivated.
10:37:01.838 Statistics reset.
10:37:01.856 Startup script...
10:37:01.856 artsshell -q terminate
10:37:01.946 MIDI connection graph change.
10:37:02.304 Startup script terminated with exit status=256.
10:37:02.306 JACK is starting...
10:37:02.306 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
10:37:02.323 JACK was started with PID=8170 (0x1fea).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
10:37:02.350 JACK was stopped successfully.
10:37:02.526 MIDI connection change.
10:37:02.728 MIDI connection change.
10:37:04.542 Could not connect to JACK server as client.

---

### Post by mpvano on 2006-01-03
Sure,

Your card doesn't support the parameters you've specified under ALSA.

You are using the lowest level ALSA functions when you open a device named "hw:n" (This is what jackd likes). They read directly from the hardware and often have a lot of constraints on buffer size and layout.

Unfortunately, the ALSA developers were originally unwilling to give developers a function that lets them FIND OUT the capabilities of the card.  You need to play a sort of guessing game with ALSA to find out what the card can do by probing the values if you don't know them from some other source of information.

Try starting with two of the very smallest buffers and working up until it stops giving this error message. Some cards can only transfer small buffers. Other cards have fixed buffers and ONLY work with one magic set of buffer sizes (often a binary multiple).

Once you get past that, try gradually increasing the number of periods until the message reappears (despite the fact that jack claims it doesn't use more than 3, some cards only work that way).

If your card doesn't support large enough total buffers to eliminate the dreaded "xruns", you may be forced to figure out how to build and install the "realtime lsm" module to give your audio programs very high priority without running them as root.

You can learn more about your card's capabilities by looking up the information about your card in the documentation files that come with the alsa source files. You can also often learn even more by reading the actual source files for your card.

Another source of some information is the /proc directory. /proc/asound has a number of "virtual" files that contain information about your alsa cards and their capabilities.

hope this helped,

Mario

---

### Post by dawynn on 2006-01-03
OK -- I had to use the realtime-lsm module in order to avoid the xruns.  in the Setup panel of qjackctl, I found that I could use any Frames/Period setting of 512 or lower.  Periods/Buffer of 2 - 10 all worked (I didn't try higher settings).  I did notice that it wasn't able to work at 24bit or 32bit, so I set it to force 16bit.

I'm trying to find documentation on the various settings, but I'm having difficulty.  In general, what works best for the quality of the recording?  Is it better to use higher or lower Frames / Period?  How about Periods / Buffer?

What else should I review for maximum sound quality?

---

### Post by mpvano on 2006-01-04
It sounds like you're on the right track. The documentation is, indeed a terrible paper chase. Here are a couple of hints on that:

There's a brand new Jack site that actually has more up-to-date info at [http://www.jackaudio.org/](http://www.jackaudio.org/). It has some better links to various kinds of information about latency, etc.

You can install the linux-docs package for your current ubuntu kernel using synaptics or apt-get. It installs most of the alsa documentation files in /usr/share/doc/linux-doc-2.6.... whatever your kernel version is. Look in the subfolder sound/alsa.

Download the current ALSA sources from [http://www.alsa-project.org/](http://www.alsa-project.org/) and unpack them. You need to search a bit to find all the documentation tidbits and source file pieces for your card, but it can be worth the search. The comments in the source files often have more hints about problems or configuration options.

In general, the recommended strategy for settings is to use 2 Periods, and the lowest value of frames/period that doesn't give you xruns except when starting up or shutting down.

Unless you are using a fairly fast CPU (2Ghz or faster Pentium), I think you're going to have trouble at 512 frames per period with xruns. If you are getting more than you can tolerate, you may have to build a custom kernel with different settings or using some of the patches pointed to by the jack website. I'd try to avoid this if at all possible, however, because it's a major nuisance duplicating the ubuntu configuration adequately and you'll need to update your kernel yourself when bugs are found.

I've had some luck running a simpler window manager, since some WM operations definitely cause trouble. You can install a stripped down manager like fvwm2 or blackbox with synaptics or apt-get and choose it at login only when you are doing jack things.

I do volunteer work supporting a major community radio station, and doing field concert and other recording for it. I've had pretty good luck for my purposes by just tolerating higher latency if it eliminates xruns. I usually use a small external mixer to handle monitoring, anyway, so latency isn't a big problem unless I'm doing something requiring overdubs, or laying down tracks one at a time - something one rarely does in live music or interview recording.

If you are planning to use ardour to do studio style multitrack recording, you'll need to get latency low enough to avoid monitoring problems (unless your cards support hardware monitoring). This usually means latencies under 30ms, but that's hard to get without special kernels.

You need to get rid of the xruns completely, but if you can't do it without latencies that are too high for software monitoring, you should give things a try anyway. As long as you are aware of the delays, you can still do very good work with latencies as high as 300-500 ms as long as you are careful about how you use plugins, etc.

WRT bit depth, few older cards support 24 bit samples, so you can speed up jack startup by telling it not to even try 24 and 32 bit depths at startup. A good 16 bit card is adequate for most recording, but requires a lot more attention to levels and headroom throughout the recording and mixing process. The extra 4-5 bits (few cards actually deliver more than 21 bits of data in that 24 bit sample) are really useful in allowing you more headroom while recording, but if you are careful setting levels and "ride" the gain carefully, you can get professional results at 16 bits - just make sure you're getting the most out of all 16 bits!

I also design and build automated archive, logging and streaming sites for FM radio stations using linux and other -nix variants. This is much easier than live recording with linux, but also has its own challenges. I can tell you that you're in for a lot of searching on Google, subscribing to a lot of mailing lists, and a lot of "grep" searches through packages, but the results are very rewarding. I'm still finding that most of the existing documentation is WAAAY out of date or just plain missing, so take any documentation with a grain of salt.

The good news is that I've definitely found Ubuntu to be a simpler starting point for working with audio than the other distributions I've tried. It usually has fairly up-to-date kernels with current ALSA drivers and patches. Most popular packages are easily installed from the Ubuntu repositories and generally work the first time. Once you get that far, it's usually pretty easy to remove the prepackaged version and install the latest bleeding edge versions without having to try to guess whether the package EVER worked at all. In many cases, later Debian packages are directly available directly from the developer sites and are quite compatible with the Ubuntu package management. I'm even considering using stripped down Ubuntu configurations for some multimedia web server sites I'm working on right now.

hope this helps...

Mario

---

### Post by dawynn on 2006-01-04
All right, here's the deal.  I'm just trying to convert some of my old records / tapes into usable formats.  Problem is, although I can hear sound coming in from the input on my computer (it's coming through my computer speakers), I haven't found an application yet that can actually record the sound.  That's why I was hoping to get JACK to work.  

This morning I tried "timemachine" after I'd started JACK.  I figured it had a simple enough front-end, it should be able to do the job.  But after timemachine had recorded a sample, I loaded the .w64 file into audacity -- and it was still dead air.  I've also tried (while JACK is shut off) to use arecord to capture what's coming in -- but it can't even find the input.  I use kmix for my mixer, and it shows that both input bars and both capture bars are marked for recording.

So, even JACK didn't provide the results I'd hoped for.  Any suggestions as to anything I might be completely overlooking?

Thank you for your help up to this point.

---

### Post by mpvano on 2006-01-05
Hmmm...

I think Jack is overkill for what you are doing.

You normally should not need to use jack for simple recording and editing. almost any OSS or ALSA recording application should fine if you have the mixer set properly. I'm guessing the mixer settings are confused for your card.

Here are a couple of things to try.

1. Make sure that ALL the mixer controls for your card are visible in the mixer you are using - the gnome-volume-control applet disables many of the controls and switches in the preferences - turn them back on and try to determine what they do.

2. Try BOTH the OSS and Alsa variants of the mixer. They often have different mappings of the card controls to sliders.

3. Take a look at the non-x windows Alsa mixer called "alsamixer". When you start it in a terminal window, type F5 to switch to viewing ALL the mixer controls. Make sure they are set to route audio properly.

4. Make sure you understand how your card works. Most audio cards have more than one routing path for audio recording depending on whether you want to record from a single source or record a "mix" of them. There are several completely different ways these two modes are implemented. You'll have to experiment with the record enabling and mute switches for all of the controls.

5. Try to set up a controlled experiment that does the following:
 - disables ALL input monitoring to the speaker
 - enables the line input as the recording source
 - enables recording from a single source (not a mix)
 - sets whatever appears to be the cards record level setting to 50%
  (the control may be marked record, capture, igain, input, or ?)
 - unmute the PCM playback and set it to 50%

Now put the input from a known audio source at line level into the line input.
You should NOT hear it.

Try running a program that copies the audio capture input to the wave output. Heres one that works for me

arecord -t raw -f cd | aplay -t raw -f cd

This uses the low level alsa record and playback test programs on your default interface (hw:0). (By the way, check out the man page - these are actually test programs for alsa and let you mess around easily with all the possible settings of your card's drivers - this is a much easier way to determine optimal period and other settings for your cards than constantly restarting jack until it runs).

You can now play with the mixer controls until you get output. You can test if it's coming through the record program by seeing if the PCM or WAVE playback slider affects it. If it doesn't you're listening to record monitoring, not the record input copied to the playback output. The output should also be noticeably delayed in time.

Once you get this working you should be able to record just fine with audacity, mhwaveedit, the record program from the xawtv utilities package, or even just by using sox or arecord by themselves.

One more trouble spot many people have, is that gnome and kde both default to enabling daemon programs that disable your sound card and take it over to make cute noises. MAKE SURE you are NOT running a sound daemon! Ubuntu has two control panels that affect this - 

In the "Sound Preferences" control panel make SURE "enable sound server startup is NOT checked".

In the "Multimedia Preferences" control panel make SURE that OSS is selected for both "source" and "sink" defaults.

Now run "ps ax | grep esd" If you see a program called esd listed in the output, you must stop it. Try "sudo killall esd" - if that doesn't kill it you'll need to do "sudo kill -KILL nnn" where nnn is the process id. If this program keeps reappearing even after you've disabled it in the preferences, you need to find out what's starting it and stop doing that!

You may still run into problems with skips and dropouts, and there are definitely solutions for those, but the first step is to get the esd daemon disabled and get simple recording and playback working as described above.

It's a little rough around the edges, but I've had pretty good luck with the program called "mhwaveedit" in the ubuntu repositories. It has input metering, graphic editing, format conversions and can use a lot of external effects. Unfortunately, like all Ubuntu audio programs, it doesn't support mp3 unless you uninstall it, download the source, and all the source dependencies from the authors website and rebuild it.

PS - My FAVORITE audio capture program (because of its simplicity) is the program called "record" which does nothing more than show the record level and let you control capture into wave files. It's part of the xawtv-utilities package and its simplicity makes it very reliable. I use it to record stereo concerts and it's never failed me.

hope this gives you some more ideas.

Mario

---

