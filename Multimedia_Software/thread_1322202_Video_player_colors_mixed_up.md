---
title: "Video player colors mixed up"
date: 2009-11-10
forum: Multimedia Software
---

### Post by amcsi on 2009-11-10
A crazy thing is going on: red becomes green and green becomes red. I think. And it is really ugly. For VLC the colors are fine, so it might be some codec problem or something. Another interesting thing is that when I make a snapshot with VLC, then again, the colors are messed up the same way. What is causing the problem and how do I fix it?

I'm running Ubuntu 9.10, I have MPlayer and VLC as video players (the colors for the video are messed up in MPlayer and Totem as well, which nI uninstalled).

---

### Post by jaygo on 2009-11-29
Just ran into the same issue on one of the four PCs running 9.10. It's the only one I upgraded rather than doing a fresh install. And it's the only one with the fluendo codecs. Unlike you, I'm getting the issue in VLC as well. Flash videos online have no issues but everything I play from the desktop does (avi, mp4, ogv).

Let me know if you find anything out.

---

### Post by jaygo on 2009-11-29
alright, fixed it. As Candrian suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=1309017&highlight=red+green+video&page=2"), go into Totem (aka Movie Player) > Edit > Preferences > Display and click reset to defaults (or just drag the hue slider to center). This fixed the issue in all my video players.

For some reason, upgrading from 9.04 to 9.10 screws up the system-wide hue setting.

---

