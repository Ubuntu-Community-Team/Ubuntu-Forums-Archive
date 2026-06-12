---
title: "Plextor Convertx PX-TV402U will it work 10.04"
date: 2010-04-03
forum: Mythbuntu
---

### Post by volkswagner on 2010-04-03
Well have seem to have all outdated hardware.  I have struggled in the past with my myth setup.  It has been nearly two years.  I have finally gave in and installed an nvidia card to reduce issues with my ATI X1250 onboard.

Now with a clean install of Mythbuntu 10.04, I am trying to get current hardware up.

The Plextor ConvertX PX-TV402U is listed in Mythtv .22, menu choice but does not see my device.  I am sure it is because I don't have proper drivers loaded.  After several hours of searching a bunch of dead links, I am hoping someone can tell me if it will work, and point me to the drivers.

Most of the threads on the device seem unanswered or unsolved.  It does not look good.  Even all the chatter about Gentoo guys got it working leads to dead links.

So will my kernel let it work if I can find the drivers?

```
 uname -a
Linux familyroom 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
```

---

### Post by nickrout on 2010-04-03
> **volkswagner said:**
> Well have seem to have all outdated hardware.  I have struggled in the past with my myth setup.  It has been nearly two years.  I have finally gave in and installed an nvidia card to reduce issues with my ATI X1250 onboard.

Now with a clean install of Mythbuntu 10.04, I am trying to get current hardware up.

The Plextor ConvertX PX-TV402U is listed in Mythtv .22, menu choice but does not see my device.  I am sure it is because I don't have proper drivers loaded.  After several hours of searching a bunch of dead links, I am hoping someone can tell me if it will work, and point me to the drivers.

Most of the threads on the device seem unanswered or unsolved.  It does not look good.  Even all the chatter about Gentoo guys got it working leads to dead links.

So will my kernel let it work if I can find the drivers?

```
 uname -a
Linux familyroom 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
```

what does lsusb say?

---

### Post by volkswagner on 2010-04-04
```
lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c16:0002 Gyration, Inc. 
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 093b:a004 Plextor Corp. ConvertX TV402U XLOADER
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Problem is Mythtv does not probe it.

[IMG]http://volkswagner.com/gate/MythTV.png[/IMG]

---

### Post by nickrout on 2010-04-04
> **volkswagner said:**
> ```
lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c16:0002 Gyration, Inc. 
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 093b:a004 Plextor Corp. ConvertX TV402U XLOADER
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Problem is Mythtv does not probe it.

[IMG]http://volkswagner.com/gate/MythTV.png[/IMG]

what do you mean "does not probe it"

---

### Post by volkswagner on 2010-04-04
> **nickrout said:**
> what do you mean "does not probe it"

It does not find it.  The backend only sees the PCI cards...(which shoudld not be listed under USB tuner)  If I start to edit the device field, "I get could not probe error"

This is why I included the image.

---

### Post by nickrout on 2010-04-04
> **volkswagner said:**
> It does not find it.  The backend only sees the PCI cards...(which shoudld not be listed under USB tuner)  If I start to edit the device field, "I get could not probe error"

This is why I included the image.

OK what device (if any) does the plextor advertise? boot the machine without it plugged in and do ls -l /dev/video* . then plug it in and do the same. That should tell you whether it is creating a video device. dmesg will also tell you stuff at that point.

Then try using the found video device number in mythtv-setup - use the left/right arrow keys in the video device field.

