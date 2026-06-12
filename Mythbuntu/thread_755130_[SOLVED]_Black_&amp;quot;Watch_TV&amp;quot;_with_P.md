---
title: "[SOLVED] Black &amp;quot;Watch TV&amp;quot; with PVR-350"
date: 2008-04-14
forum: Mythbuntu
---

### Post by sceo on 2008-04-14
Hey -  I just installed Mythbuntu 7.10 (tried the 8.04 beta but had some issues with it rebooting when trying to load X and not finding uPNP on boot).  It seems to be working (backend runs, frontend runs, Internet streams works, etc).

However, my Watch Live TV doesn't work.  It just goes black.  My backend log shows me:

```

2008-04-14 14:45:34.333 TVRec(1): Changing from None to WatchingLiveTV
2008-04-14 14:45:34.336 TVRec(1): HW Tuner: 1->1
2008-04-14 14:45:36.286 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-04-14 14:45:36.289 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-04-14 14:46:16.630 TVRec(1): Changing from WatchingLiveTV to None
2008-04-14 14:46:18.871 Finished recording Government Access: channel 1000

```

What's the VBI device all about?  Is this a permissions problem?

At first I had a similar error, but it additionally told me to go set up the Recording Profiles, which I did (set them to MPEG4 b/c I know the PVR-350 has an on-board MPEG encoder).  I'd like to use the onboard MPEG encoder, but NOT use the TV-Out.

I know all this hardware CAN work (at least on Debian) cuz it worked fine with Knoppmyth.  I just want to switch to Mythbuntu cuz I use Ubuntu on my regular desktop and cuz Knoppmyth doesn't upgrade with Myth as frequently (newest Knoppmyth still running .20; I intend to upgrade to .21 from backports once I can get it working with .20).

Incidentally, channel scanning appeared to work perfectly (it seemed to detect the right channels, not detect the wrong ones).

---

### Post by laga on 2008-04-14
Go to mythtv-setup, into the capture card settings and set your card as a "hardware encoder card" or something similar. Right now it's set up as a framegrabber card which is why it won't work.

---

### Post by sceo on 2008-04-15
OK, that was totally it!  Now on to my next problem... :guitar:

---

