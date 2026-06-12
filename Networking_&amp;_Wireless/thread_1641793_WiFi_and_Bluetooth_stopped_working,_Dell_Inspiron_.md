---
title: "WiFi and Bluetooth stopped working, Dell Inspiron 1525"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by StiltonSandwich on 2010-12-09
I have a Dell Inspiron 1525 with an Intel Corporation PRO/Wireless 3945ABG [Golan] wireless card and an internal USB Dell Computer Corp. Wireless 355 Bluetooth adapter. (According to lspci and lsusb.)

This hardware has always worked fine with Ubuntu (Kubuntu actually), and on 10.04 for at least six months.

Two days ago it suddenly stopped working; both the wireless and the Bluetooth at the same time. My wired Ethernet connection still worked, however.

I tried various solutions. Repeatedly checked that the hardware wireless switch was in the "on" position, checked there were no strange settings in the BIOS. I rebooted numerous times. I tried booting the previous kernel in case the recent kernel update caused the problem. I tried to follow some troubleshooting guides, but they all seemed to focus on people using manual, static wireless configurations; I didn't want to mess things up for NetworkManager by configuring anything like that. (It was hard to browse for solutions while cramped up on the floor in a corner, tethered to a half-metre long Ethernet cable with the screen facing the wrong way and a cupboard door trying to close itself on me!)

Blueman-manager (I use this instead of KBluetooth) reported that Bluetooth was turned off. It was impossible to turn it on. Any attempt to turn it on would cause (after some time) an error saying that Bluetooth could not be enabled because the device did not exist (I cannot remember the exact error text).

KNetworkManager simply acted as if there was no wireless card installed.

lshw indicated that the wireless card was "DISABLED".

iwlist scan said that wlan0 (the wireless interface) did not support scanning because it was disabled.

Eventually, I decided to run:
sudo aptitude reinstall network-manager network-manager-kde
to reinstall NetworkManager.

After a reboot, this fixed the problem. Wireless and bluetooth had returned to normal operation.

I am just posting this here in case anyone else is searching for a solution to a similar problem.

I would be interested to know why re-installing network-manager had any effect on Bluetooth, if anyone knows. Or, indeed, why the problem occurred in the first place. I do sometimes use Bluetooth to tether my phone as a modem, which makes a "Mobile Broadband" network interface appear in NetworkManager, however, I would not have thought this would cause Bluetooth in general to depend on having a working NetworkManager.

---

