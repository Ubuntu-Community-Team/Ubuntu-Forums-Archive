---
title: "ndiswrapper disables usb automount"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by alfh on 2011-01-31
Making wifi work with ndiswrapper disabled usb automount. This happened on several ubuntu versions, including 10.10.

After following the directions given in this post [http://ubuntuforums.org/showpost.php?p=9464809&postcount=14]("http://ubuntuforums.org/showpost.php?p=9464809&postcount=14") usb automounting stopped working.

I fixed it this way:

```
sudo gedit /etc/modules
```

Added these lines to the file:
```
usb_storage
usbhid
```

Save and exit, worked after reboot or restarting network.

usb automount troubles could also be related to legacy floppy settings in BIOS, see

[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html]("http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html")

---

### Post by MARP1961 on 2011-03-18
Many thanks for this. I have had months of different USB flash drives not automounting. I do use ndiswrapper for a PCI WiFi card that seems to need a Windows XP driver. Your fix works for me.

---

