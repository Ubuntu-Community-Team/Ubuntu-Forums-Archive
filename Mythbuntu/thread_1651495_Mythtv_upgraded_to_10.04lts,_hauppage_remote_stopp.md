---
title: "Mythtv upgraded to 10.04lts, hauppage remote stopped working"
date: 2010-12-23
forum: Mythbuntu
---

### Post by Fkewl on 2010-12-23
Any ideas to revive my dead remote?

I've upgraded (maybe i shouldn't) ubuntu to 10.04lts, but since the upgrade, my haupppage remote won't work anymore

(hauppage pvr 150 card) 

I've uninstalled and reinstalled LIRC, not working.
Tried the "dynamic mapping" and the other option , not working

I don't see /dev/lirc like i think i'm supposed to see. 

I've verified the batteries, changed them and verified connection of receiver, seem ok.

---

### Post by IceCap on 2010-12-27
To fix this look at the last message on the first page of this thread [COLOR="Red"] [http://ubuntuforums.org/showthread.php?t=1597886]("http://ubuntuforums.org/showthread.php?t=1597886") [/COLOR]
  As has been discussed around here, the lirc package in Lucid has a bug in it that had been fixed in lirc 0.8.7 which is supplied with Maveric.  Fortunately, the Maveric package for lirc works on Lucid (I just finished doing this myself and it works).

  So in short just go to this page, [COLOR="red"] [http://packages.ubuntu.com/maverick/all/lirc-modules-source/download]("http://packages.ubuntu.com/maverick/all/lirc-modules-source/download") [/COLOR] download the package and have the installer run it right away.  Reboot and it should work.

  Hope this helps.

  IC

---

