---
title: "Novatel 760USB broadband ?"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-04-07
I am using a Novatel 760 and I managed to get it to work properly by ejecting the internal storage by using this link

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=364&sid=3f625b27c24fa5fd5f9302e588591b91]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=364&sid=3f625b27c24fa5fd5f9302e588591b91")

Basically I created a file /etc/udev/rules.d/10-ejectfakecd.rules: 
```

SUBSYSTEM=="block", KERNEL=="sr[0-9]*", SUBSYSTEMS=="usb", ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5031", PROGRAM="/usr/bin/eject $tempnode", OPTIONS+="last_rule"

```

It works very well actually, but it still sometimes brings up the internal storage as a cdrom after the connection is established.  I would prefer if it did not mount the internal storage at all.  I am not a wizard at writing udev commands so I was wondering if someone knew what I could use besides the eject command to permanently disable the internal storage.

:?:

---

