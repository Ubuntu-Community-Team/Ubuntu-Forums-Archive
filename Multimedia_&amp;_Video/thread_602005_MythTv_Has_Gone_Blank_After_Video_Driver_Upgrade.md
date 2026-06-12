---
title: "MythTv Has Gone Blank After Video Driver Upgrade"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by bper on 2007-11-03
Greetings.

When I saw the compiz update, I downloaded and installed them. I also downloaded and installed the nvidia-glx-new restricted driver.

To my delight, I was able to get a higher resolution on my display, but wasn't successful with compiz.

First, the display was off the screen and I couldn't read it. But after rebooting a few times, it seemed to eventually display correctly. The only thing was that my MythTv displayed live tv in 4:3 when it used to fit across my widescreen monitor. So I tried to change the aspect ratio from 4:3 to 16:9.

I did that in MythTv-> Setup -> TV Settings -> Recording Profiles -> Software Encoders -> Live TV, Default, High Quality, Low Quality.

After doing that, then attempting to 'Watch TV', all I get is a blank screen, no audio, and eventually I get back to the MythTV menu. I went back and undid my changes, putting the aspect ratio back to 4:3, but it's still blank.

How can I resolve this now? Thanks.

---

### Post by bper on 2007-11-05
Greetings again.

Attached is the output from dmesg. Maybe something raises a flag. Any help would be appreciated. 

Thanks.

---

### Post by bper on 2007-11-12
Still waiting for any help that anyone can give.

I found some info in the mythtv log file:

2007-11-12 20:06:45.008 MainServer::HandleAnnounce Monitor
2007-11-12 20:06:45.017 adding: Hosana as a client (events: 0)
2007-11-12 20:06:45.018 MainServer::HandleAnnounce Monitor
2007-11-12 20:06:45.053 adding: Hosana as a client (events: 1)
2007-11-12 20:06:45.077 MainServer::HandleAnnounce Playback
2007-11-12 20:06:45.094 adding: Hosana as a client (events: 0)
2007-11-12 20:06:45.104 TVRec(1): Changing from None to WatchingLiveTV
2007-11-12 20:06:45.108 TVRec(1): HW Tuner: 1->1
2007-11-12 20:06:45.479 MPEGRec(/dev/video0) Error: Error getting codec params u
sing old IVTV ioctl
                        eno: Bad address (14)
2007-11-12 20:06:45.486 MPEGRec(/dev/video0) Warning: MPEG Layer1 does not work 
properly with ivtv driver. 
                        Using MPEG layer 2 audio instead.
2007-11-12 20:06:45.486 MPEGRec(/dev/video0) Error: Could not set MPEG controls 
2 through 0.
                        eno: Numerical result out of range (34)
2007-11-12 20:07:31.984 TVRec(1): Changing from WatchingLiveTV to None
2007-11-12 20:07:32.063 Finished recording Unknown: channel 1068
2007-11-12 20:10:25.972 Expiring Unknown from Mon Nov 12 20:06:45 2007, 0 MBytes
, forced expire (LiveTV recording)

Thanks.

---

