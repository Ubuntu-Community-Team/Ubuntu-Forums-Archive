---
title: "MythTV crashes; or, how to remove nvidia drivers"
date: 2010-10-24
forum: Multimedia Software
---

### Post by Der Ritter on 2010-10-24
(Apologies that this is off-topic, but I haven't received any response from MythTV Talk and I know this forum is a lot more active.)

I'm having trouble watching 1080i HD on MythTV. Whenever I try to do so, something crashes and I end up at the login screen. 720p HD or SD video works fine. Here is the relevant log output from MythTV:

```
2010-10-24 15:44:20.554 Connected to database 'mythconverg' at host: localhost
2010-10-24 15:44:20.555 Realtime priority would require SUID as root.
2010-10-24 15:44:20.559 Video timing method: USleep with busy wait
2010-10-24 15:44:20.605 TV: Changing from None to WatchingLiveTV
2010-10-24 15:44:20.605 TV: State is LiveTV & mctx == ctx
2010-10-24 15:44:20.606 TV: UpdateOSDInput done
2010-10-24 15:44:20.607 TV: UpdateLCD done
2010-10-24 15:44:20.607 TV: ITVRestart done
2010-10-24 15:44:20.633 ScreenSaverX11Private: DPMS Deactivated 1
2010-10-24 15:44:22.563 ProgramInfo(): Updated pathname '':'' -> '1091_20101024154421.mpg'
2010-10-24 15:44:22.869 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:22.870 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:22.870 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:22.871 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.036 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.037 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.098 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.099 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.099 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.100 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.219 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.220 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.221 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:23.403 [mpeg2video @ 0x44c4120]mpeg_decode_postinit() failure
2010-10-24 15:44:25.951 AudioPulseUtil, Warning: Can not connect to sound server, can not suspend.
Connection terminated
ICE default IO error handler doing an exit(), pid = 2763, errno = 11
<unknown>: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
```I suspect it's a graphics problem, which leads me to the second part of the question. This computer is a new one that has nVidia integrated graphics. The first time I booted it up I think it used the nouveau driver and that worked fine. But something came over me and I decided I needed to install the proprietary drivers, and only after I did that did the problem with MythTV start. So if the problem cannot be fixed (a reasonable proposition) then I'd like to know how to revert to using nouveau.

---

### Post by jacksaff on 2010-10-25
I also get this crash both from my backend machine when I access the front-end (it has an nvidia card with proprietary driver) and also from my eeepc (not nvidia) when it accesses the same back-end across the network.

---

### Post by Der Ritter on 2010-10-25
After much head-banging and finally a little more Googling, I discovered [Mythbuntu bug 644835]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/644835"). The solution given there is to change playback profiles to anything that does not use XvMC. That worked perfectly for me.

---

### Post by jacksaff on 2010-11-01
Works, thanks.
Mythtv's configuration is such a mess that even after reading what to do I  still had to pull some hair...

---

