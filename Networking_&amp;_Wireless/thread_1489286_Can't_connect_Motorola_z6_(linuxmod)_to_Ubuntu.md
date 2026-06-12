---
title: "Can't connect Motorola z6 (linuxmod) to Ubuntu"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by guisardo on 2010-05-20
I'm trying to connect a Motorola z6 (with LinuxMod 2 aberrant ape)  to a laptop with Ubuntu 10 Lucid. I want to use the ftp and telnet that the linuxmod provides.

When I connect the phone to the usb, a connection to a device called "Motorola Motorola TTY-MDLM/BLAN Network Composite Demo" appers under wired connections.
The same device name appears on WinXP and it seems to work just fine in that os; but when Ubuntu tries to connect, it fails. I've install the Motorola Phone Tools in the XP... maybe that installed some extra drivers.

Is there any way to debug that connection? I don't know where to start.... Am I missing some ip configuration???

Any help will be appreciated.
Regard.

Guisardo

**[SIZE="4"][Solution][/SIZE]**
1.- Upgrade to Ubuntu 10.10.
2.- Removing the usb0 connection configuration from the network-manager.
3.- Temporally disabling the firewall.
4.- Connect the phone.
5.- Activate USBLan from the phone.
6.- Run:
```
sudo ifconfig usb0 192.168.16.1 broadcast 192.168.16.7 netmask 255.255.255.248 mtu 4500
```

Remember reactivating the firewall after you're done...
Cheers! :P

---

