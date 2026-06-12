---
title: "Flash, Youtube, Fullscreen and White Bars"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Clappy on 2008-07-29
I'm having more fullscreen troubles. Certain websites with flash videos such as youtube.com, when fullscreened, they remain small with white bars on the top and bottom filling the rest of the screen.

This happens on my TV-out (1024x768) and my Samsung (1600x1050). I am using Hardy Heron 8.04, flash-nonfree, and I have an Nvidia video card using twinview (w/ xinerama?)

I found a post on the youtube forums with one other person having this issue (no resolution) and a commenter mentioned this being an issue related to Xinerama, or poor code from certain flashvid sites. I can't imagine it being the latter, otherwise more people would be reporting it.

The weird thing is, it's not all flash sites, in fact it's only Youtube that has the problem, but since I use youtube quite a bit I'd like to try and get this working right. Does anyone have any ideas? Do you need more information? Let me know please. Thanks!

---

### Post by Charbs on 2008-09-23
Im having the exact same problem. Youtube has the white bars on top and bottom of fullscreen mode. 

Im using a dual display Nvidia card with Xinerama. 

Anyone found a fix for this yet?

---

### Post by ehoffman on 2008-09-29
This may be more generalized.

Everywhere I look for people reporting this problem, they all have dual screen and Firefox3.  I'm not sure, but they may also have x64 in common.

Mozilla forum: [http://support.mozilla.com/tiki-view_forum_thread.php?locale=lt&comments_parentId=123871&forumId=1]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=lt&comments_parentId=123871&forumId=1")

---

### Post by not-a-bot on 2008-10-26
I'm running Intrepid Ibex, flashplugin-nonfree and using a dual-monitor setup on an Ati X1900 and I'm experiencing the exact same problem.
Fullscreen only on the main display, huge white bars on top and bottom an a middle area that appears to have the same aspect ratio as both monitors combined.

Does anyone have a solution or workaround for this yet?

---

### Post by godvalve on 2008-11-10
This is still a problem in 8.10. Anyone have any ideas?

(It seems to me, based on my observation of a number of other programs including OpenOffice, Code::Blocks, and Quake4, that Ubuntu (on the NVidia restricted drivers using TwinView) returns a fullscreen value that combines the resolution from both monitors into one resolution. Ergo, when the YouTube player receives this combined value as the fullscreen resolution, the video is adjusted accordingly. The problem seems to come back to the fact that Ubuntu / firefox contains the fullscreen video to one screen and so the fullscreen player is readjusted to fit on the screen. This results in the large white bars top and bottom.

The question is, how can this be remedied?

---

### Post by not-a-bot on 2008-11-10
This is not limited to the nvidia drivers but also happens with ati's fglrx drivers as well. It seems to be related to the way Ubuntu treats multi-monitor setups now.

---

### Post by justin92089 on 2008-11-10
A total shot in the dark, but I was having a similar issue at youtube after updating to the newest version of Flash, and what fixed it for me was right-clicking on the actual video, clicking settings, and then un-checking "enable hardware acceleration."  Though this was on an hp pavilion laptop running windows 2000 and firefox 3.  But all the same, I was having the exact same issue and it fixed it.

---

### Post by levelnext on 2008-12-07
same probleme here, hardy 64 bit.

---

### Post by lionbeast on 2008-12-08
same problem but the stripes are on each side of the video. 

i use intrepid with nvidia settings. dual screen.

and i have a 32 bit so it's not just related to 64 bit version. 

is there really nobody who knows how to fix this....

---

### Post by ProfKaramba on 2008-12-22
same problem here.

NVIDIA 7900GT, AMD64bits and ubuntu 8.10

---

### Post by bencoder on 2009-01-16
Hi I have the same problem, 8.10 NVidia 8300GS with twinview and different aspects on each monitor(16:10 and 4:3). One difference is that I get black bars rather than white, at the top and bottom.

I think this might actually be poor coding of the youtube video player, because dailymotion's full screen mode works fine.

Would be good if there was some work around, I've tried some of the hints here but no luck.

---

### Post by dageng1 on 2009-01-16
I am currently running Arch Linux x64, but had the same problem with Ubuntu 8.04/8.10, and also with Arch Linux. I also have a TwinView setup with two monitors with different aspects. My bars are also black. I'm hoping for a solution to this, as watching YouTube vidoes in "HD" quality just isn't the same when the display area is so limited.

I've got a Nvidia 8800GT 512MB card.

---

### Post by Pasdar on 2009-04-12
I have the same issue, first I had black bars, then white bars, and now black bars again. I have a GeForce 6200 and also have TwinView enabled.

Ubuntu 9.04

---

### Post by mynameisfiber on 2009-06-13
I have the same issue.  Dual screen with my Nvidia 9600 GT on 9.04.  I have twinview enabled with a total resolution of 2944 x 1080.

---

### Post by michal6103 on 2009-06-16
same problem

Jaunty
ATI fglrx dual screen
adobe flash

---

### Post by echofloripa on 2009-07-08
I got the same problem here, twin video, last ubuntu version. I have this problem for a long time. Google video works alright though.

---

### Post by yemu on 2010-12-16
the problem still persists :(
radeon 4850 with radeon driver - with fglrx youtube is ok. unfortunately I can't use fglrx because of vsync problems :(

---

