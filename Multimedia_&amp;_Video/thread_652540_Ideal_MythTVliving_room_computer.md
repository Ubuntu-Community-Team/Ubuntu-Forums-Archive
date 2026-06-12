---
title: "Ideal MythTV/living room computer?"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by 50words on 2007-12-28
I am shopping for a MythTV/living room computer. This will be used for MythTV as well as checking Gmail and browsing the internet (especially for TV shows available online). Nothing fancy. I plan to get a ReadyNAS network-attached hard drive bank to hold ripped DVDs, music, etc., so the hard drive size is not particularly important.

I will be using a regular TV for now, and a sweet sweet LCD or Plasma at some point.

I am looking at System76's Koala Mini, but I am concerned about the graphics card. Don't I want something a bit stronger to drive my television? Or doesn't it really matter?

If not the Koala Mini, what are other good options? A Mac Mini running Ubuntu? Something else?

---

### Post by empthollow on 2007-12-28
i think you do want something with a little more power.  more importantly you may want to look into some kind of a video out.  i'm not sure if that box has any out other than for a monitor.  probably want a card with a svideo out.  the other very important feature you need in a mythtv box is a video input card.  it can be composite in if you have a cable box or converter box but otherwise you would want to have a tv tuner card with a coax jack on it.  a downside to this mini is that it is not upgradable.  there are usb tv tuners, generally speaking usb is not meant for devices with constant connection but it does work i.e. wireless usb cards. the points i would pay attention to are video card, tv out, and video input.  the rest is just running the os.  you want it to be fast enough to keep up with the video but most computers out there can do that.

---

### Post by 50words on 2007-12-29
So the Intel 945 graphics card is enough, or not? The Koala Mini has S-video out, but it sounds like I would need something else if I want to use the PVR features of MythTV.

---

### Post by leg on 2007-12-29
Have a look at [mini-itx ]("http://www.mini-itx.com/")and consider building your own. I am fairly sure that the mythtv site has a [list of specs]("http://www.mythtv.org/docs/mythtv-HOWTO-3.html#video_capture_device") that will work well. They seem to like hauppage cards (especially the pvr 350 ) but most importantly you should select a card with hardware based mpeg-2 encoding and support xvideo extensions.

---

### Post by Joe Jarvis on 2008-01-01
> **50words said:**
> So the Intel 945 graphics card is enough, or not?

I'd go with a 965 solution.  It's has the first Intel on-board graphics capable of resolutions up to 1080p60.  I've had some success with the Intel DG965WHMKR motherboard, which is reasonably inexpensive.  It contains the 965's graphics, on-board Intel gigabit ethernet, and digital optical out (S/PDIF) for connection to a receiver; better yet, Intel-supported open-source drivers exist for all three.  It also has 6 SATA II ports if you want to make a NAS/array.  I have a server in a bedroom based on this board with pcHDTV tuners and a RAID5 array and a client based on this board in my living room, and have been happy with both.  The Intel solutions also allow ADD2 cards, like the Prolink CH7315, which should in theory allow you to add an HDMI out port for <$50.  HTH.

---

