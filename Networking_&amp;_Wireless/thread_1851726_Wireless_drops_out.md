---
title: "Wireless drops out"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by nbxmike on 2011-09-28
I have an Acer Aspire 5516 with integrated Broadcom wireless.  I have tried the sticky remedies and I can not seem to get a reliable connection.  I can connect for a few seconds to a few minutes, but invariably the link drops and I need to stop and start (via netmanager icon menu) the network to get reconnected.  I originally tried enabling the proprietary Broadcom driver, that failed so I purged that and installed b43, failure again, I downloaded and built the Broadcom driver, again failure.  I have tried two different wireless access points, one using WEP and the other using WPA2.  I have tried enabling and disabling net boot in the BIOS.  So, per the guideline here are the diagnostics:

PC - Acer 5516-5474, 2 gigabytes RAM, Ubuntu 11.04 AMD64 installed from the desktop distro

ash@river:~$ lspci | grep BCM
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


ash@river:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:24:2c:a2:2c:ef  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fea2:2cef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:12279
          TX packets:14 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24266 (24.2 KB)  TX bytes:4030 (4.0 KB)
          Interrupt:18 

ash@river:~$ iwconfig eth1
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:192  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


****************** I'm communicating on this "Not-Associated" link



ash@river:~$ lsmod | grep wl
wl                   2568244  0 
lib80211               14991  2 lib80211_crypt_tkip,wl

ash@river:~$ dmesg | grep "wl\|BCM\|eth1"
[   14.611992] wl: module license 'unspecified' taints kernel.
[   15.741786] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.741795] wl 0000:02:00.0: setting latency timer to 64
[   15.943861] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[   27.060023] eth1: no IPv6 routers present

ash@river:~$ iwlist scan eth1
iwlist: unknown command `eth1' (check 'iwlist --help').
ash@river:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ash@river:~$ iwlist scan eth1
iwlist: unknown command `eth1' (check 'iwlist --help').

ash@river:~$ lsb_release -d
Description:    Ubuntu 11.04
ash@river:~$ uname -mr
2.6.38-11-generic x86_64

ash@river:~$ sudo /etc/init.d/networking restart
[sudo] password for ash: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                           [ OK ] 


Thoughts??

---

