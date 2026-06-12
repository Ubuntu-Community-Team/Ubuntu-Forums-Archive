---
title: "ATI 9.2 Drivers - Screen Resolution Settings"
date: 2009-02-24
forum: Multimedia Software
---

### Post by cberger on 2009-02-24
Folks,

Been trying to isolate issues with screen tearing in MythVideo using an on-board ATI HD3200 Video controller.  As a result, and through numerous other failed attempts at open source and proprietary ATI drivers, installed the latest 9.2 drivers.

Followed instructions, with emphasis on removing fglrx drivers from the restricted linux modules, and all went well.  Rebooted several times with no error.

Changed from the default 1980x1024 screen resolution to 1280x720.  Did this through the ATI Config utility as well as Gnome.  Changing resolution through Gnome was ignored.  Changing through the ATI utility netted the desired results.  However, after rebooting, the screen was garbled where there should be a login.

The only resolution was rebooting into "safe mode" and running "sudo aticonfig --initial -f".  This reset X back to something useable.  As an aside, it did recreate the xorg.conf file without the "UseFastTLS" "1" in the Device Section that was originally created when upgrading to 9.2.

Anyone else run into similar issues?

I'll post another thread about this as I don't want to miss the point here, but mythtv also starts below the taskbar even though it's not running in a window (GUI & Myth running 1920x1024).  Auto hiding the task bar just makes myth start below the residual line denoting the task bar is present.  Changing to 1280x720 using ATI's ACCC and in Myth, allows mythtv to run full screen (at that resolution).  Again, after reboot, the screen is garbage resulting in the above process to fix!

Any insight is appreciated.

Clint

---

### Post by markbuntu on 2009-02-24
Did you read the release notes?
You might want to do that.

---

### Post by th0th696 on 2009-02-28
I just read the release notes and I fail to see what the point of that was?

Anyhow, cberger, I am experiencing the very same issues you are.  I've even tried this under Gentoo with the exact same results.  It's funny the corrupted screen gentoo threw up looked to be the exact same one from ubuntu, leading me to believe that somehow the video ram was retained thru the reboot.  Anyhow, I'm going to start backtracking and trying previous versions till I find something runs well on the HD 3650.  I'll post here if I find anything useful.  Best resources I've found so far are the Unofficial ATI wiki:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

and mythtv's wiki topic on the subject is quite informative:

[http://www.mythtv.org/wiki/AtiProprietaryDriver](http://www.mythtv.org/wiki/AtiProprietaryDriver)

---

### Post by markbuntu on 2009-03-01
From the release notes:

> 
&#8226;
&#8226; Catalyst Control Center, on some systems X may fails to start when the reso-
  lution is set to less than 1680x1050 through displays manager


---

### Post by th0th696 on 2009-03-01
That's probably it, display here is running 1600x1200.  I'll try the 9.1

EDIT: 9.1 working great here now

---

