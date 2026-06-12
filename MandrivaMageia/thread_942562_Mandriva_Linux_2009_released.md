---
title: "Mandriva Linux 2009 released"
date: 2008-10-09
forum: Mandriva/Mageia
---

### Post by AdamWill on 2008-10-09
Mandriva has today released [Mandriva Linux 2009](http://wiki.mandriva.com/en/2009.0), the new major release of the popular distribution. 2009 is a bold release which brings the new KDE 4 as the default desktop, along with a re-designed installer and Mandriva Control Center and many other new features. Other significant updates include GNOME 2.24, OpenOffice.org 3, Mozilla Firefox 3, and kernel 2.6.27. Key features include new graphical in-line upgrade capability, netbook compatibility, class-leading hardware support, and further improved support for working with mobile devices. For more details, see the [Release Tour](http://wiki.mandriva.com/en/2009.0_Tour) and the [Release Notes](http://wiki.mandriva.com/en/2009.0_Notes). Get it at the [download page](http://www.mandriva.com/en/download), or [go straight to the torrent list](http://torrent.mandriva.com/public).

---

### Post by AdamWill on 2008-10-09
If you're running a 2009 pre-release, to upgrade to 2009 final, simply do the following:

* Remove all repositories (urpmi.removemedia -a as root, or use the graphical repository configuration tool)
* Add 2009 repositories. At present, doing 'urpmi.addmedia --distrib --mirrorlist' as root should give you 2009 not Cooker, but it's possible it might give you Cooker if you're doing this later. If you want to be sure, do it manually, or use Easy URPMI - [http://easyurpmi.zarb.org](http://easyurpmi.zarb.org) - when it gets 2009 support (Doesn't have it as I write this).
* Make sure any mandriva-release packages you have are version 2009.0, not 2009.1
* Run urpmi --auto-select

and you should be good.

---

### Post by SuperSonic4 on 2008-10-09
Thank you very much, I must say I've been using cooker for a few weeks now (since RC1) and I find it to be much better than suse and certainly my favourite KDE distro.

As a side note, installing this plasmoid ([http://kde-look.org/content/show.php/multirows+task+manager?content=83177](http://kde-look.org/content/show.php/multirows+task+manager?content=83177)) will give you multi-row taskbar.

Keep up the good work :D

---

### Post by karellen on 2008-10-09
I'm downloading the Live CD right now

---

### Post by Antman on 2008-10-09
Once I get home, I'll download the DVD and see how it compares to 2008.1. I really want to like KDE4 but... I will probably install Gnome on my machines.

---

