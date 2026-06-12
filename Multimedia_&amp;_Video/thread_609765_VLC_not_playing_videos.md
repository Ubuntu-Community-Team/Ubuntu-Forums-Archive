---
title: "VLC not playing videos"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by Xixor5000 on 2007-11-11
I installed VLC and now i cant play videos wither either VLC OR movie player, whereas before I installed it i could at least play videos with movie player.  Some videos that play right on a web page work like youtube but most do not as well as all videos that i download to my hard drive.  It seems as though it does not have the right codecs or something because i get no sound and vertical green lines on the screen but why did it mess up movie player as well?  Any ideas?

---

### Post by jasmuz on 2007-11-11
How about deinstalling, reinstalling vlc and mozilla-vlc plugin?

---

### Post by mc4man on 2007-11-11
If you're using a nvidia card with restricted drivers I've found that once you get the green screen it will affect all your players. The simplest fix is to reboot, that usually restores video (for awhile)
If not or if the video comes back with decreased quality I've "fixed" it by backing up xorg.conf, disabling restricted drivers, reboot, enable restricted drivers, reboot, and replacing the new xorg.conf with the backup

---

### Post by Xixor5000 on 2007-11-11
The restart seemes to have fixed the problem, thanks hopefully it will continue to work

---

