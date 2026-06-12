---
title: "Wireless connection issues"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by Scooter1962 on 2009-03-07
I can't connect to a wired or wireless connection on my new laptop.
I've tried everything for the last 3 weeks, but have hit a wall at every turn.

I have burnt ndiswrapper and wireless tools onto a CD, but the package manager won't read the CD.  It also won't read the live Ubuntu  CD for package updates.

I'm posting my information as outlined in the sticky guide.

Grateful for any help.

1 ) Machine Brand and Model (PC/Laptop):
Code:
Toshiba Satellite L300 Laptop.  Vista Home Premium

Ubuntu is installed ‘inside windows’, that is, I have not partitioned the disk.

2 ) Wireless Brand, Model and Wireless Chipset:
Code:
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

(hint) use grep to get only information about the Wireless
Code:
$ lspci -nn | grep 'Wireless Brand'

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01) 
3 ) check interface:
Code:
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:7b:3f:c6  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:2962557841 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:219 Base address:0x8000 

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:62 errors:0 dropped:0 overruns:0 frame:0

          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:4368 (4.3 KB)  TX bytes:4368 (4.3 KB)

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

$ iwconfig wlan0

No such device when using my wireless domain name
4 ) Check for modules:
Code:
$ lsmod
user123@ubuntu:~$ lsmod

Module                  Size  Used by

ipv6                  263972  14 

nls_iso8859_1          12032  1 

nls_cp437              13696  1 

vfat                   18816  1 

fat                    57376  1 vfat

i915                   38144  2 

drm                    86056  3 i915


iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables


ath_pci                99096  0 

wlan                  211952  1 ath_pci

ath_hal               198864  1 ath_pci


(hint) search for the Wireless module
Code:
$ lsmod | grep "Atheros"

no reply
5 ) Kernel boot messages
Code:
$ dmesg
[    0.644612] NET: Registered protocol family 2

[    0.644738] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.644970] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.645481] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    0.645817] TCP: Hash tables configured (established 131072 bind 65536)

[   21.664161] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FBBO PQ: 0 ANSI: 5

[   21.664307] scsi 1:0:0:0: Attached scsi generic sg0 type 0

[   21.670543] scsi 6:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRTD08A 1.54 PQ: 0 ANSI: 5

[   21.670648] scsi 6:0:0:0: Attached scsi generic sg1 type 5

[   21.672042] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded


[   33.458814] ath_hal: module license 'Proprietary' taints kernel.

[   33.460941] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

[   33.474479] wlan: 0.9.4

[   33.481293] ath_pci: 0.9.4

[   33.481332] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[   33.481347] ath_pci 0000:03:00.0: setting latency timer to 64

[   33.529835] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

[   33.529850] ath_pci 0000:03:00.0: PCI INT A disabled


(hint) the same as in (4)

6 ) Network configuration
Code:
$ sudo lshw -C network
user123@ubuntu:~$ lshw -short  
WARNING: you should run this program as super-user. 
H/W path       Device  Class       Description 
============================================== 
                       system      Computer 
/0                     bus         Motherboard 
/0/0                   memory      942MiB System memory 
/0/1                   processor   Genuine Intel(R) CPU             575  @ 2.00G 
/0/100                 bridge      Mobile 4 Series Chipset Memory Controller Hub 
/0/100/2               display     Mobile 4 Series Chipset Integrated Graphics C 
/0/100/2.1             display     Mobile 4 Series Chipset Integrated Graphics C 
 Controller 
/0/100/1c              bridge      82801I (ICH9 Family) PCI Express Port 1 
/0/100/1c/0    eth0    network     RTL8101E/RTL8102E PCI Express Fast Ethernet c 
/0/100/1c.1            bridge      82801I (ICH9 Family) PCI Express Port 2 
/0/100/1c.1/0          network     AR242x 802.11abg Wireless PCI Express Adapter 
/0/100/1c.4            bridge      82801I (ICH9 Family) PCI Express Port 5 
/0/100/1d              bus         82801I (ICH9 Family) USB UHCI Controller #1 
/0/100/1d.1            bus         82801I (ICH9 Family) USB UHCI Controller #2 
/0/100/1d.2            bus         82801I (ICH9 Family) USB UHCI Controller #3 
/0/100/1d.3            bus         82801I (ICH9 Family) USB UHCI Controller #6 
/0/100/1d.7            bus         82801I (ICH9 Family) USB2 EHCI Controller #1 
/0/100/1e              bridge      82801 Mobile PCI Bridge 
/0/100/1f              bridge      ICH9M LPC Interface Controller 
/0/100/1f.2            storage     ICH9M/M-E SATA AHCI Controller 
/0/100/1f.3            bus         82801I (ICH9 Family) SMBus Controller 
/1             scsi6   storage      
/2             scsi7   storage      
/3             pan0    network     Ethernet interface 


 ) Scan for networks:
Code:
$ iwlist scan
hint) the same as in (3)
Code:
$ iwlist scan wlan0
 ) Ubuntu Version: 
Code:
$ 
9 ) Kernel/architecture (including 32 vs. 64 bit): 
Code:
$ uname -mr
2.6.27-7-generic i686 
10 ) Restarting the network:
Code:
$ sudo /etc/init.d/networking restart
Add this information to the post, even is the output is and error, and more if you have, and describe your issue.
__________________
lsb_release -d

Ubuntu 8.10

---

