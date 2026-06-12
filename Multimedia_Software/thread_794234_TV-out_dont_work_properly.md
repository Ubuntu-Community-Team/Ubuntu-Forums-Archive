---
title: "TV-out dont work properly"
date: 2008-05-14
forum: Multimedia Software
---

### Post by fabben on 2008-05-14
Last week I've been trying to get TV-out working, and have solved some problems, but not all:

I have a PC with ASUS EAH3650, with a Radeon 3650, 512 MB and a Ubuntu 8.04 installed from CD some weeks ago. I installed the ati-driver from ati.com somewhere (it's not the open source one, because that says not support TV-out yet).

If I'm booting the machine with only one screen configured in xorg.conf, everything works good. I can start ATI Catalyst Control Center, and the 3D accelerator works fine.

Under booting sequence I also see the boot text on my TV, so the connection to TV works fine. (I'm using the SVIDEO connector).

But then I try to boot with two screens, like I do with my other computer (that have NVidia card, so it is some differences) I get problems. What I want is to have one screen :0.0 (monitor, 1600x1200) and one :0.1 (TV, PAL B, 800x600).

**The problem:**
Accelerator dont work. Things that is to suppose to use it just hangs. Program don't crash, but nothing happends.

_ Works:_
$ DISPLAY=:0.0 feh picture.jpg
$ DISPLAY=:0.0 mplayer movie.mpg
$ DISPLAY=:0.1 feh picture.jgg

_Dont work:_
$ DISPLAY=:0.1 mplayer -fs movie.mpg
 (Nothing apperars on the TV screen, only the GNOME interface).
$ glxinfo
  (hangs, but not ends, just take the terminal until I do ^C)
$ fglrxinfo
   (same as glxinfo)
$ glxgears
   (same as glxinfo).

I have tested zillions of variants av xorg.conf. The latest version is on [http://fabbe.se/X/xorg.conf]("http://fabbe.se/X/xorg.conf").

The log file for that startup I put on: [http://fabbe.se/X/Xorg.0.log]("http://fabbe.se/X/Xorg.0.log").

(Both files is listed in [http://fabbe.se/X/](http://fabbe.se/X/) )

I would be very glad if someone could look at it and give me some clue.

Greetings
Fabbe

---

