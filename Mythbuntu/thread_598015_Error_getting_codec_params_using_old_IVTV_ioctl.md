---
title: "Error getting codec params using old IVTV ioctl"
date: 2007-10-30
forum: Mythbuntu
---

### Post by bkhull on 2007-10-30
I got a Hauppauge WinTV PVR-350 after looking at the mythTv documentation, and loaded MythTV; immediately, I was able to watch TV on it, but I had to fool around a while to get sound because I'm using a USB device instead of the motherboard sound card.  Now I always get a failure to initialize video when I go to view TV.
Looking at /var/log/mythtv/mythtvbackend.log, I find I get this:

2007-10-30 20:00:00.322 TVRec(1): Changing from None to WatchingLiveTV
2007-10-30 20:00:00.329 TVRec(1): HW Tuner: 1->1
2007-10-30 20:00:00.537 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
                        eno: Bad address (14)
2007-10-30 20:00:21.357 TVRec(1): Changing from WatchingLiveTV to None

I have tried rescanning for channels with US-bcast, US-cable, and US-cable-hrc, rebooting with 30 seconds of power off etc, and I'm not getting any headway there; does this look familiar to anybody?  What am I doing wrong?  It's maddening to be so close and have nothing (again).  My sound works beautifully now, but no video after I had it to start with is very frustrating.

---

### Post by superm1 on 2007-11-15
Are you still encountering this?

---

### Post by dizzl on 2007-11-18
I got the same error on my PVR-500 on both tuners. I'm in Europe, using PAL.

---

