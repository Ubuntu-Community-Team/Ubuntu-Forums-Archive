---
title: "Broadcom BCM4306: Lubuntu 12.04 wifi not working."
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by caraj on 2013-07-02
All my wireless-related specs have the name Broadcom in them. Is Broadcom supported? Is there something I should install? My wifi is turned on, but the icon in the system tray shows no list of networks when I access it, so there appears to be nothing the computer is registering as being able to be connected to.

---

### Post by varunendra on 2013-07-03
> **caraj said:**
> All my wireless-related specs have the name Broadcom in them.
Except for some ultra-new ones, all broadcom chips are supported, but due to licencing issues, you need to install the relevant driver/firmware manually for most of them.

To determine which driver you need, please enter the following command in a terminal (ctrl+alt+T) and post back its output here :
```
lspci -nnk | grep -iA2 net
```

---

### Post by Irihapeti on 2013-07-03
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2013-07-06
caraj,

Support questions should be asked in threads so that it can be benefited from advice from more people and similarly more people can get benefited from the answer.

From your PM to me -
> after typing lspci -nnk | grep -iA2 net I got the readout:

02:03.0 Network controller {0280}: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet {14e4:165d} (rev 01)
Subsystem: Dell Latitude D400 {1028:865d}
Kernel driver in use: tg3
--
02.03.0 Network controller {0280}: Broadcom Corporation BCM4306 802.11b/g Wireless LAN contrtoller {14e4:4320} (rev 03)
Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card {1028:0003}
Kernel driver in use: b43-pci-bridge 

What driver dows this mean I need, and where do I get it?

Your card is BCM4306 [14e4:4320] which needs b43 driver that is already in the Linux kernel. However, it needs a firmware that needs to be installed manually due to licencing issues. If you connect to internet via cable, run this command in terminal -
```
sudo apt-get install linux-firmware-nonfree
```

If you have no way to connect Ubuntu to internet, download the same above package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)
Copy the downloaded ".deb" file to your Ubuntu machine > double-click to install, then reboot or do -
```
sudo modprobe -v b43
```

Enjoy the wireless ! :)

---

### Post by wildmanne39 on 2013-10-05
Make sure you do not have the terminal and software center open at the same time then run the command again and it should get your wireless working after a reboot unless you have the wrong firmware or driver installed already before you run that command.
Thanks

---

