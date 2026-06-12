---
title: "Channel consistently failing to record, but OK as live TV"
date: 2013-03-22
forum: Mythbuntu
---

### Post by NautiusMaximus on 2013-03-22
Hi All

I've recently found that every recording I've tried on one specific channel (5* in the UK) has failed. The recording appears to work, and a recording appears with appropriate metadata, but the recording itself is blank. Lasts for the scheduled length of the programme, but just with a blank screen and silence. A reasonably chunky mpg file gets recorded (about 900 MB for a 1-hour programme).

My first thought was that this was probably one of the endless retunes we seem to have to do on Freeview here in the UK, but in fact I can watch the channel just fine as live TV, which I assume rules out simply not being tuned into the channel, yes? Not had any problems recording any other channels.

I've checked my mythbackend log file, and it's not terribly helpful. The only error message I can find is this:

"Error: Unknown type, recording width was 544"

Any ideas how I might start troubleshooting this?

I'm using Mythbuntu 10.04.

Many thanks
NM

---

### Post by NautiusMaximus on 2013-03-22
OK, I've done a little more digging. It seems that this is a playback problem, rather than a recording problem. It turns out that the programmes did record really, and I can watch them just fine in VLC media player. But for some reason, they don't want to play back via the MythTV frontend.

Here's what my mythfrontend log looks like when I try to play back:

```
2013-03-22 16:12:52.843 Current MythTV Schema Version (DBSchemaVer): 1254
2013-03-22 16:12:52.845 ProgramInfo(): Updated pathname '':'' -> '1030_20130317225800.mpg'
2013-03-22 16:12:52.982 NVP(0): Disabling Audio, params(-1,-1,-1)
2013-03-22 16:12:53.111 Preview: Grabbed preview '/var/lib/mythtv/recordings/1030_20130317225800.mpg' 640x480@184s
2013-03-22 16:12:53.167 ~MythContext waiting for threads to exit.
2013-03-22 16:13:00.027 TV: Attempting to change from None to WatchingPreRecorded
2013-03-22 16:13:00.178 NVP(2): Disabling Audio, params(-1,-1,-1)
2013-03-22 16:13:00.363 VDPAU: Created 2 output surfaces.
2013-03-22 16:13:00.363 VDPAU: Created VDPAU render device 1280x768
2013-03-22 16:13:00.489 OSD Theme Dimensions W: 640 H: 480
2013-03-22 16:13:00.818 Realtime priority would require SUID as root.
2013-03-22 16:13:00.819 TV: Changing from None to WatchingPreRecorded
2013-03-22 16:13:00.822 Video timing method: USleep with busy wait
2013-03-22 16:13:00.825 Failed to enable deinterlacing
2013-03-22 16:13:00.827 VDPAU: Added 2 output surfaces (total 4, max 4)
2013-03-22 16:13:07.974 TV: Attempting to change from WatchingPreRecorded to None
2013-03-22 16:13:07.987 TV: Changing from WatchingPreRecorded to None
2013-03-22 16:13:21.258 Deleting UPnP client...
```

Any ideas what could be going on here?

Thanks
NM

---

### Post by klc5555 on 2013-03-22
Sometimes playback profile is the culprit in stuff like this --have you tried a few on these recordings? Particularly the non-VDPAU ones.

---

### Post by NautiusMaximus on 2013-03-23
Thanks for that suggestion, but no dice, I'm afraid. I tried all the playback profiles that were available. None of them worked.

---

### Post by PhilWig on 2013-03-23
Have you googled that deinterlace message?  Does this help?
[http://ubuntuforums.org/showthread.php?t=1681603](http://ubuntuforums.org/showthread.php?t=1681603)
Phil

---

### Post by NautiusMaximus on 2013-03-24
Thanks for that. I'm not sure whether it helps or not.

In the post you linked to, the deinterlacing setting was set to "none". My deinterlacing setting is not set to "none", it's set to "Bob (2x)". 

There are a great many other deinterlacing settings. I suppose I could try all of them to see if any of them work better than others. It does seem likely, given the "Failed to enable deinterlacing" message in the log file, that some glitch with deinterlacing could be what's causing the problem.

Does anyone have any ideas for which settings might be the most likely to be successful? Or indeed anything else I could try?

Thanks
NM

---

