---
title: "ATSC with an old TV"
date: 2008-10-21
forum: Multimedia Software
---

### Post by edwinhibben on 2008-10-21
I would like to set up a Mythbuntu DVR to record broadcast shows.  I will not be using cable or satelite.  So I know that Feb 17th all NTSC will shutoff and it will only be ATSC.  So I found this cool device called HD HomeRun that can pick up ATSC signal and send them to a computer and it has two tuners which is great.  What do I need to do since I have an old tv?  Will I still need to send for a coupon to get one of the converter boxes?  Do I need to do something special in the setup so that the Mythbuntu box sends the signal to my old TV in a way that my old TV can understand?  I plan on getting a video card that has a SVideo out port and my TV does have a SVideo in port.  Any help or suggestions in this and other pitfalls I should avoid in setting up my first Mythbuntu box would be appreciated.
Thanks

---

### Post by NT4usB on 2008-10-21
If you're only going to watch recordings via MythTV (with Myth, live TV is also a recording) you won't need a coupon converter. Your computer becomes your converter box.
I don't know the HD HomeRun...
Depending on the video card you get. Nvidia, you can install nvidia-settings utility which will help you set up the S-video connection. xorg.conf can also be configured manually for the S-Video.
There's a ton of info on the web and dozens of sites dedicated to MythTV. Most every question has been asked and answered somewhere, sometime. The trick is finding them *g*

---

