---
title: "Failed to enable deinterlacing"
date: 2011-02-04
forum: Mythbuntu
---

### Post by bcg30506 on 2011-02-04
My system was working fine until I did the system updates synaptic was reporting.  Then I had issues getting my VDPAU setup working again.  I got that sorted out and am now able to watch full 1080p videos again with either mplayer or mythfrontend and use only 3-4% CPU, courtesy of NVidia. :)

However, for the 1st time ever I'm seeing an error in mythfrontend.log when watching TV that says "Failed to enable deinterlacing" even if I set it manually using the Video Scan menu while watching a video.  I can tell it is not deinterlaced now where it was before due to the tell-tale jaggies.

What could a "normal" apt-get upgrade break to make deinterlacing fail now in MythTV?  What other info would help?  I'm running 10.04 with myth-0.23.1-fixes.

Here is the relevant section from the log:
```
2011-02-04 13:01:25.865 ProgramInfo(): Updated pathname '':'' -> '1004_20110204130123.mpg'
2011-02-04 13:01:25.867 The realtime priority setting is not enabled.
2011-02-04 13:01:25.867 TV: Changing from None to WatchingLiveTV
2011-02-04 13:01:25.867 TV: State is LiveTV & mctx == ctx
2011-02-04 13:01:25.868 TV: UpdateOSDInput done
2011-02-04 13:01:25.868 TV: UpdateLCD done
2011-02-04 13:01:25.868 TV: ITVRestart done
2011-02-04 13:01:25.870 OpenGLVideoSync()
2011-02-04 13:01:25.896 [mpegvideo_vdpau @ 0x1252960]warning: first frame is no keyframe
2011-02-04 13:01:25.898 [mpegvideo_vdpau @ 0x1252960]warning: first frame is no keyframe
2011-02-04 13:01:25.947 Video timing method: SGI OpenGL
2011-02-04 13:01:25.963 Failed to enable deinterlacing
2011-02-04 13:01:25.976 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-02-04 13:01:33.373 Mixer unable to find control Master 1
2011-02-04 13:01:33.373 mixer unable to find control Master 1
2011-02-04 13:01:35.410 ProgramInfo(): Updated pathname '':'' -> '1046_20110204130134.mpg'
2011-02-04 13:01:35.442 ProgramInfo(): Updated pathname '':'' -> '1046_20110204130134.mpg'
2011-02-04 13:01:35.733 [mpegvideo_vdpau @ 0x1252960]warning: first frame is no keyframe
2011-02-04 13:01:35.734 WriteAudio: buffer underrun

```

---

### Post by bcg30506 on 2011-02-04
I figured it out.  Luckily I backup the DB before upgrading and when comparing the files from mysqldump before and after, it seems either the upgrade or my efforts to get VDPAU working again implicitly changed my deinterlacing setting to None in the playback profile without my knowledge.

I changed it back to Temporal 2x and the error went away and the picture looks good again. :guitar:

---

