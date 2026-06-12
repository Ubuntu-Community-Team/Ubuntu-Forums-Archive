---
title: "PVR 350 capture settings?"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by mikeon on 2007-07-23
Hi,
I have my PVR 350 video cature card working well with ubuntu 7.04.

I am capturing video from a VHS player on the composite video input with cat /dev/video0 >> file.mpg. The resulting mpeg2 file is around 2.5 to 3GB per hour. I'm just saving the resulting file to a DVD+R without any menu creation or chapters etc. I just use GOPChop to trim the start and finish.

My problem is that I struggle to get even 80mins on to a single layer dvd and many of the VHS cassettes I am converting are typically 90 - 120 minutes. My blank dvds are 4.7 or "120 minute", is this "120 minute" just a marketing gimmick as at up to 3GB/hr in my case it's just not possible!

Now finally my question, does converting mpeg2 to a dvd iso add some more compression to allow more time than a plain mpeg2? If not then what settings can I use to capture directly from the PVR350 at a lower bitrate? I am reluctant to re-encode the file to another format as my machine is not the fastest. 
BTW, I capture in PAL (european) 720x576. I know for VHS quality this is overkill so I'd like if possible to capture directly such that 2 hours of video would be no more than 4GB but still play on a normal dvd player. I use the ivtv driver with V4l2-ctl and ivtvctl command line to change settings.

Any suggestions? Thanks.

---

