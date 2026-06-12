---
title: "Hauppage WinTV HVR-1950"
date: 2010-02-05
forum: Mythbuntu
---

### Post by Zack McCool on 2010-02-05
Getting the following errors when attempting to plug this USB tuner in:

```

Feb  4 14:56:24 barada kernel: [519626.730162] usb 1-4: firmware: requesting v4l-pvrusb2-73xxx-01.fw
Feb  4 14:56:24 barada kernel: [519626.734736] pvrusb2: wrong fx2 firmware size
Feb  4 14:56:24 barada kernel: [519626.734744] pvrusb2: Failure uploading firmware1
Feb  4 14:56:24 barada kernel: [519626.734746] pvrusb2: Device initialization was not successful.
Feb  4 14:56:24 barada kernel: [519626.734749] pvrusb2: ***WARNING*** pvrusb2 device hardware appears to be jammed and I can't clear it.
Feb  4 14:56:24 barada kernel: [519626.734752] pvrusb2: You might need to power cycle the pvrusb2 device in order to recover.
Feb  4 14:56:32 barada kernel: [519633.885774] pvrusb2: Device being rendered inoperable

```

I have downloaded the latest driver from Hauppage, and this is apparently the problem after some research.  It seems that the current firmware image is too large for the kernel drivers, and the kernel thinks it is a bad image.

I no longer can locate the original CD for the device, so I am stuck in a place I don't want to be.

I am looking for one of two things:

1) Does anyone have a copy of the older firmware (successfully running on your system would make me happy!)

2) Does anyone have any tips to make the current firmware work?

I found some references to new versions of the kernel possibly correcting the issue, but this does not seem to be the case.  I have downloaded 2.6.33-rc6 from kernel.org, built a test MythBuntu 9.10 VM in VirtualBox, and tried it with the new kernel.  Still get the exact same error.

Any help would be great.  I am planning to build a new Atom-based MythBuntu machine for my living room TV, and would like to use this tuner since, you know, I already paid for it and everything...   ;)

---

### Post by rimshot4 on 2010-02-05
Wow, I've been working on this issue with a new out-of-the-box HVR-1950 all evening. It now ships with the new firmware, so I'm stuck too. 

From my research I've found that the Ubuntu team has a fix and will be backporting it into Lucid. Unfortunately that comes out in March. It's expected to be, I think, in the next stable kernel.

Here's a new driver that's supposed to work, along with a cryptic how-to: [http://www.isely.net/pvrusb2/pvrusb2.html#Download](http://www.isely.net/pvrusb2/pvrusb2.html#Download)

My major issue right now is that I don't know how to compile the driver. I've been using Ubuntu for about a month. Any help you can give would be very much appreciated! I'm trying not to blow my weekend on this thing.

Alternately let me know if you find the old firmware.

---

### Post by Zack McCool on 2010-02-05
Thanks for the info.  I'm going to give it a go after I get home from work this morning, and if it works, I'll be sure to report back.

I had seen the launchpad info suggesting that it would be fixed in Lucid, but it also suggested that it was because of the driver being updated in the newer kernel, but that's only the case if this driver indeed fixes it and is included in Lucid, as it is definitely not in the latest kernel versions.

If it does work, I'll post a little of a howto to try to get you through it...   ;)

---

### Post by Zack McCool on 2010-02-06
It's not working out as well as I'd like.  I'm having a hard time getting it to compile, and haven't had enough time to really spend on it.  

Basically, you need to link to a source tree, but I can't seem to find a suitable one, even though the linux-headers and linux-source packages are installed.

I'll work on it more Saturday night, and I'll update the thread after I either succeed or get fed up and throw a PC out of a window...   ;)

---

### Post by rimshot4 on 2010-02-08
Aha!

It seems that you merely need the firmware provided at isley.net, not a whole new driver. The firmware fixed my problem as well.

The link to the 8kb firmware: [http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw](http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw)

You'll want to place it in /lib/firmware/kernalversionfolder/

I emailed the opensource driver developer, Mike Isely, through his email listserv. Being quite a gentleman, he emailed me back the following day and gave me the solution.

