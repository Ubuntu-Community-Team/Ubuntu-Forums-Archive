---
title: "Finally got custom Ubuntu router up and running, just need help finalizing!"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by joebobjoe on 2010-07-03
Quick question guys and gals: How do I get "wlan0" and "eth0" interfaces to start at startup as as well as for "dhclient" to obtain an IP address automatically for "eth0?"

Thanks.

---

### Post by Iowan on 2010-07-03
If I recall correctly, you can select the "Make available to all users" option for the interfaces. Ordinarily, Network Manager waits until a user logs in to set up networking, but the aforementioned option is supposed to make it happen at startup.

---

### Post by joebobjoe on 2010-07-03
> **Iowan said:**
> If I recall correctly, you can select the "Make available to all users" option for the interfaces. Ordinarily, Network Manager waits until a user logs in to set up networking, but the aforementioned option is supposed to make it happen at startup.
Sorry, forgot to mention: I'm not using a GUI.

---

### Post by Iowan on 2010-07-03
If networking is configured via */etc/network/interfaces*, it *should* fire up at startup... :confused:

---

### Post by joebobjoe on 2010-07-04
Okay, after days of head-splitting, finally got my custom Broadcom-based (the head-splitting part) wireless router up and running. Well for the most part. Iptables isn't finished yet. Anyway, I am about to begin a Google journey regarding boot-up management, but any advice regarding these key questions could help me out along the way:

[LIST=1]
[*]How do I get my external interface "eth0" up and running the "dhclient" command at boot?
[*]How do I assign "wlan0" an IP address, etc. at boot (I've tried adding "wlan0" to the /etc/network/interfaces with no effect)?
[*]How do I get the hostapd daemon to start at boot and after "wlan0" is up?
[*]How do I get /etc/init.d/dhcp3-server to start after all of this?
[/LIST]

Thank-you Ubuntu community!

---

### Post by joebobjoe on 2010-07-04
> **Iowan said:**
> If networking is configured via */etc/network/interfaces*, it *should* fire up at startup... :confused:

I don't think my driver plays very well with /etc/network/interfaces. Its the b43 driver for Broadcom wireless. It never listened to that file as far as I can remember.

---

### Post by Iowan on 2010-07-04
Threads merged.

---

### Post by gareththered on 2010-07-05
Try [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) for the wireless.  It's old, but should work.
For ethernet, try> auto eth0
iface eth0 inet dhcp in '/etc/network/interfaces'

Regards,

Gareth

---

