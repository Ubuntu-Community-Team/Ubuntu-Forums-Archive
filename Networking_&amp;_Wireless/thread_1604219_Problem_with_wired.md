---
title: "Problem with wired"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by mystdeim on 2010-10-23
I bought a new desktop Lenovo and got problem: I can`t to connect to my local network

Some output:
```
$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82552 10/100 Network Connection (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```and
```
$ dmesg | grep eth
[    1.163490] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 44:87:fc:98:42:7d
```

```
cat /var/log/syslog | grep eth0
Oct 24 01:31:25 anovikov-desktop kernel: [    1.163490] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 44:87:fc:98:42:7d
Oct 24 01:31:25 anovikov-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0)
Oct 24 01:31:25 anovikov-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): carrier is OFF
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): now managed
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): bringing up device.
Oct 24 01:31:25 anovikov-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
```

I tried ifconfig eth0 up, but nothing...

Please, tell me how to enable it?

---

### Post by David Cash on 2010-12-06
I'm having exactly the same issue with a Lenovo Q150 - did you find a solution?

---

