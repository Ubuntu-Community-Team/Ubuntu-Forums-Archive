---
title: "several mplayer issues"
date: 2009-10-30
forum: Multimedia Software
---

### Post by lovinglinux on 2009-10-30
These problem occurs with smplayer, gnome-mplayer and gecko-mediaplayer.

[list][*] when in fullscreen, the video flickers a lot when the overlay menu hides itself
[*] video does not resume from pausing, unless you seek forward or backwards.
[*] videos stops for no reason and a white screen is displayed in the place of the video content
[*] when starting fullscreen mode in Firefox using gecko-mediaplayer, the video does not fill the entire screen. Then I have to get out of the fullscreen mode and start it again.[/list]

These problems do not occur all the time, except for the video flickering, but are very frequent.

Some info about my system:

[list][*] I'm running Karmic kde-minimal with compiz and emerald, but I don't have any compiz issues. 
[*] I have restricted extras, all gstreamer and medibuntu stuff. 
[*] I have the smplayer and mplayer PPA repository enabled.
[*] I have nvidia 7300 GT with 185 driver installed and nvidia direct rendering is enabled
[*] VLC does not exhibit these behaviors.
[*] [/list]

Bug report: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/453855](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/453855)

I'm wondering if anyone else is experiencing the same problems and if someone has a solution already?

---

### Post by rvm4000 on 2009-10-30
> **lovinglinux said:**
> These problem occurs with smplayer, gnome-mplayer and gecko-mediaplayer.

[list][*] video does not resume from pausing, unless you seek forward or backwards.[/list]

Change the audio driver from alsa to pulse.

For the other problems disable compiz and see if it works better.

---

### Post by andrew.46 on 2009-10-30
Hi lovinglinux,

> **lovinglinux said:**
> video does not resume from pausing, unless you seek forward or backwards.

I have built my own svn MPlayer under Karmic and I have noticed the pause problem but I am not sure where the problem lies. The same revision of MPlayer on another distro I run does not have this problem.

**Edit:** Just saw RVM's solution and it solves the problem, thanks!!

Andrew

---

### Post by mc4man on 2009-10-30
> when in fullscreen, the video flickers a lot when the overlay menu hides itself

That's generally caused by having "unredirect fullscreen windows" enabled in compiz's general settings, but if you have ati or intel then running compiz and having good video playback seems to be a bit of a crapshoot

---

### Post by lovinglinux on 2009-10-30
> **rvm4000 said:**
> Change the audio driver from alsa to pulse.

For the other problems disable compiz and see if it works better.

Thanks. That seems to have fixed the pausing issue.


> **mc4man said:**
> That's generally caused by having "unredirect fullscreen windows" enabled in compiz's general settings, but if you have ati or intel then running compiz and having good video playback seems to be a bit of a crapshoot

Already tried that, but thanks anyway.

---

