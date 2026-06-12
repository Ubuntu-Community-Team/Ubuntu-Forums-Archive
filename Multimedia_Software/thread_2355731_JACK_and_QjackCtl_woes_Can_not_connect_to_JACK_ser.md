---
title: "JACK and QjackCtl woes: Can not connect to JACK server as client"
date: 2017-03-16
forum: Multimedia Software
---

### Post by Bucky Ball on 2017-03-16
Xubuntu-core 16.04.2 with STA DSP24 soundcard and breakout box (the card also known as Envy24 or ICE1712 I believe; common). 

Things were working, to a point. When I launched QjackCtl and hit 'Start', no errors and all good. Trouble was, with a mic plugged in to the breakout box, no sound. In my quest to work out why, I installed a couple of things, among them Mudita (a GUI specific to that card and nice) and also multimedia-jack. This is where the problems start, nearly.

Retried and still nothing. When I'm checking 'Connections' in QjackCtl, I see nothing that looks like it's disconnected anywhere. There should be sound. Hunt through websites. Everything seems to be as it should be. Then discover something interesting. Pulseaudio, which I'm also running, can interfere with Jack and prevent it from accessing the soundcard (yes, Pulse is using the DSP24). Thinking this is worth a shot, I open Synaptic and 'Complete Removal' of multimedia-jack ensues. This is where the real nightmare begins. 

Now, QjackCtl doesn't start at all. It launches, but when I try to start I get the message window:
> 
Could not connect to JACK server as client.
- Overall operation failed.
- Server communication error.

Below is more detailed output from the 'Messages' window:

```
15:31:06.488 JACK is starting...
15:31:06.489 /usr/bin/jackd -dalsa -r48000 -p512 -n2 -D -Chw:DSP24,1 -Phw:DSP24,1
Cannot connect to server socket err = Connection refused
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
no message buffer overruns
no message buffer overruns
no message buffer overruns
jackdmp 1.9.11
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
Cannot lock down 82274202 byte memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:DSP24,1|hw:DSP24,1|512|2|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
15:31:06.702 JACK was started with PID=2459.
15:31:13.716 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
Cannot read socket fd = 18 err = Success
Cannot open qjackctl client
CheckRes error
JackSocketClientChannel read fail
JackShmReadWritePtr1::~JackShmReadWritePtr1 - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
Unknown request 4294967295
CheckSize error size = 0 Size() = 12
CheckRead error
15:45:58.625 JACK is stopping...
Jack main caught signal 15
```

Very keen to get this happening. I was making sure I could do something as simple as getting Jack to work with a microphone and Audacity before I whack Ardour on here and spend some hundreds of dollars on Bitwig (music technologist and musicologist, so no, Bitwig not too complicated, but exactly what I'm after and the reason I'm bothering with trying this out on Linux and not simply using Windows, which is what I'm familiar with for digital audio production). :) So far, I haven't managed to get past step one, although making good progress with other things re. Linux digital audio. 

Just to add, in QjackCtl in 'Settings> Advanced' I have the input and output set to 'hw: DSP24,1'. This was shown to be the card from a command I pumped in last night. Any help, ideas, suggestions appreciated. This is hopefully a simple thing and my inexperience is the hurdle. I'm thinking of reinstalling multimedia-jack to get me back to square one, if it does, but it was working beautifully before I installed and then uninstalled it. Previously, when I started JACK it automatically stopped Pulse and took over the soundcard without me doing a thing (and Pulse kicked back to life and worked normally when I stopped jack and closed QjackCtl). Now there is chaos and I'd really like to get to where I was prior to four hours of confusion. :|

More info required, just ask. :)

PS: I also tried uninstalling QjackCtl and whatever jack I could find and reinstalling QjackCtl. Being a novice to this, shooting blindly and getting nowhere fast. I'll keep plugging away and eventually I might hit a can!

---

### Post by Bucky Ball on 2017-03-16
Update: I figure when I 'Completely removed' multimedia-jack using Synaptic, it dragged out something vital to jack with it. So ... reinstalled multimedia-jack and errors, but different. QjackCtl launches, I hit 'Start' and this is what I get. 

```
17:00:38.634 JACK was started with PID=2359.
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
17:00:40.647 JACK connection change.
17:00:40.648 Server configuration saved to "/home/bucky/.jackdrc".
17:00:40.649 Statistics reset.
17:00:40.652 Client activated.
17:00:40.652 Patchbay deactivated.
17:00:40.841 Buffer size change (512).
cannot lock down memory for RT thread (Cannot allocate memory)
ALSA: poll time out, polled for 15999218 usecs
DRIVER NT: could not run driver cycle
17:00:54.851 JACK connection graph change.
jack main caught signal 12
no message buffer overruns
17:00:54.852 Shutdown notification.
17:00:54.853 Client deactivated.
17:00:54.854 JACK is being forced...
cannot read server event (Success)
cannot continue execution of the processing graph (Bad file descriptor)
graph error - calling shutdown handler
17:00:55.054 JACK was stopped
```

Could be getting closer or going in circles. Thing is, multimedia-jack drags in a whole load of stuff that wasn't required when jack was at least starting previously. Stuff I don't need now and may never need. I'm a stickler for getting rid of bloat, so ideally I would like to get rid of most of what multimedia-jack dragged in and keep the basic meaty goodness that I actually do need to have jack functional ...

PS: Not sure if mentioned hardware, but plenty capable. i7 processor and 16Gb of RAM. Been using it to sync HD vid and high quality audio then edit so plenty of grunt for this.

PPS: Just tried with 'Realtime' unticked in the QjackCtl settings. No diff.

---

### Post by Bucky Ball on 2017-03-17
Bump

---

### Post by Bucky Ball on 2017-03-21
Ok. Totally purged all things jack, including multimedia-jack and all related bits and pieces. I then reinstalled qjackctl ONLY and everything worked. Jack launches, starts with no issues. Problem solved. :)

These were the commands:

```
sudo apt-get purge --auto-remove jack
sudo apt-get purge --auto-remove jackd
```

I may also have run:

```
sudo apt autoremove
```

... after that. Then I installed qjackctl, rebooted, all good.

---

