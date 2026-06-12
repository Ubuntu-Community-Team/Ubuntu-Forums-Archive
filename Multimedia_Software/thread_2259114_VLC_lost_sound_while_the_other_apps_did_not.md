---
title: "VLC lost sound while the other apps did not"
date: 2015-01-02
forum: Multimedia Software
---

### Post by denarced on 2015-01-02
This was seemingly difficult to solve so I'll post the procedure to help others.

**The Problem**
VLC lost sound, possibly after waking up from suspend. Sound was enabled everywhere:
[LIST]
[*]VLC main sound volume
[*]VLC sound enabled
[*]Sound settings application specific volume
[*]System sound level + mute
[/LIST]

**Failed Solutions**
[LIST]
[*]VLC: change sound volume
[*]VLC: mute and unmute
[*]VLC: jump in the video
[*]VLC: jump to next video in playlist
[*]VLC: disable and enable audio
[*]VLC: cycle between audio channels left, right, reversed, and back to normal
[*]Mute and unmute VLC as an application in sound settings
[*]Change sound level for VLC in system settings
[*]Uninstall VLC and reinstall
[*]Purge VLC and reinstall
[*]Reset VLC configuration
[*]Reboot whole system
[/LIST]

**Solution**
Go to settings "Sound -> Play sound through". Change "analog output" to "digital output" and back. VLC sound is back and all other apps have sound as well.

**Environment**
[LIST]
[*]Ubuntu 14.04 LTS 64 bit
[*]VLC 2.1.4 Rincewind (2.1.4-0ubuntu14.04.1 in apt repo)
[*]Linux computername 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[/LIST]

---

### Post by TheFu on 2015-01-02
I've seen this myself and have been switching to "direct hardware device with full software conversions" to get it working.  Never tried switching back.

Good tip, regardless. Hopefully it will work for others.

---

