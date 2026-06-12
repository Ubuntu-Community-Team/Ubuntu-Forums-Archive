---
title: "Problem playing audio cd's in Amarok"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by _jj on 2007-08-04
When I try and play an audio cd in Amarok (Engage-Play Audio Cd) nothing happens and I get the message "Could not play AudioCD" appearing in the bottom left corner.
This is despite the fact the cd is mounted (appears on desktop) and can be played with other players (Kaffeine) or even ripped.
The default device is set to
audiocd:/dev/cdrom
which seems to match the cd part of my fstab
UUID=3550463f-3c29-4874-8c10-82fecbc45691 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

thanks in advance for any help

---

### Post by f37u5g0d on 2008-05-05
I have a dual CD comp and the same problem you are having with ubuntu 8.04 and amarok.  You have to go to /dev and go through all of the "link to block devices" (the icons that are in there not the folders).  These files represent all of your hardware.  Find the one that reads cdrom1 or cdrom0 or something along those lines.  Then go into amarok settings > configure amarok and navigate to the engine tab.  You'll see a box called "default device."  In that box change the default "/dev/cdrom" to whatever file you found in the /dev folder.  i.e. "/dev/cdrom1" or whatever it is.  This worked for me.  I have 2 cd drives but for some reason I have cdrom2 and cdrom3 in my dev folder so I but /dev/cdrom2 in the amarok settings and now I can play CD's.

---

