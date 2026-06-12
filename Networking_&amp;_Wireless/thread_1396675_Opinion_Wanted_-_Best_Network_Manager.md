---
title: "Opinion Wanted - Best Network Manager"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by tecknomage on 2010-02-02
OK, I run **Ubuntu 9.10** with the default **Network Manager**.

Seeking opinion on IF this is the best network manager to use :?:

How about KWLan or anther manager?


I do have a specific reason to ask. No matter what I do, I cannot get my WiFi connection to work. This MAY be a problem with my **2Wire (*brand*) Router** at home.

Even when my router is set for no WEP, **Network Manager** keeps asking for a password and will not accept NOT having one.


Wireless & WEP is the one feature that ALL Linux version could use improvement. There seems to be no standard. Multiple locations for files and data, like where AND how network interfaces info is kept. The need for complex SUDO or other command-line setup vs a user-friendly GUI.

---

### Post by claracc on 2010-02-02
Wicd.

Network-manager from gnome doesn't work with some intel wifi cards.

---

### Post by redbook4574 on 2010-02-02
wicd is fine unless you need mobile broadband, if so stick with network manager.

---

### Post by jamoncillo on 2010-02-02
yeah. I too want out of Network Manager. It has given me a couple of troubles with both my network at home (once I switched autenthication from WEP to WPA2) and with my school network (WPA) I Was thinking in installing WICD. A lot of people speak for it, so I'm actually making the switch right now. 

I was trying to use a USB wireless adapter instead of my built in PCI-card, but if I turned off the switch also my USB adapter was disabled. So I just Installed WICD and it seems to be more customizable than Network Manager.

Altough Network Manager is easier to use, since autodetects some of your network configuration


EDIT: hahah
I can't get an IP address on WICD  XD

---

### Post by tecknomage on 2010-02-03
> **claracc said:**
> Wicd.

Network-manager from gnome doesn't work with some intel wifi cards.

I did try **WICD** with **Ubuntu 9.4**, but had the same problem that Network Manager has.

This is when I discovered that network data was NOT kept in consistent folders, Also, the contents of key files like **interfaces.txt** which various help files tell you to modify for Wireless (***wlan0** entries*). We should not be doing this sort of thing manually. _Whatever network manager_ used should make the correct entries for you in this file. This tells me that network managers are keeping the required wireless setup info somewhere else, which only adds confusion.

---

### Post by cb951303 on 2010-02-03
I, too, prefer wicd over networkmanager.

---

