---
title: "X restart needed to play video files after changes to nvidia settings?"
date: 2010-04-16
forum: Multimedia Software
---

### Post by wintercorn on 2010-04-16
I run Ubuntu 9.04 on with proprietary NVidia driver 180.44.

When I change anything in the nvidia-settings, e.g. screen resolution, brightness, second screen etc, everything works fine - except for the fact that I can't play any video files in any player. Sound is there, players don't display any error messages, but the image is black. Flash video within browsers is fine, though.

Things go back to normal with the new settings kept after restarting X. However, having to restart X and lose my desktop set up every time when I just want to connect my laptop to my office screen is highly inconvenient.

Is this a bug or expected behaviour that I have to live with?

---

### Post by Junkieman on 2010-04-17
**Update**: I [followed this post]("http://ubuntuforums.org/showpost.php?p=7552397&postcount=14") and got the latest drivers installed, now just to see if the problem happens again.

I have a similar problem, maybe we can solve this quicker if we work together.

I use nVidia driver version 185.18.36 on Ubuntu 9.10. I would suggest try updating your driver and see if that helps - [http://www.nvidia.com/page/drivers.html](http://www.nvidia.com/page/drivers.html)

Video works fine until randomly all video players will display a black window instead of the video, sound still works. Restarting the session fixes this, until it happens again, about every few hours. 

I suspect a driver bug, but can't find any other reports. Compiz is not enabled.

Can anyone help us to track this issue down? thanks :)

---

### Post by wintercorn on 2010-04-17
I added the nvidia-vdpau ppa to install the 195 driver. However, that ppa caused some [dependency problems]("http://ubuntuforums.org/showthread.php?t=1446831") so I uninstalled the driver again. 

Now I can't get any nvidia driver installed anymore, jockey doesn't see any drivers, manual installation of the packages doesn't work. Unfortunately, I can't help with the video problem anymore as I'm desperate to get a basic system running again.

**Update: ** I followed the instructions in post #18 of [this bug report]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/315555") to get my restricted drivers back. I checked on versions 185, 190, 195 if the bug still appears. 190 and 195 make X crash on my system (Thinkpad T61, nvidia quadro NVS 140m) but version 185 is fine and the bug seems to be resolved. Video works now after changes to nvidia-settings without having to restart X.

I haven't encountered your random video problems yet but I've been running that driver for a couple of hours only. If I notice similar issues, I'll report here.

---

### Post by wintercorn on 2010-04-18
I can now confirm your bug: While the bug I observed in version 180 seems to be fixed in 185, the video goes black on a seemingly random basis after a few hours.

The decision which driver to activate seems be about an ugly trade off which bug is more tolerable. With version 180 I can at least be sure that video keeps working as long as I don't touch nvidia-settings and don't connect a second screen.

Any help on this issue would be appreciated.

---

