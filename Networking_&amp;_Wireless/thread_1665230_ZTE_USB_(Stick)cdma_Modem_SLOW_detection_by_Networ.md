---
title: "ZTE USB (Stick)cdma Modem: SLOW detection by NetworkManager"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by kiers on 2011-01-12
Hi all,
using Ubuntu 10.10; NetworkManager 0.8.1; ZTE CDMA USB Modem AC2736.

When i connect the dongle to the USB port on my computer it takes 4-5 MINUTES (!) for my modem to detect. I did try disabling ModemManager (ie. /usr/share/dbus-1/system-services/org.freedesktop.ModemManager.service) but that dint help any. In fact it prevented from my dongle being recognized as a modem at all!

Here in hopes of quick pertinent solutions, i am posting interesting part of my /vAR/log/messages digest here:
================
Jan 12 11:44:38 kiers-Desktop kernel: [  976.900518] usb 4-1: new full speed USB device using uhci_hcd and address 4
Jan 12 11:44:39 kiers-Desktop kernel: [  977.068062] scsi6 : usb-storage 4-1:1.0
Jan 12 11:44:39 kiers-Desktop usb_modeswitch: switching 19d2:fff5 (ZTE, Incorporated: USB Storage)
Jan 12 11:44:39 kiers-Desktop kernel: [  977.784046] usb 4-1: USB disconnect, address 4
Jan 12 11:44:41 kiers-Desktop kernel: [  979.264018] usb 4-1: new full speed USB device using uhci_hcd and address 5
Jan 12 11:44:41 kiers-Desktop kernel: [  979.429915] option 4-1:1.0: GSM modem (1-port) converter detected
Jan 12 11:44:41 kiers-Desktop kernel: [  979.430032] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
Jan 12 11:44:41 kiers-Desktop kernel: [  979.431938] option 4-1:1.1: GSM modem (1-port) converter detected
Jan 12 11:44:41 kiers-Desktop kernel: [  979.432036] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
Jan 12 11:44:41 kiers-Desktop kernel: [  979.434024] option 4-1:1.2: GSM modem (1-port) converter detected
Jan 12 11:44:41 kiers-Desktop kernel: [  979.434142] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
Jan 12 11:44:41 kiers-Desktop kernel: [  979.436026] option 4-1:1.3: GSM modem (1-port) converter detected
Jan 12 11:44:41 kiers-Desktop kernel: [  979.436131] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB3
Jan 12 11:44:41 kiers-Desktop kernel: [  979.438185] option 4-1:1.4: GSM modem (1-port) converter detected
Jan 12 11:44:41 kiers-Desktop kernel: [  979.438296] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB4
Jan 12 11:44:41 kiers-Desktop kernel: [  979.453952] scsi7 : usb-storage 4-1:1.5
Jan 12 11:44:41 kiers-Desktop usb_modeswitch: switched to 19d2:fff1 (ZTE, Incorporated: ZTE CDMA Tech)
Jan 12 11:44:42 kiers-Desktop kernel: [  980.468968] scsi 7:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
Jan 12 11:44:42 kiers-Desktop kernel: [  980.470957] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jan 12 11:44:42 kiers-Desktop kernel: [  980.484950] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Jan 12 11:47:29 kiers-Desktop pppd[2091]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jan 12 11:47:29 kiers-Desktop pppd[2091]: pppd 2.4.5 started by root, uid 0
Jan 12 11:47:29 kiers-Desktop pppd[2091]: Using interface ppp0
Jan 12 11:47:29 kiers-Desktop pppd[2091]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 12 11:47:30 kiers-Desktop pppd[2091]: PAP authentication succeeded
====================

note it's between 11:44 to 11:47 that Network Manager is "busy" or "lost" doing modeswitches etc. God knows. But it seems like an inordinate wait for sticking in a USB stick-modem.

Any suggestions? Could it be that ttyUSB0 (which is the MODEM part of the stick) is being delayed because "GSM Modem converter" is also being associated with ttyUSB1-4 ??

---

### Post by Pathan on 2011-05-07
Same problem here. Were you able to find any solution?

---

