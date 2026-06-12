---
title: "Restoring USB wired interface"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by aredubya on 2010-06-18
Hi folks,

I've been working on a koala system, trying to  set it up as a wireless AP with a pair of wired interfaces. The hardware  itself is a small Nvidia ION platform with a built-in NIC and a bunch  of USB ports, so I decided to set it up with a single wired USB NIC and a  wireless USB NIC. For wired, I settled on a TrendNet TU2-ET100. Initially, this NIC worked  perfectly on with no hackery required, plugged in and off it went,  assigned as eth1 on the system.

For wireless, I've tried a couple  of different units, both of which required use of the compat-wireless  drivers to get recognized. I'm still having problems with that, but I'll  deal with that later. In building and installing the compat-wireless  drivers, it appears to have messed up the included drivers for my  TrendNet USB NIC. Now when I boot the box, it comes up with the  following error:

Jun 18 13:57:39 sanbox kernel: [    7.102401]  asix: disagrees about version of symbol usbnet_set_msglevel
Jun 18  13:57:39 sanbox kernel: [    7.102411] asix: Unknown symbol  usbnet_set_msglevel
Jun 18 13:57:39 sanbox kernel: [    7.103510]  asix: disagrees about version of symbol usbnet_change_mtu
Jun 18  13:57:39 sanbox kernel: [    7.103515] asix: Unknown symbol  usbnet_change_mtu
Jun 18 13:57:39 sanbox kernel: [    7.103871] asix:  disagrees about version of symbol usbnet_unlink_rx_urbs
Jun 18  13:57:39 sanbox kernel: [    7.103877] asix: Unknown symbol  usbnet_unlink_rx_urbs
Jun 18 13:57:39 sanbox kernel: [    7.104181]  asix: disagrees about version of symbol usbnet_get_msglevel
Jun 18  13:57:39 sanbox kernel: [    7.104186] asix: Unknown symbol  usbnet_get_msglevel
Jun 18 13:57:39 sanbox kernel: [    7.104623]  asix: disagrees about version of symbol usbnet_open
Jun 18 13:57:39  sanbox kernel: [    7.104629] asix: Unknown symbol usbnet_open
Jun 18  13:57:39 sanbox kernel: [    7.104889] asix: disagrees about version of  symbol usbnet_skb_return
Jun 18 13:57:39 sanbox kernel: [     7.104895] asix: Unknown symbol usbnet_skb_return
Jun 18 13:57:39  sanbox kernel: [    7.105106] asix: disagrees about version of symbol  usbnet_tx_timeout
Jun 18 13:57:39 sanbox kernel: [    7.105111] asix:  Unknown symbol usbnet_tx_timeout
Jun 18 13:57:39 sanbox kernel: [     7.105653] asix: disagrees about version of symbol usbnet_get_settings
Jun  18 13:57:39 sanbox kernel: [    7.105659] asix: Unknown symbol  usbnet_get_settings
Jun 18 13:57:39 sanbox kernel: [    7.106097]  asix: disagrees about version of symbol usbnet_suspend
Jun 18  13:57:39 sanbox kernel: [    7.106102] asix: Unknown symbol  usbnet_suspend
Jun 18 13:57:39 sanbox kernel: [    7.106313] asix:  disagrees about version of symbol usbnet_start_xmit
Jun 18 13:57:39  sanbox kernel: [    7.106318] asix: Unknown symbol usbnet_start_xmit
Jun  18 13:57:39 sanbox kernel: [    7.106728] asix: disagrees about version  of symbol usbnet_get_drvinfo
Jun 18 13:57:39 sanbox kernel: [     7.106733] asix: Unknown symbol usbnet_get_drvinfo
Jun 18 13:57:39  sanbox kernel: [    7.107204] asix: disagrees about version of symbol  usbnet_get_endpoints
Jun 18 13:57:39 sanbox kernel: [    7.107209]  asix: Unknown symbol usbnet_get_endpoints
Jun 18 13:57:39 sanbox  kernel: [    7.107825] asix: disagrees about version of symbol  usbnet_nway_reset
Jun 18 13:57:39 sanbox kernel: [    7.107830] asix:  Unknown symbol usbnet_nway_reset
Jun 18 13:57:39 sanbox kernel: [     7.108075] asix: disagrees about version of symbol usbnet_stop
Jun 18  13:57:39 sanbox kernel: [    7.108080] asix: Unknown symbol usbnet_stop
Jun  18 13:57:39 sanbox kernel: [    7.108414] asix: disagrees about version  of symbol usbnet_defer_kevent
Jun 18 13:57:39 sanbox kernel: [     7.108419] asix: Unknown symbol usbnet_defer_kevent
Jun 18 13:57:39  sanbox kernel: [    7.108986] asix: disagrees about version of symbol  usbnet_disconnect
Jun 18 13:57:39 sanbox kernel: [    7.108991] asix:  Unknown symbol usbnet_disconnect
Jun 18 13:57:39 sanbox kernel: [     7.109323] asix: disagrees about version of symbol usbnet_set_settings
Jun  18 13:57:39 sanbox kernel: [    7.109328] asix: Unknown symbol  usbnet_set_settings
Jun 18 13:57:39 sanbox kernel: [    7.109538]  asix: disagrees about version of symbol usbnet_probe
Jun 18 13:57:39  sanbox kernel: [    7.109543] asix: Unknown symbol usbnet_probe
Jun  18 13:57:39 sanbox kernel: [    7.109752] asix: disagrees about version  of symbol usbnet_resume
Jun 18 13:57:39 sanbox kernel: [    7.109757]  asix: Unknown symbol usbnet_resume

...and from there, the NIC  won't show up any longer - no eth1 visible in ifconfig -a. Clearly, some  alternate driver (usbnet?) from compat-wireless has messed up the asix  driver from being able to start up. Any ideas on how to get that  restored?

---

### Post by aredubya on 2010-06-18
Reviewing lsusb output, I found the manufacturer and version string:

Bus 001 Device 003: ID 0b95:7720 ASIX Electronics Corp. AX88772

Digging around, I found another thread for another Ubuntu user noting similiar problems, indicating he'd found an alternate driver from the chipset manufacturer, available at:

[http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=86](http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=86)

[http://www.asix.com.tw/FrootAttach/driver/AX88772B_772A_760_772_178_LINUX2.6.32_Driver_v3.2.0_Source.tar.bz2](http://www.asix.com.tw/FrootAttach/driver/AX88772B_772A_760_772_178_LINUX2.6.32_Driver_v3.2.0_Source.tar.bz2)

I downloaded the source tarball and did a make/make install on it, then modprobe'd, but no luck:

root@sanbox:~/asix# modprobe asix
FATAL: Error inserting asix (/lib/modules/2.6.31-22-generic/kernel/drivers/net/usb/asix.ko): Unknown symbol in module, or unknown parameter (see dmesg)

The errors are the same sorts of "Unknown symbol" errors I'd found before. Perhaps it's my kernel parameters? I haven't done any direct recompilation, but have new-ish kernel headers, hence the lib/modules path noted above. Still stuck, unfortunately :(

---

### Post by justforsp on 2010-07-05
what is the version of the kernel are you using?

---

