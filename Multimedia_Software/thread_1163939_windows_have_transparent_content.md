---
title: "windows have transparent content"
date: 2009-05-19
forum: Multimedia Software
---

### Post by KhaaL on 2009-05-19
I've had this problem before in intrepid, but it dissapears and returns at will :confused: And now it's back.

The symptoms are these: in virtualbox or smplayer, the contents are transparent in the window. smplayer plays the video but nothing is visible because its transparent. In virtualbox only certain things are transparent, for example during the BIOS when booting a machine or certain applications colors (see screenshot). When compiz is turned off, contents inside virtualbox shows. However, the video in smplayer is blank instead (this is with xv output module). I tried setting it to GL2, then the video output would work, but the starting screen is as transparent as with xv. anybody who has similiar issues? This is with nvidia version 185.18.04 (but occured with other versions) and Xserver 1.6.0

---

### Post by KhaaL on 2009-05-20
with a restart, this problem is gone for now - windows contents in virtualbox and smplayer are showing now. This problem seems to come and go at will, any suggestions to logs i could look into to get clues on this problem?

---

### Post by terdon on 2009-06-06
Are you running cairo-dock? I got the same problem and it seems to be the docks fault. Check out this thread:
[http://www.cairo-dock.org/bg_topic.php?t=2201]("http://www.cairo-dock.org/bg_topic.php?t=2201")

---

### Post by fabounet on 2009-06-07
actually it's a bug in Qt4
the simple way to fix it is to set this variable before you launch any Qt-based program :
```

export XLIB_SKIP_ARGB_VISUALS=1
skype &
```

---

### Post by terdon on 2009-06-07
I posted a simple workaround to this thread:

[http://ubuntuforums.org/showthread.php?t=1178269]("http://ubuntuforums.org/showthread.php?t=1178269")

---

### Post by KhaaL on 2009-06-08
Thanks terdon, I also updated the [bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-nv/+bug/378823") with the information you provided

---

