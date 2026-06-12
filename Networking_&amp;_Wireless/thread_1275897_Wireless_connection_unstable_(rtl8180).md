---
title: "Wireless connection unstable (rtl8180)"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by the_uncle on 2009-09-26
Hi.
I have a problem related to wireless LAN connection.
My local network comprises a DSL modem-router plus access point and a wireless range extender to extend the coverage of the wireless signal.
The connection to the internet via Ethernet cable on the router and wireless connection to the router is working smoothly. However I have problems in connecting to the internet through the range extender.

After some time (10 to 30 minutes) the connection to the range extender is dropped and the only way to bring it up again is to restart the networking with the init.d scripts or to manually re-associate the range extender mac address using iwconfig.

My wlan is encrypted with a 128-bit WEP (due to the presence of other clients that don't support any other encryption), but the problem shows up even with no encryption.

I normally use static IP address assignment, but the problem shows up even with DHCP.

I took care of properly configuring the range extender (manual assignment of the access point MAC, same wireless channel, ...)
I've tried to replace the range extender with a different brand/model, with no effect.

Also installing linux-backports as suggested in another thread didn't do the job.

FYI, I'm using an up-to-date Xubuntu 9.04 Jaunty x86_64 (kernel 2.6.28-15-generic), provided with an RTL-8185 chipset-based pci card driven by rtl8180 kernel module.

I've experienced the same erratic behaviour on my machine under Debian Lenny 5.0.3, the latest Archlinux available, and Gentoo 11.1.

A different machine equipped with Ubuntu 8.10 shows the same crap.
The connection gets lost both when I manually configure the connection (edit of /etc/network/interfaces and /etc/resolv.conf) and when I use the Network Manager of Ubuntu or Wicd.


In the attachments you can find the output of:
lspci
lshw -C Network
ifconfig -a
iwlist wlan0 scan
iwconfig (before and after the disconnection)
dmesg | grep wlan0 (before and after the disconnection)

Any suggestion or idea would be appreciated.
Thank you.

---

### Post by the_uncle on 2009-09-30
bump.

---

