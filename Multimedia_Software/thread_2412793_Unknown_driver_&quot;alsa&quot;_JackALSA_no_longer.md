---
title: "Unknown driver &quot;alsa&quot;: Jack/ALSA no longer playing nice suddenly"
date: 2019-02-17
forum: Multimedia Software
---

### Post by Bucky Ball on 2019-02-17
Hi all,

**Firstly**, using Xubuntu-core 16.04 and working on audio with Bitwig Studio. For hardware, I have an old Hoontech DSP24 eight channel audio interface. It's great and working fine. The card is referred to as an 'ICE1712' device or 'DSP24'. I think they were fairly common back in the day and from the first time I used the Hoontech on the Xubuntu box, it has always 'just worked'. No diddling around necessary. Ditto with Jack. First time I launched it, it just worked; saw the Hoontech and all its ports (has MIDI ports, too). Until about three days ago. 

**Some background**. I have been using QJackctl to start and use jack. Everything was working beautifully. Working late one night on something, closed down the computer with droopy eyes, get up inspired the next day to continue work, boot up and Jack and ALSA are no longer talking to each other. Haven't played a note or created anything since. Except probably some confusion.

I have spent literally days on this and am here through desperation. I've hit the wall. Scoured the net and found nothing that fits with what happened or much that fits the errors. Thing is, I didn't fiddle or tweak any file. Wasn't digging around in code or changing files. Was just sitting there working and then closed down, switched the machine off, switched it back on the next day. 

The only thing I can think of at this point is that when I closed down, I left something open and that, in turn, has left something hanging and I can't find what. I was playing with Ardour that night as never dug around much there and had it and Bitwig open at the same time at one point. I did read somewhere about some anomaly with Ardour/Jack, but apparently that was fixed. Is it possible that I have stopped jack and quit QJackctl while Ardour was still open and this has broken something? I was also playing around with Audacity for a bit with both Ardour and Bitwig open at one stage. I definitely stopped and started QJackctl a number of time during the session with Ardour open (Bitwig is very robust and solid and is not effected by that, don't know about Ardour or Audacity).   

**To what actually happens**. When I launch QJackctl, this is what I get in the 'Messages' window.

```
00:50:43.659 Logging started --- Mon Feb 18 00:50:43 2019 ---
00:50:43.695 Statistics reset.
00:50:43.702 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
00:50:43.741 ALSA connection graph change.
```

When I now click 'Start' in QJackctl, I get the following.

```

00:52:17.784 /usr/bin/jackd -dalsa -r48000 -p256 -n2 -D -Chw:DSP24 -Phw:DSP24,2
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Unknown driver "alsa"
jackdmp 1.9.11
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
00:52:18.007 JACK was started with PID=6658.
00:52:18.013 JACK was stopped
00:52:20.020 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
```

And Jack, obviously, doesn't start. This is the line that has me totally bemused.

```
Unknown driver "alsa"
```

Now, if I open a terminal and ...

```
jack_control start
```

... jack seems to start (no error in terminal). If I then hit 'Start' in QJackctl, I get this in 'Messages'.

```
01:04:37.897 JACK connection change.
01:04:37.900 Client activated.
01:04:37.900 Patchbay deactivated.
01:04:38.113 JACK connection graph change.
```

But ... and it's a big one; when I click 'Connect' in QJackctl, under 'Audio' there is 'System', but under system I only have two output and two input ports; all the rest are missing. This suggest to me QJackctl is seeing and using the regular consumer audio card in the computer, NOT the 8 channel audio interface. It is an interface I am totally unfamiliar with. 

The whole system has always used the Hoontech and QJackctl has always showed the audio interface's ports which ends up being twelve audio ins and twelve audio outs under 'Audio' and the MIDI ports under the 'MIDI' tab. I've never used internal audio for anything (it is switched off in the BIOS in fact). The only thing this can be is the Hoontech 'consumer' audio card physically in the computer. To explain: the Hoontech audio interface plugs into its own PCI card on the computer and attached to that is a regular consumer type card that sits in another PCI slot. I have never used it, but now it pops up out of nowhere!

I have a feeling this could be related to Jack not finding Alsa because Alsa seems to be seeing the DSP24 and all of its ins/outs/MIDI ports.

So, at the end of my tether and eager to get back to work, so any ideas, clues, fixes, magic, spells, voodoo that might get me over this hump would be very much appreciated. I will say that I have tried quite a lot of things, but have avoided doing anything major because I didn't do anything major prior to this happening. I would rather not use and elephant gun to kill a mosquito, if you know what I mean, and figure I can't be too far away from the fix as I haven't done anything to take me too far away from a working, stable setup.

I am convinced, maybe stupidly, that this is something simple that is beyond my experience because I haven't recompiled jack or alsa or done any major tweaking ... then it happened. I didn't do anything. First everything just worked. Then it didn't. My closest guess is that the reason QJack is seeing the wrong ports is because of this ...

```
Unknown driver "alsa"
```

... as ALSA seems to see the audio interface fine and all its ports fine, but not Jack. Maybe it's not seeing the audio interface because ALSA 'owns' it and Jack can't talk to ALSA. 

**So my question** would be, how do I get QJackctl and ALSA playing nice again and get rid of that error message? 

All ideas welcome. :(

---

### Post by Claus7 on 2019-02-20
Hello,

haven't head of this before, yet, since you are getting messages about missing directories, have you tried to reinstall all these programs in question? I guess you have already tried, yet you do not clearly mention it. 

Have you checked also this:
[https://discourse.ardour.org/t/jackdmp-says-unknown-driver-alsa/81819](https://discourse.ardour.org/t/jackdmp-says-unknown-driver-alsa/81819)
?

Some very minor ideas at the time being...

Regards!

---

### Post by Bucky Ball on 2019-02-21
Thanks for your input, Claus7, but fixed. I still have absolutely no idea how jack broke in the first place, but in the process of trying to fix it, I uninstalled jack from the repos, downloaded jack from their site and installed that. It didn't work. 

Yes, I installed and uninstalled jack umpteen times to no avail, but once I started doing some more digging, I discovered that the jack I had installed was a mishmash of things and different versions. I'd overlooked the fact that the jack I'd downloaded from their site was still installed and I'd installed jack from the repos three or four times at least after that.

So, uninstalled the non-repo jack via a terminal (with 'sudo ./waf uninstall' for the curious), installed jack from the repos, rebooted the machine and all back to normal. 

Open Qjackctl, click start and no errors. Under 'Audio> System' I now have my Hoontech DSP24 back with its twelve output and ten input ports.

No idea what caused it but back to work and happy. There's a week I'll never get back, but these things happen and it got fixed eventually. I was looking down the barrel of an OS reinstall as I'd tried everything and was at a dead end, so I'm thanking my lucky stars.

---

### Post by Claus7 on 2019-02-22
Hello,

nice that you found solution to this problem that it was mismatch of versions after all.

Regards!

---

