---
title: "XBMC HD playback suddenly bad (nvidia)"
date: 2012-10-04
forum: Multimedia Software
---

### Post by freddybob on 2012-10-04
I've been running XBMC in Ubuntu 12.04 (64) with Unity for months and never had a problem.

In the last two or three days I've found XBMC's GUI start to become slow and unresponsive and HD playback has become stuttery.

Turning off Vertical Blank Sync within XBMC's settings fixes the GUI lag but not HD playback.

Has anyone else experienced this problem?  I'm trying to work out which updates have caused it, I see nvidia-common, jockey-common and xdiagnose were all updated this week, is one of these to blame?

---

### Post by BicyclerBoy on 2012-10-05
My HTPC does not run unity..but have used mythtv on 12.04 unity & old nVidia card.

I find that some compiz (unity) settings screw up video etc.

Debug:
check nvidia driver install by running:
- nvidia-settings ; does it report any errors
- glxgears
- vdpauinfo (works on 8200, 8400, 9400, ION (+  some IGP) & 210 or later)

How old is your card..the 6000s & 7000s have been pushed out of the latest nVidia driver >=302

Do you run XBMC full screen?
There are couple of compiz settings to try, run:
- ccsm
"tick"
- un-redirect full screen
- legacy full screen support.
mess about with:
- refresh rate detect in compiz broken (afaik with nvidia < 302)

Could be problem with XBMC...so try:
mplayer -vo vdpau -vc ffmpegvdpau some-mpeg4-layer10-video.mpg

---

### Post by freddybob on 2012-10-05
Thanks,

No obvious errors in nvidia-settings, glxgears or vdpauinfo.

It's an ION 2 with nvidia driver 295.49.

I run XBMC in fullscreen.

You are right that the problem seems to be related to Unity and/or Compiz.  

When I open and terminal and kill Unity with "metacity --replace" and then run XMBC it works beautifully. I then of course have to "unity --replace" once I drop back out of XBMC. Not ideal.

I will try playing with the CCSM options you suggested.

---

### Post by freddybob on 2012-10-05
Ticking "Unredirect Fullscreen Windows" in CCSM has fixed the problem.

Thanks very much for your help.

---

### Post by Durkslag on 2012-11-02
Thank you so extremely much!!!

My HTPC with XBMC is running so smoothly now and this problem was driving me mad until i read this thread.

---

