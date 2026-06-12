---
title: "mythbuntu VDPAU MKV lagging / buffer issue"
date: 2014-01-14
forum: Mythbuntu
---

### Post by EternalStudent on 2014-01-14
I am running mythtv .27 on mythbuntu 12.04.  I have a Nvidia gt 630 with 2G rm (384 cuda cores) which works nicely.  
I'm using VDPAU high quality settings, but still seem to have a lagging issue.
the issue always occurs with MKV files. It happens most often in panning landscape scenes.

It seems i'm pegging the buffer during playback.  it's constantly up at 99%.

During MKV Playback options in the interval player settings it displays Available Buffer 99% of 4MB

According to this, I shouldn't have this problem with MKV.  This is a combined backend/frontend.  Could it be the local file designation overwrites the MKV setting?

[http://www.mythtv.org/wiki/Release_Notes_-_0.25](http://www.mythtv.org/wiki/Release_Notes_-_0.25)

> Make the ringbuffer size dynamic [bff8594]


    4MB for local files (unchanged)
    8MB-16MB for network playback
    16MB-32MB for matroska files and files with unknown bitrates 


Thanks for the help

---

### Post by tgm4883 on 2014-01-14
> **EternalStudent said:**
> I am running mythtv .27 on mythbuntu 12.04.  I have a Nvidia gt 630 with 2G rm (384 cuda cores) which works nicely.  
I'm using VDPAU high quality settings, but still seem to have a lagging issue.
the issue always occurs with MKV files. It happens most often in panning landscape scenes.

It seems i'm pegging the buffer during playback.  it's constantly up at 99%.

During MKV Playback options in the interval player settings it displays Available Buffer 99% of 4MB

According to this, I shouldn't have this problem with MKV.  This is a combined backend/frontend.  Could it be the local file designation overwrites the MKV setting?

[http://www.mythtv.org/wiki/Release_Notes_-_0.25](http://www.mythtv.org/wiki/Release_Notes_-_0.25)



Thanks for the help

No.


You aren't "pegging the buffer". In an ideal situation, your buffer would be full. What you just said was your buffer is empty, meaning that for whatever reason, your computer isn't fast enough to fill the buffer. Could be CPU speed, disk speed, network speed (although it sounds like it's a local file). Basically, the path the video takes to the display looks like this (for local playback).

Hard Disk -> RAM (buffer) -> Display

You can see that having a full buffer would be better, as there would be more video in RAM (Fast). Somewhere on your system the process for getting it from hard disk to RAM is slow.

---

### Post by EternalStudent on 2014-01-14
Thanks, tgm.  That makes a lot of sense.  I'll play around when I get home tonight.  This is the disk the file is on:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136351](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136351)
I would think that would be ok.  I'll run a performance test on HD.  

I wonder if there is something with the bus / cable.

I'll report back what I find.

Thanks again!

---

### Post by EternalStudent on 2014-01-14
OK.  So here are more details. 
fdisk -l readout

```
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2010


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930276351  1465137152   83  Linux



```

I don't think the drive is the problem:
[ATTACH=CONFIG]249508[/ATTACH]

 I copied more information down about the video playback because I'm wondering if it's a buffer problem now.  

storage to buffer: > 1Gbps
Buffer to Decoder: 18-22 Mbps
Available Buffer: 97-99%
Video: 1920x1080@23.98fps
codec: H.264
Decoder: vdpau
FPS: 23.98


Any ideas what else may be causing the lag during playback? 

Thanks!

---

### Post by tuat2 on 2014-01-14
I've also had a similar issue. It turned out it was an issue with the nvidia driver.

But before I found out that the driver was the real cause, I switched to "high quality" and from openGL to QT, which also removed the lags I had.

---

### Post by EternalStudent on 2014-01-15
Any other suggestions?  I tried basically every option for video playback in the frontend setup and still have lag.  most were worse than VPDAU.  Going to high quality or some others, just use more CPU. I've got a 4 core processor and did not peg any of the cores during High quality playback.

I also noticed one of the movies i have issues with is Codec: H.264, but not all of them are.  One is VC-1.  

Thanks.

---

### Post by EternalStudent on 2014-01-17
Got it!  Crazy issue was with my TV!  Samsung auto motion plus.  Before the upgrade I used the VGA connection.  The TV defaults to different settings than after I upgraded to HDMI.  So I modified the auto motion plus setting to Clear setting (low blur reduction and high judder reduction - I learned after a quick internet search).  that fixed the issue.  I think High blur reduction was actually overcompensating....
Thanks for the help.

---

