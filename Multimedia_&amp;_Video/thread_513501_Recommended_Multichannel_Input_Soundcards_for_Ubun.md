---
title: "Recommended Multichannel Input Soundcards for Ubuntu Studio?"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by dbsoundman on 2007-07-30
I was just recently given this wonderful computer with Ubuntu which I have "upgraded" to UbuntuStudio. Now I have Ardour and I'd love to use it but I need a good soundcard for recording. I'd rather not go out and buy one that doesn't work well with Ubuntu, so I was just wondering what you all might suggest for a soundcard or some other method of getting ideally 8 tracks but 4 would be all right of audio input and 2 tracks of audio output on a soundcard. If I could make something like firewire work that would be fine as well, but I would rather not make this a very expensive proposition either. From what I recall, soundcards in general are cheaper than, say, the Lexicon Omega USB interface I use with my Dell Windows XP laptop, so I'm hoping there's something out there for me to use.

Thanks!

-Dan

---

### Post by stmiller on 2007-07-30
PreSonus is going to be your best bet. They have Linux drivers, and support Linux.

Check out this page:

[http://www.ffado.org/](http://www.ffado.org/)

---

### Post by Drunky on 2007-07-30
I've heard that M-Audio stuff is good.  And the drivers are supported.

No?

---

### Post by thisllub on 2007-08-03
I just installed Studio64 on this PC.
I just purchased a Lexicon Omega and it works perfectly in Ardour without any configuring at all.

The only thing I made sure of was to disable the onboard sound before the installation.
As Studio 64 is Debian etch it should work in Ubuntu.

I have another PC with Ubuntustudio on it. I will see if it works there later.

---

### Post by fbusy on 2007-08-04
I use a M-audio mobile USB in ubuntu and it works great.. its a very simple interface but its all i need : add also that i got it working in ubuntu in a couple minutes. hope i helped some.

---

### Post by KillerBob-it on 2007-08-04
I tried Ubuntustudio with a M-Audio FW1814 firewire device but there's no way to make it working...](*,)

---

### Post by El Flauta on 2007-08-05
On M-Audio web site, you can see the support/drivers section. Some hardware are compatible with Linux, like Audiophile 2496 :)

You can see the drivers available [HERE]("http://www.m-audio.com/index.php?do=support&tab=driver").

---

### Post by fbusy on 2007-08-13
look up    madfuload    .. i was able to load my m-audio mobile pre card with it quickly, im not sure it will work with the firewire, but i know it has code for more m-audio products within it. . . also i installed wine and then adobe audition im in heaven removing windows from my computer woo woo
hope it helps

---

### Post by tgalati4 on 2007-08-13
M-Audio Delta66 using the envy24control works for me.

---

### Post by paulg on 2007-08-17
Your most stable choice in terms of performance, value stability is PCI at the moment. Anything in the M-Audio Delta series or the Audiophile would be a solid choice depending on budget and input/output requirements. Depending on where you are in the world Terratec is another solid choice.

Some USB devices work well but from what I have read FireWire will be the way to go for external audio for a few technical reasons in how the audio transport is handled over FireWire vs. USB (e.g. USB cannot be time sync'd to the processor). That said, FireWire Audio on Linux isn't quite ready for prime-time but it's getting there ...quickly!

As mentioned before, check out FFADO. It needs to be installed from SVN and you would likely need to do a custom compile of ardour, JACK (and qjackctl) so you may want to check out [FreeBoB]("http://freebob.sourceforge.net") which was the precursor to FFADO. I believe is FreeBoB aware version of JACK is available in the Studio repository but something for you to look up first.

I personally own and use an M-Audio MobilePre. It works well enough for me but I do get many random xruns in JACK even with the latency turned up well beyond what the device is capable of. From what I have read the issue is with USB and the fact that there is no built in timing mechanism and not necessarily a driver issue. When all of the features in FFADO are implemented this should not be a problem with FireWire. Apparently it's not perfect yet and [some?] FireWire devices still have this problem in Linux.

---

### Post by WestCoastSuccess on 2007-08-19
I'm not using Ubuntu Studio (I'm on Feisty) but thought I'd mention I bought the M-Audio FireWire Solo today and it seems to work fine with jackd/freebob.

On my AMD 64 X2 with 2GB RAM I'm at 1.67ms latency with no X Runs.

I posted some info on how I got it set up here: [http://ubuntuforums.org/showthread.php?p=3215654#post3215654](http://ubuntuforums.org/showthread.php?p=3215654#post3215654)

---

### Post by dbsoundman on 2007-08-27
Ok, so I bought a used M-Audio Delta 1010 on ebay. However, I can't get jackd to connect to it. Envy24Control shows up fine, but I can't use Ardour without jack running, and jack won't connect to it. Help?

This is the error sequence that Jack shows me:

```
17:58:24.957 Patchbay deactivated.
17:58:25.024 Statistics reset.
17:58:25.039 Startup script...
17:58:25.039 artsshell -q terminate
17:58:25.080 MIDI connection graph change.
can't create mcop directory
Creating link /home/dan/.kde/socket-blackdiamond.
17:58:25.339 Startup script terminated with exit status=256.
17:58:25.341 JACK is starting...
17:58:25.342 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p4096 -n2
17:58:25.367 JACK was started with PID=6930 (0x1b12).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|4096|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 4096 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: cannot set period size to 4096 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
17:58:25.395 JACK was stopped successfully.
17:58:25.396 Post-shutdown script...
17:58:25.396 killall jackd
jackd: no process killed
17:58:25.569 MIDI connection change.
17:58:25.616 Post-shutdown script terminated with exit status=256.
17:58:27.586 Could not connect to JACK server as client. Please check the messages window for more info.
```

Help?

-Dan

---

