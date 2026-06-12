---
title: "HDPVR, MythBuntu 9.10 Stops Recording"
date: 2009-11-23
forum: Mythbuntu
---

### Post by drumz on 2009-11-23
I'm finally trying to go HD with my myth setup that has worked for years.  Today I connected my Hauppauge HD-PVR and as a first test used mplayer to playback the video straight from /dev/video1.  It worked for a few minutes then froze - and at the same time the top blue led 'lid' turned off.  Stopping/restarting mplayer it did the same thing.

If I try 'cat /dev/video1 > foo' it'll record roughly 14-15MB of data and then stop.  Killing the cat process and doing it again yields the same results.  Trying the same thing on my laptop it works fine, I let it record for a while without any problems.

Both my server and my laptop are running Ubuntu 9.10, patched to the same everything.  The only difference is the server is a dual CPU AMD Opteron setup - which has been absolutely rock solid for years.  I see no heavy CPU or disk I/O load on the server so it appears to be handling recording fine - until the HDPVR decides to 'just stop' for some reason.

Looking at the logs on the server shows me nothing, there's no indications of any problems.  The hd-pvr simply stops.  I've even gone so far as removing my PVR350 card from the server thinking there may have been some type of conflict but that didn't change the results.

/var/log/message output is below.  It should be noted that in /etc/modprobe.d/option.conf I have the HDPVR set to appear as video3 so the 'video9' below is actually not correct:
```

Nov 23 09:55:45 executor kernel: [  307.957582] usbcore: registered new interface driver hdpvr
Nov 23 09:56:00 executor kernel: [  322.592026] usb 2-3: new full speed USB device using ohci_hcd and address 3
Nov 23 09:56:00 executor kernel: [  322.832414] usb 2-3: configuration #1 chosen from 1 choice
Nov 23 09:56:00 executor kernel: [  323.036267] hdpvr 2-3:1.0: untested firmware version 0x12, the driver might not work
Nov 23 09:56:01 executor kernel: [  323.417705] hdpvr 2-3:1.0: device now attached to /dev/video9
Nov 23 10:03:04 executor kernel: [  746.574472] usb 2-3: USB disconnect, address 3
Nov 23 10:03:04 executor kernel: [  746.688075] hdpvr 2-3:1.0: device /dev/video9 disconnected
```


I also enabled debug output on the hdpvr kernel module.  Below is what you see in /var/log/debug.  At the end it just freezes until I stop mplayer or cat and then it outputs the 'transmit worker exited' line.

```
Nov 23 09:56:00 executor kernel: [  323.144236] hdpvr 2-3:1.0: magic request returned 8
Nov 23 09:56:01 executor kernel: [  323.169220] hdpvr 2-3:1.0: config call request for value 0x1700 returned 1
Nov 23 09:56:01 executor kernel: [  323.192214] hdpvr 2-3:1.0: config call request for value 0x1500 returned 1
Nov 23 09:56:01 executor kernel: [  323.237207] hdpvr 2-3:1.0: config call request for value 0x1200 returned 1
Nov 23 09:56:01 executor kernel: [  323.261204] hdpvr 2-3:1.0: config call request for value 0x1300 returned 1
Nov 23 09:56:01 executor kernel: [  323.285199] hdpvr 2-3:1.0: config call request for value 0x2900 returned 1
Nov 23 09:56:01 executor kernel: [  323.308196] hdpvr 2-3:1.0: config call request for value 0x2a00 returned 1
Nov 23 09:56:01 executor kernel: [  323.332191] hdpvr 2-3:1.0: config call request for value 0x2b00 returned 1
Nov 23 09:56:01 executor kernel: [  323.356188] hdpvr 2-3:1.0: config call request for value 0x2c00 returned 1
Nov 23 09:56:01 executor kernel: [  323.381182] hdpvr 2-3:1.0: config call request for value 0x2d00 returned 1
Nov 23 09:56:01 executor kernel: [  323.391181] hdpvr 2-3:1.0: control request returned 4
Nov 23 09:56:01 executor kernel: [  323.397183] hdpvr 2-3:1.0: no valid video signal or device init failed
Nov 23 09:56:01 executor kernel: [  323.407172] hdpvr 2-3:1.0: control request returned 1
Nov 23 09:56:01 executor kernel: [  323.417177] hdpvr 2-3:1.0: control request returned 1
Nov 23 09:56:01 executor kernel: [  323.417180] hdpvr 2-3:1.0: allocating 64 buffers
Nov 23 09:56:43 executor kernel: [  365.216438] hdpvr 2-3:1.0: video signal: 1280x720@60hz
Nov 23 09:56:46 executor kernel: [  368.755307] hdpvr 2-3:1.0: encoder start control request returned 0
Nov 23 09:56:46 executor kernel: [  368.956531] hdpvr 2-3:1.0: config call request for value 0x700 returned 1
Nov 23 09:56:46 executor kernel: [  368.956545] hdpvr 2-3:1.0: streaming started
Nov 23 09:56:46 executor kernel: [  368.956557] hdpvr 2-3:1.0: hdpvr_read:438 buffer stat: 64 free, 0 proc
Nov 23 09:56:46 executor kernel: [  368.956652] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  368.992558] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:46 executor kernel: [  368.992579] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  369.010535] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:46 executor kernel: [  369.010568] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  369.011029] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:46 executor kernel: [  369.011064] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  369.019831] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:46 executor kernel: [  369.019854] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  369.050662] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:46 executor kernel: [  369.050682] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 2 free, 62 proc
Nov 23 09:56:46 executor kernel: [  369.050692] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  369.056808] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:46 executor kernel: [  369.056830] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:46 executor kernel: [  369.066802] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
...
...
...
Nov 23 09:56:51 executor kernel: [  373.183165] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.194149] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:51 executor kernel: [  373.194176] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.203136] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:51 executor kernel: [  373.203162] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.213136] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:51 executor kernel: [  373.213159] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.236039] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:51 executor kernel: [  373.236202] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 2 free, 62 proc
Nov 23 09:56:51 executor kernel: [  373.236217] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.244122] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:51 executor kernel: [  373.244133] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.259127] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:56:51 executor kernel: [  373.259137] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:56:51 executor kernel: [  373.269119] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
...
...
...
Nov 23 09:57:04 executor kernel: [  386.362010] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:57:04 executor kernel: [  386.362032] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:57:04 executor kernel: [  386.372010] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:57:04 executor kernel: [  386.372034] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:57:04 executor kernel: [  386.382018] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:57:04 executor kernel: [  386.382040] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:57:04 executor kernel: [  386.392003] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:57:04 executor kernel: [  386.392028] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:57:04 executor kernel: [  386.401004] hdpvr 2-3:1.0: hdpvr_read:498 buffer stat: 1 free, 63 proc
Nov 23 09:57:04 executor kernel: [  386.401026] hdpvr 2-3:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
Nov 23 09:57:10 executor kernel: [  393.120959] hdpvr 2-3:1.0: config call request for value 0x800 returned 1
Nov 23 09:57:10 executor kernel: [  393.120986] hdpvr 2-3:1.0: transmit worker exited
Nov 23 09:57:12 executor kernel: [  394.488700] hdpvr 2-3:1.0: used 0 urbs to empty device buffers

```

---

### Post by drumz on 2009-11-24
Not finding any similar posts online, I re-started troubleshooting from the ground up.  Dropping down to looking at complete basics re-looked up the specs for my mobo and despite what I thought it doesn't support the needed USB 2.0 the HD-PVR requires.  Thought it was new enough but apparently not.

Now to find a new mobo.....

---

