---
title: "blue faces on downloaded youtube videos"
date: 2014-07-04
forum: Multimedia Software
---

### Post by merlinus on 2014-07-04
I can watch youtube videos using Opera and my nvidia card (GeForce GT-520) with correct colors after running a few terminal commands.  But when I download the videos, the faces come up blue when playing them either on movie player or banshee.

I am using the latest nvidia proprietary driver -- 331.38.  Are there any workarounds?

---

### Post by SeijiSensei on 2014-07-04
Disable VDPAU in the video players.

---

### Post by merlinus on 2014-07-04
I do not see an option for this in banshee preferences, but changing color balance: hue in movie player worked.

---

### Post by SeijiSensei on 2014-07-04
I use the excellent SMPlayer ("sudo apt-get install smplayer") which lets you choose from a variety of video drivers.

The "smurfing" effect appeared when a [bug]("http://ubuntuforums.org/showthread.php?t=1949137") was introduced into Flash player for Linux that reversed the order of colors when communicating with the VDPAU graphics hardware on NVIDIA adapters.  Since the bug occurred right before Adobe discontinued support for Flash on Linux, it has remained in the player ever since.  I believe NVIDIA tried to fix the problem that Adobe created by rewriting the VDPAU driver.  Your experience suggests that the fix might have worked for the Flash Player plugin but then recreated the problem in downloaded Flash videos.  Anyway, if you can turn off hardware acceleration in your video player (essentially meaning disabling the VDPAU driver), the problem should be resolved.

---

### Post by merlinus on 2014-07-04
Thanks very much re: smplayer.  I just installed it, and the youtube videos are the correct colors.  Any settings I might need to change, other than sources (e.g. cd, dvd)?

BTW, every time there is a security fix to flash player via update manager I have to run terminal commands ('cd /usr/lib/flashplugin-installer' and 'sudo perl -pi.bak -e 's/libvdpau/lixvdpau/g' libflashplayer.so') in order to get rid of the blue faces -- arghhh!

---

### Post by monkeybrain20122 on 2014-07-04
BTW, smplayer also has a stand alone Youtube player (Smtube) in case you haven't noticed. 

Not sure how you dl the videos and in what format, but you should be able to choose .mp4 instead of .flv. In that case you can keep vdpau enabled (in player).

---

### Post by merlinus on 2014-07-04
I d/l-ed them using download helper, in .flv format, but IIRC I can choose .mp4 instead.  How do I enable vdpau in the player?  Is it from video/output driver?  At the moment it is user defined: xv.

Did not see smtube in synaptic.  Is it already a part of smplayer, and if so, how do I access it?  I pasted a youtube url into the open/url box, but nothing happened.

---

### Post by monkeybrain20122 on 2014-07-04
Options > Preferences > Video > Output driver  and choose vdpau from dropdwon (second screenshot)

Options > Youtube browser (first screenshot)

You should install up tp date smplayer from [https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)
smtube (the Youtube browser) from repo probably doesn't work as google keeps changing things and the repo version doesn't keep up.
(Download is not working with smtube even from ppa, but I compiled from git so it works)

---

### Post by merlinus on 2014-07-04
Thanks!  I added the ppa to my apt list, and installed smplayer after apt-get update, and the youtube player was installed as well.

---

