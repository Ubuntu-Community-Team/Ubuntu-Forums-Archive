---
title: "Nvidia 210 - No video"
date: 2010-05-19
forum: Multimedia Software
---

### Post by joshedmonds on 2010-05-19
I recently installed an Nvidia 210 graphics card on a system running 10.04, and the proprietary drivers installed without issue (v195.36.15), Compiz and gaming working well, but no video!

I have a 1280x1024 LCD connected to the VGA output, and if I play a video file (any format, multiple players including VLC) the player progresses the time, the sound works, but no image is displayed in the player window. Any ideas?

---

### Post by joshedmonds on 2010-05-20
I have found some possibly related information for other 210 users out there (n.b. I'm not using XBMC)

Bug report for failure to render xvid using vdpau in XBMC:
[http://trac.xbmc.org/ticket/8337]("http://trac.xbmc.org/ticket/8337")

Forum discussion that led me to that bug:
[http://forum.xbmc.org/showthread.php?p=499866]("http://forum.xbmc.org/showthread.php?p=499866")

I installed package libvdpau1 with no results.

---

### Post by dckrooney on 2010-05-20
I had similar issues to what you're describing, also with a 210.

I'm currently using the nouveau drivers provided by 10.04, but under 9.10 I was using the proprietary ones. 

Here's how I got video playback to work for me:

First I installed libvdpau1 (as you mentioned). Then I installed SMplayer (which gives you more options over video output than Mplayer) from the Software Center.

Next, go to Options->Preferences->General->Video and change the "Video Driver" to vdpau (I think it's set at "user defined" by default).

After that, everything seemed to work cleanly. 

Hope this helps :P

---

### Post by joshedmonds on 2010-05-21
Many thanks dckrooney, that works for playback with SMPlayer. Hopefully other 210 users (and possibly other Nvidia driver users) can benefit from this workaround.

I found several similar bugs in Launchpad against particular players (VLC and MPlayer), and based on the workaround and descriptions of those bugs the issue is player specific.

---

### Post by epictetus on 2010-12-10
Thanks for the work-around! I was having the same problem with the GT 240 on Ubuntu 10.10, but this lets me watch video again.

---

### Post by joshedmonds on 2010-12-10
It's interesting that you had that problem on 10.10, as I reinstalled 10.04 a little while ago (with Nvidia drivers, but sans libvdpau and SMPlayer) and video seems to be working fine in Totem.

---

