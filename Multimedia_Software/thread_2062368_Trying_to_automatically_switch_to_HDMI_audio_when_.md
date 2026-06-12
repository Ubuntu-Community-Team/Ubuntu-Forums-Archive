---
title: "Trying to automatically switch to HDMI audio when cable is plugged in"
date: 2012-09-24
forum: Multimedia Software
---

### Post by rainwalker on 2012-09-24
All I need is a way to:
1. Automatically detect when HDMI is connected
2. Switch to HDMI audio, basically simulate opening the sound settings and clicking on HDMI out
3. Switch back to laptop speakers when HDMI is unplugged

What event is triggered when an HDMI cable is plugged in, and would I be able to tie into it? I've checked dmesg and found nothing useful (as far as I could tell).

I found [_this_]("https://charlesmcruz.wordpress.com/2012/06/23/ubuntu-12-04-stoggle-hdmi-sound-toggleswitch/"), which looks like what I want, but it doesn't work for me because I have no /sys/class/drm directory. [_This_]("https://charlesmcruz.wordpress.com/2012/09/08/ubuntu-12-04-sound-toggle-1-3-hdmi-sound-toggleswitch/") is an updated version of the script that does some extra stuff, but it's still based on that same /sys/class/drm directory.

[_This post_]("http://ubuntuforums.org/showthread.php?t=1370383") from 2010 provides a script that can be bound to a keyboard shortcut, but I want it to be automatic. Apparently it doesn't work on 12.04 anyway, but user psmbfuer [_posted_]("http://ubuntuforums.org/showpost.php?p=12254865&postcount=29") his own version of the script 1 day ago (as of this post) that apparently does. I haven't tried it, because ```
pactl list cards
``` lists my single soundcard as 2 different cards, one for HDMI and one for the laptop speakers.

Any suggestions for approaching this?

---

### Post by Yuske on 2013-02-19
up for this. I've just installed Ubuntu 12.04 - HDMI video works nicely, but I still have to manually switch the HDMI sound =(

---

