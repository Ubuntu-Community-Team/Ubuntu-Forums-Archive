---
title: "9500 GT Questions"
date: 2009-05-14
forum: Mythbuntu
---

### Post by chip33az on 2009-05-14
Hi,

I just put together a new computer with an AMD 4850e and a Nvidia GeForce 9500 GT.  I thought I'd give Mythbuntu 9.04 (64-bit) a try since this is my first 64-bit machine.  I'm borrowing a friend's AverMedia 1500 to use as the TV tuner.

Everything installed with no issues, but I don't think the video is working as well as it should.  I have the TV out working fine, but every once in a while while watching a movie the video will skip a second.  Also, the sound during playback of TV recordings becomes off (stopping and starting the recording typically fixes this).

Should XVMC be loading for the 9500 GT? 

I haven't used MythTV in a very long time and the new playback screen is completely different.  How do I know what to enter?  Is there a good guide to this somewhere?

---

### Post by ian dobson on 2009-05-14
Hi,

If possible use XVMC, hardware acceleration is always better than software. 

On my frontend system I can playback SD video on a Core2Duo running at 1200MHz an a 9300GT with only about 5-10% CPU load.

If your being really "on the edge" try using the VDPAU backport and have hardware supported HD playback.

The configuration for HW support is under Configuration,TV,Playback or something like that.

Regards
Ian Dobson

---

### Post by chip33az on 2009-05-14
Thanks.  For some reason I thought the 9xxx version didn't support XVMC.  I looked to see if XVMC is started on my server and it doesn't look like it.

This weekend, I'll try the VDPAU, what the heck!

---

### Post by ian dobson on 2009-05-14
Hi,

Looks as if your right about xvmc, looking at my backend log it seems that mythtv is using another renderer without telling me.


```
2009-05-15 05:32:26.159 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,vdpau,xlib,' available, using 'xv-blit' instead.
2009-05-15 05:32:26.163 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-15 05:32:26.197 VideoOutputXv: Ack! Disabling ChromaKey OSD
                        We can't use ChromaKey OSD if chromakeying is not supported!
2009-05-15 05:32:26.206 OSD Theme Dimensions W: 640 H: 480
2009-05-15 05:32:26.626 TV: Changing from None to WatchingPreRecorded
```

Just do a search here for VDPAU and you'll find links on how to enable a third party repositry with the backports.

Regards
Ian Dobson

---

### Post by chip33az on 2009-05-15
I did a quick try to upgrade to the VDPAU this morning and while the upgrade went fine, X doesn't start and the logs show something about the nvidia kernel driver not loading.  

Guess it is time to troubleshoot!

---

