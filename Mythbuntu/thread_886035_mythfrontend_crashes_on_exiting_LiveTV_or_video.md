---
title: "mythfrontend crashes on exiting LiveTV or video"
date: 2008-08-10
forum: Mythbuntu
---

### Post by nelsonmuntz on 2008-08-10
Whenever I exit LiveTV (or occasionally the viewing of a video), mythfrontend shuts down without so much as a peep. I've checked the mythfrontend.log file and have not found anything untoward. These are the last entries:


```
2008-08-10 23:25:20.568 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2008-08-10 23:25:20.614 OSD Theme Dimensions W: 640 H: 480
2008-08-10 23:25:20.812 TV: Changing from None to WatchingLiveTV
2008-08-10 23:25:20.813 New DB connection, total: 3
2008-08-10 23:25:20.814 Connected to database 'mythconverg' at host: localhost
2008-08-10 23:25:20.815 Realtime priority would require SUID as root.
2008-08-10 23:25:20.818 FilterManager: failed to load filter 'none', no such filter exists
2008-08-10 23:25:20.818 Couldn't load deinterlace filter none
2008-08-10 23:25:20.852 Video timing method: USleep with busy wait
2008-08-10 23:25:22.722 NVP: prebuffering pause
2008-08-10 23:25:22.723 WriteAudio: buffer underrun
2008-08-10 23:25:27.235 NVP: prebuffering pause
2008-08-10 23:25:27.236 WriteAudio: buffer underrun
2008-08-10 23:25:29.010 TV: Attempting to change from WatchingLiveTV to None
2008-08-10 23:25:29.342 TV: Changing from WatchingLiveTV to None

```

I was also getting a subsequent line saying 'DPMS Reactivated'. I tried removing DPMS from xorg.conf (I don't need it anyway) and this line no longer appears in the log, but the problem remains the same.

Anybody encountered something like this?

I'm using Mythbuntu 8.04 and an ATI Radeon HD 3450 based graphics card.

Cheers,
Nelson

---

### Post by JugeHuge on 2008-08-11
Hello..

I have same problem with ATI HD3200 and i haven't found solution on it. 

I think this is ATI driver related issue. All posts what i have found regarding this issue had always ATI graphics card in their setup.

---

### Post by thebitpit on 2008-10-16
I have an ASUS ATI 3450 based card.I noticed that you are using:

*2008-08-10 23:25:20.852 Video timing method: USleep with busy wait*

on your front end. I don't know if this will solve your problem, but you might try to enable RTC video timing. I have seen references to a special mythbuntu contol panel setting, but since I use gentoo I don't know where it is. I set it like this:

**sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq**


For realtime priority you may also need to make /dev/rtc look like this:

**crw-rw-r-- 1 root audio**

These bits helped my mythtv system run better.

---

### Post by dougie173 on 2009-04-03
I tried last night to use the on board ATI driver on my motherboard, to try and free up a PCI slot so I can put a second tuner card in my myth box.

I didn't had time to test or try and diagnose the fault but have you tried running myth in debug.

You can do this by starting myth from a terminal with the following command

```
mythfrontend --verbose all 
```

You should output this to a file as it produces a LOT of output.

---

