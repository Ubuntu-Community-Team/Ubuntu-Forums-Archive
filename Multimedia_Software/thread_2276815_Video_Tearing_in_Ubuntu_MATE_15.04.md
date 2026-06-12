---
title: "Video Tearing in Ubuntu MATE 15.04"
date: 2015-05-05
forum: Multimedia Software
---

### Post by Berwyn_Powell on 2015-05-05
Hello There,
First of all sorry for another thread asking about video tearing, but no solution already posted that I found has worked so far.

I've just installed Ubuntu Mate 15.04 on a ASUS N550JV and am having tearing issues in video playback. I don't get tearing anywhere else (vsync works in games etc.) and can't seem to fix it. I've tried the Tearing.sh file with no success and VDPAU doesn't fix the issue (supposedly that is meant to fix it). I also don't have an option for vsync in the nivida x-server settings. The laptop has a GT750M and I'm using the tested 346.59 drivers.

Any help would be much appreciated on this one as I'm fresh out of ideas.
Thank you, Bez

EDIT: I've tried both SMPlayer and VLC, both have identical issues.

---

### Post by dino99 on 2015-05-05
from the baker's forum    [https://devtalk.nvidia.com/default/topic/543305/screen-video-tearing-gtx6xx-7xx-kepler-9xx-maxwell-in-almost-all-applications-including-desktop/](https://devtalk.nvidia.com/default/topic/543305/screen-video-tearing-gtx6xx-7xx-kepler-9xx-maxwell-in-almost-all-applications-including-desktop/)
question [http://askubuntu.com/questions/479352/screen-tearing-only-when-playing-videos-using-geforce-gt-750m](http://askubuntu.com/questions/479352/screen-tearing-only-when-playing-videos-using-geforce-gt-750m)

---

### Post by mc4man on 2015-05-05
What happens if you switch to Intel, are vids ok?
Nvidia optimus drivers via nvidia-prime create tearing, [everywhere on a compositing DE]("https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1260128") like compiz, I gather with mate just with videos?..
(here with a nvidia m gpu I never use nvidia drivers on a Ubuntu (unity/compiz) install, Intel gpu is fine

---

### Post by Berwyn_Powell on 2015-05-05
The intel drivers cause no problems, so switching is an option; they do not work with HDMi sound output however. I was tempted to move over to Nouveau permanently, but I do a little too much gaming and Blender work etc. to be able to take the performance hit. The tearing does seem to be confined only to videos, I'm running Marco as the window manager. The only thing stopping me using intel for videos is that it seems to screw my sound card up, HDNMi does not work at all and the in-built sound sometimes disables itself.

---

### Post by mc4man on 2015-05-05
As far as hdmi sound no idea here as only use either built-in speakers or bluetooth. You should search out that issue as it could be more  fixable.
Otherwise maybe  when wayland or mir are usable as the issue (no vsync) is likely at it's root an xserver problem that was never fixed & never will be.

---

### Post by Berwyn_Powell on 2015-05-05
I'll try the HDMi thing, thanks for the help. I've heard about wayland and mir, but being a Linux noob don't fully understand. This is totally unrelated, but is there some kind of linux architecture for beginners guide that I could have a look at? (one that describes what everything is and how it all fits together; boot-loader, window manager etc.)

---

### Post by mc4man on 2015-05-05
I guess another possible would be to see if bumblebee still works, then it's more nvidia on demand. Note that nvidia-prime & bumblebee can *not *co-exist..

---

### Post by Berwyn_Powell on 2015-05-05
I've not tried Bumblebee yet, but when I was on Mint 17.1 it really screwed things up. I think I remember reading that it doesn't work after 13.10 or so. I'd rather not screw around with drivers too much as last time I did I had to reinstall the system; as I'm using it as my uni laptop that causes a little too much downtime. Thanks for the help though, I guess I'll have to wait until wayland is out to get vsync working properly with the nvidia drivers.

---

### Post by mc4man on 2015-05-05
I'm sure there's lots of info/reading available, myself again don't know.
 I've only approached/learned, ect. from trial & error with some logical problem solving techniques

---

### Post by dino99 on 2015-05-05
> **Berwyn_Powell said:**
> I'll try the HDMi thing, thanks for the help. I've heard about wayland and mir, but being a Linux noob don't fully understand. This is totally unrelated, but is there some kind of linux architecture for beginners guide that I could have a look at? (one that describes what everything is and how it all fits together; boot-loader, window manager etc.)

check my signature links below, you will get some reading hours  ):P

---

### Post by Yellow Pasque on 2015-05-07
Have you tried enabling compositing for marco?
[https://wiki.archlinux.org/index.php/MATE#Enabling_compositing](https://wiki.archlinux.org/index.php/MATE#Enabling_compositing)

Sorry for Arch Linux link, but it came up first when searching. The command should work the same on Ubuntu, though it's possible Ubuntu already has it enabled by default.
I guess compton would be another option. It's what I run on top of xfce and it works well for my 8400GS using both proprietary and open-source driver.

---

### Post by mc4man on 2015-05-07
It's likely compositing will make it worse, as in - everywhere.
The problem isn't nvidia drivers or chipsets in general, it's specific to  optimus chipsets & nvidia-prime

---

