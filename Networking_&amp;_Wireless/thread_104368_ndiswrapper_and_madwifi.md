---
title: "ndiswrapper and madwifi ?"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by coderasm on 2005-12-16
I'm trying to get my DWL-G132 usb wifi adapter to work under Ubuntu.  I'm running ubuntu 5.10 with kernel 2.6.12-10-686.  I really want it to get to work with the aireplay program uncluded in the aircrack suite.  Do I need to install ndiswrapper or madwifi or both?  I have already installed ndiswrapper 1.7.  I haven't gone any further than that.  Thanks for any help.

---

### Post by thezerogroup on 2005-12-16
Here is a link to a madwifi how to: 


[http://www.ubuntuforums.org/showthread.php?t=104670]("http://www.ubuntuforums.org/showthread.php?t=104670")

---

### Post by Lambert on 2005-12-18
madwifi doesn't currently support usb devices with the atheros chipset. You will need to use the windows drivers with ndiswrapper.

There are many posts in the forum about ndiswrapper and entries in the wiki. You can also look at the ndiswrapper wiki for help.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