By the way do you have a PVR 350 (as the screenshot suggests?

---

### Post by volkswagner on 2010-04-04
Seems a video device is not created.

Before and after plugging in Plextor:

```
ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2010-04-04 20:32 /dev/video0
crw-rw----+ 1 root video 81, 9 2010-04-04 20:32 /dev/video1
crw-rw----+ 1 root video 81, 5 2010-04-04 20:32 /dev/video16
crw-rw----+ 1 root video 81, 3 2010-04-04 20:32 /dev/video24
crw-rw----+ 1 root video 81, 1 2010-04-04 20:32 /dev/video32
crw-rw----+ 1 root video 81, 8 2010-04-04 20:32 /dev/video48
eric@familyroom:~$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2010-04-04 20:32 /dev/video0
crw-rw----+ 1 root video 81, 9 2010-04-04 20:32 /dev/video1
crw-rw----+ 1 root video 81, 5 2010-04-04 20:32 /dev/video16
crw-rw----+ 1 root video 81, 3 2010-04-04 20:32 /dev/video24
crw-rw----+ 1 root video 81, 1 2010-04-04 20:32 /dev/video32
crw-rw----+ 1 root video 81, 8 2010-04-04 20:32 /dev/video48

```

From dmesg after plugging in Plextor:

```
[  659.350035] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  659.500618] usb 1-4: configuration #1 chosen from 1 choice
```

Yes I do have a pvr350 and a Kworld 110, which are the only probed devices under the Plextor choice.

---

### Post by nickrout on 2010-04-04
I assume you have read the wiki pages?

[http://www.mythtv.org/wiki/Plextor_PX-TV402U](http://www.mythtv.org/wiki/Plextor_PX-TV402U)

[http://www.mythtv.org/wiki/Plextor_ConvertX](http://www.mythtv.org/wiki/Plextor_ConvertX)

---

### Post by volkswagner on 2010-04-05
> **nickrout said:**
> I assume you have read the wiki pages?

[http://www.mythtv.org/wiki/Plextor_PX-TV402U](http://www.mythtv.org/wiki/Plextor_PX-TV402U)

[http://www.mythtv.org/wiki/Plextor_ConvertX](http://www.mythtv.org/wiki/Plextor_ConvertX)

Thanks for the links.  I did not land on the first link.  The second link is where I found the lack of info.

After digging through links from the wiki, it does not look good.  There has not been any work for the driver patches.  I don't want to break anything on my system, being attached to an SD TV and very difficult access, messing around with hardware and reinstalls is most annoying.

This is the reason for my question, will it work with my kernel.  

It looks like i'll need to downgrade my kernel or possible do a clean install of Jaunty.   I was really hoping to start off with a long term support system, as I said, modifying the system is a real pain with my setup.

> Patch 8 - as of 2.6.29

As of 2.6.29, the `inode` parameter has been removed from video_usercopy() in v4l2_ioctl.h. I've patched the driver to remove this, but there are a lot of deprecation warnings. The driver builds and installs but there are also many errors in the syslog, so more work is needed. It's only a matter of time before this driver needs major repair.


At least with the better wiki page I can actually land on real pages, not just get forwarded to dead pages.

Thanks for the help.

So, I must ask, does anyone have this hardware running on Kernel newer than 2.6.29?

---

### Post by nickrout on 2010-04-05
The first wiki page I linked to says > A driver for the 2.6.31 kernel can be found at the go7007.imploder.org site.

---

### Post by volkswagner on 2010-04-06
> **nickrout said:**
> The first wiki page I linked to says

Yes and I thank you for the updated links.  Still my concern is I'm running

```
2.6.32-19-generic
```

Since it seems this driver fix is specific to the kernel, I'm not confident it will work with a newer kernel without specific new build of the fix.

I will image my / partition an give it a go if nobody can confirm if it works or not.

Thanks again.

---

### Post by nickrout on 2010-04-06
> **volkswagner said:**
> Yes and I thank you for the updated links.  Still my concern is I'm running

```
2.6.32-19-generic
```

Since it seems this driver fix is specific to the kernel, I'm not confident it will work with a newer kernel without specific new build of the fix.

I will image my / partition an give it a go if nobody can confirm if it works or not.

Thanks again.

Why not run mythbuntu 9.10 then? It has a 2.6.31 kernel.

---

### Post by volkswagner on 2010-04-07
> **nickrout said:**
> Why not run mythbuntu 9.10 then? It has a 2.6.31 kernel.

With end of life for 9.10 one year away, I don't want to be in the same boat next year, cobbing together my old hardware.

I have had a difficult time getting a stable system.  If it were not for end of life, I'd be using 7.10 since it was near plug and play with my hardware.  Only updates to mythtv and ubuntu broke stuff.

So I am hoping to get 10.04 up.  I know it is beta, but the alternative for me would find a long term support distro that I can get working, even if I have to install MythTV on my own.

What sucks is I have started this project over two years ago, with short lived success.

---

### Post by nickrout on 2010-04-07
> **volkswagner said:**
> With end of life for 9.10 one year away, I don't want to be in the same boat next year, cobbing together my old hardware.

I have had a difficult time getting a stable system.  If it were not for end of life, I'd be using 7.10 since it was near plug and play with my hardware.  Only updates to mythtv and ubuntu broke stuff.

So I am hoping to get 10.04 up.  I know it is beta, but the alternative for me would find a long term support distro that I can get working, even if I have to install MythTV on my own.

What sucks is I have started this project over two years ago, with short lived success.

linhes may work, check their forums.

or get hardware with supported open source drivers.

---

### Post by cchi on 2010-05-10
Hello, I am wondering how you went here (i.e. getting your Plextor Convertx PX-TV402U working in Ubuntu 10.04 - Lucid Lynx).  I am keen to upgrade mine from 8.04 to 10.04, but its all working perfectly now in Ubuntu 8.04, so I am hesitant...  Did the driver compile, and does it work ok?  Please let us know.

I want to upgrade to 10.04 because it has other packages which I need to build my site, but I wont risk it is mythtv will go down...

---

### Post by volkswagner on 2010-05-11
I have been on and off this project.  I did get the driver to compile, with a small file edit...More on that later.

However, I can't get control of the device.  I am not sure if it is a UDEV rule to be set, or if the driver is not playing nice.  

I'll update as soon as I get more time.

---

### Post by nickrout on 2010-05-12
> **volkswagner said:**
> I have been on and off this project.  I did get the driver to compile, with a small file edit...More on that later.

However, I can't get control of the device.  I am not sure if it is a UDEV rule to be set, or if the driver is not playing nice.  


What do you mean "can't get control of the device".

---

### Post by volkswagner on 2010-05-12
> **nickrout said:**
> What do you mean "can't get control of the device".


From memory, I seem to recall that error message.

I am trying to dedicate a little time today.

I have a replacement cable box, so I am giving another go at it.

I have used gorecord to create an .avi file which had garbled sound and pixelated/choppy video.  This at least tells me It can work?

I am trying to use the Plextor via s-video, connected to my cable box for channels not avail via cable ready tuners.  In the past I used my PVR 350 for this purpose.  In the past I used the firewire channel changer, to change the channel on the cable box, when recording via s-vid to the PVR 350....worked great in the past.

With the same settings, using the plextor, I get the following errors.  Note, the firewire channel changer works great for viewing via firewire.

Backend.log
```
2010-05-12 13:42:02.064 TVRec(5): HW Tuner: 5->5
2010-05-12 13:42:02.069 ProgramInfo(): Updated pathname '':'' -> '3110_20100512134148.mpg'
2010-05-12 13:42:02.119 Channel(/dev/video1) Error: GetCurrentChannelNum(707): Failed to find Channel
2010-05-12 13:42:02.127 Channel(/dev/video1)::TuneTo(707): Error, failed to find channel.
2010-05-12 13:42:02.170 TVRec(5) Error: Failed to set channel to 702. Reverting to kState_None
2010-05-12 13:42:02.182 TVRec(5): Changing from WatchingLiveTV to None
2010-05-12 13:42:02.255 ProgramInfo(): Updated pathname '':'' -> '3110_20100512134148.mpg'
2010-05-12 13:42:29.508 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-05-12 13:42:29.538 Expiring 12 MBytes for 1002 @ Wed May 12 13:33:51 2010 => Unknown
```

OK, so now I remove the channel changer reference, and removed set channel to.  Both fields are now blank.

Now I can get live tv to view with the Plextor (yay, doesn't lock up mythfrontend).  No sound and supper slow motion video.  I may be on my wat to get this bugger working.

Now I get the following int backend.log
```
2010-05-12 14:02:48.285 TVRec(5): HW Tuner: 5->5
2010-05-12 14:02:48.354 Channel(/dev/video1) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-05-12 14:02:48.461 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:48.570 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-05-12 14:02:48.605 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
VIDIOC_S_CTRL:V4L2_CID_AUDIO_MUTE: Invalid argument
2010-05-12 14:02:48.633 ProgramInfo(): Updated pathname '':'' -> '3110_20100512140227.mpg'
2010-05-12 14:02:48.650 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.017 RecBase(5:/dev/video1): GetKeyframePositions(0,9223372036854775807,#1) out of 1
2010-05-12 14:02:49.139 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.198 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.255 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.329 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.441 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.495 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:49.508 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:02:59.599 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-05-12 14:02:59.613 Expiring 5 MBytes for 3110 @ Wed May 12 13:41:48 2010 => Unknown
2010-05-12 14:02:59.622 ProgramInfo(): Updated pathname '':'' -> '3110_20100512134148.mpg'
2010-05-12 14:02:59.689 ProgramInfo(): Updated pathname '':'' -> '3110_20100512134148.mpg'
2010-05-12 14:03:02.640 ProgramInfo(): Updated pathname '':'' -> '3110_20100512134148.mpg'
2010-05-12 14:03:49.259 ProgramInfo(): Updated pathname '':'' -> '3002_20100512140248.nuv'
2010-05-12 14:03:49.276 TVRec(5): Changing from WatchingLiveTV to None
2010-05-12 14:03:49.289 ProgramInfo(3002_20100512140248.nuv), Error: Unknown type, recording width was 0

```

Perhaps It will be better for me to switch the setup, for the PVR 350 to record via svid and set the plextor to use the tuner...what do ya'll think?

---