Thanks Mike!

---

### Post by Zack McCool on 2010-02-09
That is EXACTLY what I've been looking for!

I will download it now, and give it a try in the morning.  That should solve the issue, though.

Thanks!
Joe

---

### Post by Zack McCool on 2010-02-11
That firmware definitely did the trick.  

I booted to the Mythbuntu CD, did the initial install, opened a terminal window and copied the firmware to /lib/firmware and /target/lib/firmware, then connected the USB cable and ran the backend config and Myth found the device with no issues.

Still haven't connected the antenna to it yet (no time), but I don't expect that there'll be any more issues...

Thanks for the help!

---

### Post by jerrylamos on 2010-02-11
> **Zack McCool said:**
> 
I booted to the Mythbuntu CD, did the initial install, opened a terminal window and copied the firmware to /lib/firmware and /target/lib/firmware, then connected the USB cable and ran the backend config and Myth found the device with no issues.

Still haven't connected the antenna to it yet (no time), but I don't expect that there'll be any more issues...


Zack, how did you make out?  mplayer runs fine for me. 

Mythbuntu installed from Synaptic onto Ubuntu 9.10 Karmic Koala recognizes the card but claims no signal?  

The HVR-1950 input signal is analog channel 4.

I'd be happy with mplayer/mencoder except how do I schedule recording?

Thanks, Jerry

---

### Post by Zack McCool on 2010-02-12
Chances are, I won't get the time to play with it until the weekend.  But you might want to give tvtime a shot.  Or maybe vlc.  Not sure if mplayer is well-suited to the task...

I'll let you know how I make out with Myth once I get that antenna hooked up...

Also, just ordered my Ion Nettop from System76, so hopefully I'll have a fully-functional system on my TV soon!

---

### Post by rimshot4 on 2010-02-12
> **jerrylamos said:**
> Zack, how did you make out?  mplayer runs fine for me. 

Mythbuntu installed from Synaptic onto Ubuntu 9.10 Karmic Koala recognizes the card but claims no signal?  

The HVR-1950 input signal is analog channel 4.

I'd be happy with mplayer/mencoder except how do I schedule recording?

Thanks, Jerry

Jerry,

I can't for the life of me get any channels. So the device is recognized, but I can't watch anything on MPLayer or anywhere else. I'm trying to use it with analogue cable. Do you use it with analogue, and if so, how did you go about getting your channels.conf together?

-Jesse

---

### Post by jerrylamos on 2010-02-13
Some things I did:

My HVR-1950 is attached to the output of the HDTV to analog broadcast, in my case U.S. broadcast channel 4

synaptic install ivtv-utils, mark & install everything it wants
synaptic install mplayer
copied capture driver into /lib/firmware, for HVR-1950 I have it is 
v4l-pvrusb2-73xxx-01.fw
which I got from the internet, look at 
[http://www.isely.net/pvrusb2/setup.html#Firmware](http://www.isely.net/pvrusb2/setup.html#Firmware) 
and select
[http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw](http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw)

start tv display with
ivtv-tune -c 4 --device=/dev/video0
mplayer -vf pp=lb /dev/video0

When that worked, this is ubuntu 9.10 karmic, I then installed
tv-viewer from sourceforge.net.  It uses mplayer.

That required getting from synaptic the 8.5 levels of
tcl
tk
remove the 8.4 levels.

tv-viewer does display and also schedule recordings - I'm still learning how to use it..

The recordings are mpeg, a bit big, which I displayed by installing from synaptic:
gnome-mplayer
gstreamer.10plugins 
three versions:  good, bad, and ugly....

I've spent some time with myth tv which doesn't see any output from the hvr-1950 even though mplayer and tv-viewer work fine.

Good luck...

Jerry

---

### Post by rimshot4 on 2010-02-14
Jerry, 

I discovered the same program last night, although I never ran the IVTV command. It's quite good, though I wish the recording scheduler had a better GUI and series record functions. But, problem solved!

I don't suppose either of you gentlemen have gotten the remote to work yet? Still working on that one. Linux hardware installation has a steep learning curve.

Thanks,

Jesse

---

