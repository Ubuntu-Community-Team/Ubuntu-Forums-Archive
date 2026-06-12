---
title: "Jaunty 9.04 Wireless adapter prevents suspend / hibernate"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by Andras B. on 2009-07-12
Hi all!

I'm rather new to Ubuntu, and I'm having some problems. One of those is that my USB wireless adapter, model TP-LINK WN322G, is preventing the PC from going into suspend / hibernation state. If I use "Suspend" or "Hibernate" function, the Desktop goes away, and I'm stuck with a blinking cursor, the PC stays on, and I can do nothing but press Reset on the case, because it won't respond to any key or mouse input. I am positive that the adapter is the cause of this, because if I unplug the device, Suspend or Hibernation works every time.

I have done some Googling on this issue, but found nothing relevant.

I am using a standard Ubuntu 9.04, no tweaks or edits yet, just set up my e-mail etc, so it counts as a fresh install, I guess. By the way, the adapter was working out-of-the-box, networking works fine.

Any help welcome!

Thanks!
):P

---

### Post by pytheas22 on 2009-07-12
Please post the output of this command so we can know which driver your wireless card is using:
```

lshw -C Network
lsusb
dmesg | grep wlan
```

If we know that, we can edit the suspend/hibernate scripts to tell them to remove the driver before going to sleep, which would probably solve the problem.

---

### Post by Andras B. on 2009-07-12
Thanks for the reply! I hope these help :)

lshw -C Network:
```
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:0f:af:4d:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:d7:1a:13:c5:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

lsusb:
```
Bus 001 Device 004: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 002: ID 13fd:1840 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c293 Logitech, Inc. WingMan Formula Force GP
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg | grep wlan:
```
[   26.159064] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.947928] wlan0: authenticate with AP 00:1d:0f:e2:44:3e
[   39.953693] wlan0: authenticated
[   39.953697] wlan0: associate with AP 00:1d:0f:e2:44:3e
[   39.955813] wlan0: RX AssocResp from 00:1d:0f:e2:44:3e (capab=0x431 status=0 aid=1)
[   39.955816] wlan0: associated
[   39.956279] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.548016] wlan0: no IPv6 routers present
```

---

### Post by pytheas22 on 2009-07-12
Thanks for that information.  To set up a script that will remove the wireless module before suspend starts, run these commands:

```
cd /etc/pm/sleep.d
sudo gedit 49-rmmod-wifi.sh
```

A file will now be open.  Paste this into it:
```

#!/bin/sh
#
# remove wireless module

case "$1" in
        hibernate|suspend)
                modprobe -r zd1201 zd1211rw
                ;;
        thaw|resume)
                modprobe zd1201
                modprobe zd1211rw
                ;;
esac
```

Then save and close the file.  Finally, run this command:

```
chmod +x 49-rmmod-wifi-sh

```

This will hopefully take care of it.  Please give it a try and let me know.  If it doesn't work, please post the output of these commands after the computer wakes back up:
```

dmesg | grep -ie zd -e resume -e suspend
lsmod | grep zd
```

---

### Post by Andras B. on 2009-07-13
Thank you so very much! Both Suspend and Hibernation works fine now!

Note:

```
chmod +x 49-rmmod-wifi-sh
```gave me a file not found error (note the dash instead of the dot), should be:

```
chmod +x 49-rmmod-wifi.sh
```

---

### Post by pytheas22 on 2009-07-13
Glad that worked on the first try.  The dash vs. dot was just a typo on my part.

---

