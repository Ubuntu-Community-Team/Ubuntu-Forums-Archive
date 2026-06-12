---
title: "rtl8187se and networking problems in Maverick"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jon.reeve on 2010-08-29
Just upgraded to Maverick and my network card stopped working. This is on an MSI Wind U100 with an rtl8187se card. When I plug in a USB wifi card, everything works fine. Any ideas on how to get my built-in wifi card to work?

---

### Post by VinDSL on 2010-08-30
Are all of your onboard devices enabled in BIOS?!?!?

---

### Post by jon.reeve on 2010-08-30
I didn't disable anything in BIOS, between Lucid and Maverick, so I doubt it could have anything to do with that. The wifi light is on.

---

### Post by VinDSL on 2010-08-30
> **jon.reeve said:**
> [...]The wifi light is on.Try running...

```
$ sudo dmesg | less
```

See if it's being recognized by Maverick at startup.

---

### Post by jon.reeve on 2010-08-31
This is what I'm getting: 

```
 [   18.392565] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
Aug 29 22:42:31 jon-laptop kernel: [   18.392571] Copyright (c) 2004-2005, Andrea Merello
Aug 29 22:42:31 jon-laptop kernel: [   18.392577] r8180: Initializing module
Aug 29 22:42:31 jon-laptop kernel: [   18.392583] r8180: Wireless extensions version 22
Aug 29 22:42:31 jon-laptop kernel: [   18.392589] r8180: Initializing proc filesystem
Aug 29 22:42:31 jon-laptop kernel: [   18.392662] r8180: Configuring chip resources
Aug 29 22:42:31 jon-laptop kernel: [   18.392702] r8180 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 29 22:42:31 jon-laptop kernel: [   18.413088] Linux agpgart interface v0.103
Aug 29 22:42:31 jon-laptop kernel: [   18.439453] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Aug 29 22:42:31 jon-laptop kernel: [   18.492298] r8180: Channel plan is 2
Aug 29 22:42:31 jon-laptop kernel: [   18.492304] 
Aug 29 22:42:31 jon-laptop kernel: [   18.492312] Dot11d_Init()
Aug 29 22:42:31 jon-laptop kernel: [   18.492322] r8180: MAC controller is a RTL8187SE b/g
Aug 29 22:42:31 jon-laptop kernel: [   18.494516] r8180: usValue is 0x100
Aug 29 22:42:31 jon-laptop kernel: [   18.494521] 
Aug 29 22:42:31 jon-laptop kernel: [   18.537394] r8180: EEPROM version 104
Aug 29 22:42:31 jon-laptop kernel: [   18.541643] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
...
Aug 29 22:42:31 jon-laptop kernel: [   18.815107] type=1400 audit(1283136118.409:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=541 comm="apparmor_parser"
Aug 29 22:42:31 jon-laptop kernel: [   18.815962] type=1400 audit(1283136118.409:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=541 comm="apparmor_parser"
Aug 29 22:42:31 jon-laptop kernel: [   18.816556] type=1400 audit(1283136118.413:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=541 comm="apparmor_parser"
Aug 29 22:42:31 jon-laptop kernel: [   18.840207] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input6
Aug 29 22:42:31 jon-laptop kernel: [   18.840451] usbcore: registered new interface driver uvcvideo
...
Aug 29 22:42:31 jon-laptop kernel: [   19.668848] r8180: Card successfully reset
Aug 29 22:42:31 jon-laptop kernel: [   20.405966] r8180: WIRELESS_MODE_G
Aug 29 22:42:31 jon-laptop kernel: [   20.405973] 
Aug 29 22:42:31 jon-laptop kernel: [   20.447070] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by jon.reeve on 2010-08-31
Never mind, update apparently fixed the problem; works fine now.

---

### Post by VinDSL on 2010-08-31
> **jon.reeve said:**
> Never mind, update apparently fixed the problem; works fine now.~Cool :D

Glad the mystery was [SOLVED].

I couldn't live without my Asus EeePC netbook!

You probably feel the same about your Wind...

---

### Post by bhaverkamp on 2010-08-31
Just dealt with this yesterday. You need the latest drivers. I googled for it, found it, installed it in under 10 minutes. I dont have the link handy but google is your friend. I got the driver from the vendors website.

---

### Post by bhaverkamp on 2010-08-31
[http://code.google.com/p/msi-wind-linux/](http://code.google.com/p/msi-wind-linux/)

---

