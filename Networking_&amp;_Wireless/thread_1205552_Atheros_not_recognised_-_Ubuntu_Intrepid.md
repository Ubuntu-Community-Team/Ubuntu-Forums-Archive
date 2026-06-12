---
title: "Atheros not recognised - Ubuntu Intrepid"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by cupevampe on 2009-07-06
Hello everyone, since a few days, possibly a couple of weeks, my wifi is not shown in the network manager menu.

I have been requested in another post to run the following commands:

adama@adama:~$ lsmod | grep ath
ath_pci                99096  0 
wlan                  211824  1 ath_pci
ath_hal               198864  1 ath_pci

adama@adama:~$ sudo rmmod ath5k
[sudo] password for adama: 
ERROR: Module ath5k does not exist in /proc/modules
adama@adama:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
adama@adama:~$ sudo modprobe ath5k
FATAL: Module ath5k not found.
adama@adama:~$ dmesg | grep -e ath -e wlan
[   18.370842] ath_hal: module license 'Proprietary' taints kernel.
[   18.372963] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   18.387524] wlan: 0.9.4
[   18.412060] ath_pci: 0.9.4
[   18.412170] ath_pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.412243] ath_pci 0000:04:00.0: setting latency timer to 64
[   18.460881] ath_pci 0000:04:00.0: PCI INT A disabled
adama@adama:~$ lspci -nn | grep Atheros
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
adama@adama:~$ 

My kernel version is 2.6.27-14-generic
possibly the issue started after a kernel upgrade, but I cannot be sure about it.
ANy hint would greatly help

tha!

Alex

---

### Post by ibutho on 2009-07-06
There are several possible solutions to your problem in this [thread]("http://ubuntuforums.org/showthread.php?t=967654").

---

### Post by cupevampe on 2009-07-06
ok i'll check that.

let me just add the following in case it can be useful to someone. :)
any help is greatly appreciated!

adama@adama:~$ uname -a
Linux adama 2.6.27-14-generic #1 SMP Tue Jun 30 19:57:39 UTC 2009 i686 GNU/Linux
adama@adama:~$ lspci | grep -i net
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
adama@adama:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

adama@adama:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:87:eb:f9  
          inet addr:89.125.6.132  Bcast:89.125.7.255  Mask:255.255.254.0
          inet6 addr: fe80::203:dff:fe87:ebf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1448  Metric:1
          RX packets:25814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25576988 (25.5 MB)  TX bytes:3272561 (3.2 MB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7105 (7.1 KB)  TX bytes:7105 (7.1 KB)

---

### Post by cupevampe on 2009-07-06
thanks, installing the backports solved the issue!

---

