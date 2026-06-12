---
title: "USB wireless adapter recognized automatically, times out while authenticating with AP"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by Timbo23 on 2010-06-16
Hi everyone, my networking knowledge is weak and I'm a newcomer to Linux. I'm using a Netgear MA101 (revision B) USB wireless adapter, based on the Atmel  AT76C503A chipset. I have Ubuntu 10.04 installed.

My adapter is recognized immediately but whenever I try to connect to my Netgear MR812 v2 router (running the latest firmware) the signal strength is extremely low and eventually it times out, as evidenced by the results of a *dmesg*:
```

[132.024967] wlan0: authenticate with AP 00:09:5b:4e:90:6a
[132.224077] wlan0: authenticate with AP 00:09:5b:4e:90:6a
[132.424088] wlan0: authenticate with AP 00:09:5b:4e:90:6a
[132.624089] wlan0: authentication with AP 00:09:5b:4e:90:6a timed out
```This continues a few times...

I have my router set up to be open, no password. My closest neighbors live well outside of my router's range, so I'm not too worried. Since there should be no authentication needed, why is this even causing a problem?

When I do a *lsusb*, it correctly identifies my adapter.  This adapter has gotten excellent signal in the exact same location when I was running various versions of Windows on this PC. Also, my OSX box in this room gets excellent signal, so I'm wondering why I get such poor signal with Ubuntu, and if the poor signal is why I keep timing out.

I know that as of 9.04, this chipset is automatically supported, but I'm starting to wonder if it's a driver issue because it looks to me like the driver is installed but maybe not activated or set to work correctly with my adapter. When I run *nm-tool*, I get:
```

- Device: wlan0 -----------------------------
   Type: 802.11 WiFi
  Driver: at76c50x-usb
  State: Disconnected
  Default: No
  HW Address: 00:09:5B:38:51:77
```So, it correctly identifies the driver. However, when I run *lshw -C network*, I get:
```
*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial 00:09:5b:38:51:77
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
```Shouldn't there be an entry for "driver" under configuration? Furthermore, when I run *lsmod*, one of the lines it returns is:
```
at76c50x usb             37640             0
```Also, I have no resolv.conf file in /etc. Maybe it's not there because I haven't yet successfully connected to the Internet? Or is it something I'd need to set up manually?

That is about all of the troubleshooting that I know how to do in Linux...Does anyone have any ideas that might point me in the right direction?

---

### Post by Timbo23 on 2010-06-17
I'm particularly wondering if anyone can shed some light on what it means when you time out while authenticating with the router. Considering my router is open with no encryption, why does my adapter need to authenticate?

Is there any more information that I could give you guys that might be helpful? I'm not too familiar with Linux commands, especially those related to networking, but would love to use this experience to learn what I can!

---

