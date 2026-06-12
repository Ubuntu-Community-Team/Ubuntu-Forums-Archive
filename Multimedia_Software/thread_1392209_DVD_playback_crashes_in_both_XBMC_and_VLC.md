---
title: "DVD playback crashes in both XBMC and VLC"
date: 2010-01-27
forum: Multimedia Software
---

### Post by clconway on 2010-01-27
I'm having a recurring problem with DVD playback and I have no idea if it the hardware, the drivers, or the decoding libraries are to blame. I'm looking for any advice on how to debug this.

This happened most recently the other day with a Netflix rental. Several seconds into the main feature, playback just stopped and returned to the XBMC Main Menu. This happened once, I quit XBMC and turned on debugging, then it happened again in exactly the same place (log:  [http://pastebin.ca/1764610](http://pastebin.ca/1764610)). Then I opened the disc in VLC; it playback stopped in the same place.

I rebooted and tried again. Playback got a bit farther, but not more than a few seconds (log:  [http://pastebin.ca/1764618](http://pastebin.ca/1764618)).

This has happened many times with many different discs, usually Netflix rentals. It doesn't always happen in the first few seconds of the main feature: sometimes it happens before the main screen even loads; sometimes it happens twenty minutes in.

If I rip an ISO with Brasero, I am able to watch the movie without any similar crashes. This was the case with the movie above. Here's a log of playing the first minute or so without error:  [http://pastebin.ca/1764626](http://pastebin.ca/1764626).

Sometimes, if I set the disc aside and try the next day, it will play with no problem.

I actually replaced my DVD drive because I thought it might be the problem, but the same thing is happening with the new drive (same model, replacement-only warranty).

Any ideas?

Details:

Distro: Mythbuntu 9.10
Kernel: 2.6.31-17-generic-pae
CPU: Athlon 64 X2 5200+ 1.0GHz
XBMC version: 1:9.11-karmic1 (SVN rev: 26018)
VLC version: 1.0.4-1~getdeb2
GPU: GeForce 8200
NVIDIA driver: 190.53-0ubuntu1~karmic~nvidiavdpauppa8
Video resolution: 1900x1080
DVD drive: Sony Optiarc AD-7240S-0B

---

### Post by clconway on 2010-01-31
This happened again last night. Here's a crash log: [http://pastebin.ca/1773659](http://pastebin.ca/1773659)
I also got a debug log from VLC: [http://pastebin.ca/1773684](http://pastebin.ca/1773684)
In this case playback from the ISO was no better.

The problem seems to always be heralded by the error log:
> ERROR: Error getting next block: Error reading from DVD.


My best guess at this point is that my drive or driver just can't handle any scratches or skips during playback --- that would explain why this mostly happens with rental discs that have some wear and tear on them. Are there settings I can tweak to make playback more fault tolerant? Is this likely to be a flaw in the drive itself, so that getting a replacement or buying a different model might solve the problem?

---

### Post by FreezWay on 2010-01-31
[http://linux.about.com/od/ubuntu_doc/a/ubudg34t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg34t2.htm)

---

### Post by clconway on 2010-01-31
> **FreezWay said:**
> [http://linux.about.com/od/ubuntu_doc/a/ubudg34t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg34t2.htm)

I've got libdvdcss2 installed from Medibuntu.

---

