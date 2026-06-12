---
title: "USB wireless -driver installed OK, freezes Dapper on activate"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by damianubuntu on 2006-05-11
HI all,
using  a Linksys WUSB 54g, installed drivers as per 

[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

This worked on another machine and in Breezy, but on this machine using Dapper the device is found after installing drivers, and I can configure it from System...Networking, but when I click Activate the whole of Dapper hangs and needs a PC like hard reboot.

I've had this wireless working with this router, so there shouldn't be a problem there, and I've had this machine (on Dapper) connect to the router with eth card (now removed).  I've tried the various troubleshooting steps on 

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

which is otherwise excellent, but Im a bit stuck because prior to clicking Activate, everything looks correct, and after...:confused: 

Any ideas anyone?

Cheers

---

### Post by damianubuntu on 2006-05-12
Worked out a strange fix with Kobalt's help:

Configured the adaptor in Networking, but without activating it.  Rebooted and then activated and all is now OK>  Its a bit PC like, but at least it works!

---

