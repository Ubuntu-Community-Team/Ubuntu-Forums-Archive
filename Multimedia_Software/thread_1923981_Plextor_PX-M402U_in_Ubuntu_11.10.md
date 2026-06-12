---
title: "Plextor PX-M402U in Ubuntu 11.10"
date: 2012-02-11
forum: Multimedia Software
---

### Post by bavid on 2012-02-11
Has anyone been able to get the Plextor PX-M402U USB capture box working in 11.10? I had it working on a machine with an older version of Ubuntu (8.something?), which recently suffered a hard disk failure. I was using the GO7007 driver. 

Initially, I was unable to compile the GO7007 driver, but got it working after I bypassed the compilation of the gorecord application. (Unfortunately, not having gorecord makes testing difficult.)

Now I can record from Myth, but it's taking the sound from my laptop's internal mic, not from the audio encoder on the Plextor box. Previously, I could acquire sound from /dev/dsp0, but now I don't have anything under /dev/dsp*. I suspect that the driver is not fully loading based on the following dmesg results:

```
usb 1-3.2: new high speed USB device number 13 using ehci_hcd
go7007-usb: probing new GO7007 USB board
go7007: registering new Plextor PX-M402U
wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB
go7007: probing for module wis-saa7115 failed
go7007: registered device video0 [v4l2]

```

Has anyone else tried this? At the moment, falling back to 10.04 is the best idea I can come up with.

(Yes, I realize that this is an old capture card and that it hasn't been actively supported in years.)

---

### Post by seltzered on 2012-08-28
Hey,

Just curious if you ever had success with this. I'm trying to get this running on 12.04, no luck yet. I wasted a bunch of time attempting to port the earlier drivers from go7007.imploder.org, only to realize the linuxtv project seems to keep them updated.

I'm stuck in the same spot unfortunately though, so far I've tried the following on a new 12.04 install

sudo modprobe go7007-usb
sudo modprobe go7007

#unplug/replug convertX

sudo apt-get install xawtv
xawtv

and then the device isn't detected. My guess is it's because usbfs isn't supported in kernel 3.x, haven't tried to work around it yet.

---

