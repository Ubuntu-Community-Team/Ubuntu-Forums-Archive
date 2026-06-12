---
title: "Ati 9000 IGP Mobility"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by MrDetermination on 2007-03-15
Any chance in hell we can get this thing working w/3D acceleration?  I've tried the 8.28 I think, from the wiki "The Ubuntu way", the Ati 8.38 installer.  The Envy way.  The Automatix way.  I've tried editing the xorg.conf file and reconfiguring that.  I would *love* to have 3D support on this laptop as it is the best way I can spend real time in Linux, learning linux.  Not having that support is kind of a drag though, and makes me boot to Windows.

---

### Post by petrusgomes on 2008-02-18
Hi!

I had the same problem two years ago and reading the notes from ATI proprietary driver, I discovered that 900 IGP mobility has no 3D support with this drivers...

But, simply using the open "ati" driver from ubuntu, I have 3D support and Compiz stuff... =)

Just change the driver option, from /etc/X11/xorg.conf to "ati"  and you will probably get all working... ( make a backup of xorg)

sorry for english...I'm brasilian

Good Luck

---

