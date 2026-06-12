---
title: "How to install D-Link wireless N 150 USB adapter DWA-125"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by saravana j on 2010-10-13
I want to install the DLink N150 (DWA-125) Wireless USB adapter in Ubuntu 9.04

if if go to

system-> administrator->log file viewer->dmesg

[    8.840794] type=1505 audit(1286918554.305:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2041
[    8.871542] type=1505 audit(1286918554.333:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2045
[    8.871619] type=1505 audit(1286918554.333:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2045
[    8.871647] type=1505 audit(1286918554.333:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2045
[    8.871675] type=1505 audit(1286918554.333:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2045
[    8.957547] type=1505 audit(1286918554.421:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2050
[    8.957705] type=1505 audit(1286918554.421:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2050
[    8.975965] type=1505 audit(1286918554.437:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2054
[   24.794950] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.794953] Bluetooth: BNEP filters: protocol multicast
[   24.810930] Bridge firewalling registered
[   25.906267] ppdev: user-space parallel port driver
[   26.141818] [drm] Initialized drm 1.1.0 20060810

srl@srl-lenovo-desktop:~$ lsusb
Bus 001 Device 007: ID 07d1:3c16 D-Link System 
Bus 001 Device 005: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
srl@srl-lenovo-desktop:~$ 


i dont know how to enable wireless.

any suggestion will be helpful

---

### Post by blakep2 on 2010-10-13
Just click the wireless icon at the top.  Make sure enable wireless is checked.

---

### Post by flash63 on 2010-10-13
Hello,
add device ID assignment for the driver rt2870sta.

See [http://ubuntuforums.org/showthread.php?p=9954424&posted=1#post9954424](http://ubuntuforums.org/showthread.php?p=9954424&posted=1#post9954424)

Replace the ID for the Config-File and the udev-Rule by the one you need.
Bus 001 Device 007: ID [COLOR="Red"]07d1:3c16[/COLOR] D-Link System

---

