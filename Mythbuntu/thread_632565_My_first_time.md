---
title: "My first time"
date: 2007-12-05
forum: Mythbuntu
---

### Post by brake16 on 2007-12-05
Good Morning

I'll soon be trying out Mythbuntu (my first Linux experience) with the following setup:

Gateway M-1617 (laptop)
CPU: AMD Turion TL-58 (1.9 GHz, dual core)
RAM: 2 GB (667 MHz, DDR2)
Video Card: ATI Radeon X1270 (built-in, "Up to 256MB HyperMemory", meaning it probably steals it from the system RAM)
Sound Card: built-in ("High Definintion Audio - 2 channel")
HD: 250 GB 5400 rpm
Remote: Harmony 880 (need IR port on computer yet)
Tuners: ATI/VisionTek TV Wonder 600 USB 2.0

My goal is to record HD OTA (atsc) for playback on my 1080p 50" Samsung DLP through the HDMI port that's built into the laptop.  I don't plan to try to hook up my satellite tuner to the laptop.  I picked up the TV Wonder 600 tuner on the recommendation from a friend, but I'm willing to get a different USB tuner if it will work better.  I'd also be willing to entertain the idea of an Expresscard 54 tuner (if such a thing were reasonably priced).

I've already tried using this setup with Vista and the software provided with the TV Wonder 600.  The audio & video became out of sync, and this became progressively worse as the recording went on (~1-2 seconds off after 1 hour).  I've since found other forums discussing this timing issue as a result of separate clocks for the audio & video that get out of sync due to high CPU demand, especially where the video and/or audio are on the mobo (both, in my case).  After many attempts to have as few processes running as possible (to no avail) I decided to try a Linux distro.  I've been looking for an excuse to try Linux, now those claims of "less resource demand than Windows" will be put to the test!

Long story short, does anyone see/foresee any problems with trying Mythbuntu on the setup I've described?  I know there can be issues between Linux and ATI video cards/tuners, but I'm seeing conflicting info on how far that's been resolved.  I'm willing to get a different tuner, but I'm pretty much committed to the video.  

If I don't hear anything from here, I'll be trying this out over the next week (and most certainly posting for setup help).  Wish me luck,

brake16

---

### Post by brake16 on 2007-12-05
BTW, this would make this a dual-boot machine (w/ Vista).

brake16

---

### Post by sloggerkhan on 2007-12-05
[http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1](http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1)
might be helpful, though there are other sources which may be more helpful.

---

### Post by twkisner on 2007-12-05
> **brake16 said:**
> Good Morning

I'll soon be trying out Mythbuntu (my first Linux experience) with the following setup:

Gateway M-1617 (laptop)
CPU: AMD Turion TL-58 (1.9 GHz, dual core)
RAM: 2 GB (667 MHz, DDR2)
Video Card: ATI Radeon X1270 (built-in, "Up to 256MB HyperMemory", meaning it probably steals it from the system RAM)
Sound Card: built-in ("High Definintion Audio - 2 channel")
HD: 250 GB 5400 rpm
Remote: Harmony 880 (need IR port on computer yet)
Tuners: ATI/VisionTek TV Wonder 600 USB 2.0

My goal is to record HD OTA (atsc) for playback on my 1080p 50" Samsung DLP through the HDMI port that's built into the laptop.  I don't plan to try to hook up my satellite tuner to the laptop.  I picked up the TV Wonder 600 tuner on the recommendation from a friend, but I'm willing to get a different USB tuner if it will work better.  I'd also be willing to entertain the idea of an Expresscard 54 tuner (if such a thing were reasonably priced).



Your tuner is on the list of "not supported".  The supported USB list is short (see link below). FYI there is an Air2PC USB tuner on e-bay now that works with Linux, still cheap last I checked.

[http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

Your milage may vary with your video card too.  I can't comment because I haven't tried, but I think the ATI driver for Linux isn't very friendly for options, so it may not work HDMI.

Speed/RAM/and HD are all fine,built in sound is probably fine as well.

Tom

---

### Post by uopjohnson on 2007-12-05
If you are willing to buy somehting else consider the HDHomeRun OTA tuners.  They are network tuners (not usb) but they are very well supported.

---

### Post by sloggerkhan on 2007-12-05
Do you know if HDHomeRun supports unencrypted analogue cable signals (ntsc)?

---

### Post by uopjohnson on 2007-12-06
seems to:[URL="http://www.silicondust.com/wiki/products/hdhomerun"]
http://www.silicondust.com/wiki/products/hdhomerun[/URL]

---

### Post by twkisner on 2007-12-06
> Do you know if HDHomeRun supports unencrypted analogue cable signals (ntsc)?

> **uopjohnson said:**
> seems to:[URL="http://www.silicondust.com/wiki/products/hdhomerun"]
http://www.silicondust.com/wiki/products/hdhomerun[/URL]

No, I looks like it only supports -digital- not analog.  I don't have one, but I was under the impression that it was only ATSC and Digital Cable.

---

### Post by uopjohnson on 2007-12-06
ah yes.  I read the OP wrong.  You really want one of the pvr-x50 cards to do analog cable.

---

