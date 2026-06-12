---
title: "Wireless won't connect - 7.10AMD64"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Dusenberg on 2009-01-07
I have fitted Peak PCI wireless card to my AMD64 PC and I can't get it to see or connect to my wireless lan.  My laptop connects ok (how I'm typing this).  I have followed instructions on bapoumba's sticky:  Help please!?

> 
lspci 
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

 lsusb (all output)
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0411:0089 MelCo., Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

root@PC1:/home/j# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:12:0E:9A:B7:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:130 dropped:28 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:13524 (13.2 KB)
          Interrupt:20 Memory:ffffc20000330c00-ffffc20000330d00 

 802.11b/g  Mode:Managed  Frequency=2.447 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
ieee80211_rtl          88336  1 r8180

dmesg:
[   36.066118]  hda: hda1 hda2 < hda5<7>rtl_ieee80211_crypt: registered algorithm 'NULL'
[   36.135654] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[   36.135657] rtl_ieee80211_crypt: registered algorithm 'WEP'
[   36.135659] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[   36.154488] 
[   36.154490] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   36.154493] Copyright (c) 2004-2005, Andrea Merello
[   36.154494] rtl8180: Initializing module
[   36.154495] rtl8180: Wireless extensions version 22
[   36.154497] rtl8180: Initializing proc filesystem
[   36.154553] rtl8180: Configuring chip resources
[   36.154567] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[   36.154610] rtl8180: Memory mapped space @ 0xfeaffc00 
[   36.154753] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[   36.154759] rtl8180: This is a PCI NIC
[   36.154761] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[   36.160954] rtl8180: Card MAC address is 00:12:0e:9a:b7:42
[   36.176407] rtl8180: EEPROM version 105
[   36.178469] rtl8180: Card reports RF frontend Realtek 8225
[   36.178470] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[   36.178472] rtl8180: WW:use it with care and at your own risk and
[   36.178474] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[   36.178476] rtl8180: Energy threshold: b
[   36.178478] rtl8180: PAPE from CONFIG2: 6
[   36.178577] rtl8180: IRQ 20
[   36.178705] rtl8180: Driver probe completed
.............
[   67.453913] rtl8180: Setting SW wep key
[   67.554903] audit(1231345723.962:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4864 profile="/usr/sbin/cupsd"

root@PC1:/home/j# lshw -C network
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 20
       serial: 00:12:0e:9a:b7:42
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g

root@PC1:/home/j# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:48:4D:B2
                    ESSID:"JL01"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 1224ms ago
          Cell 02 - Address: 00:1F:33:86:3A:90
                    ESSID:"norka"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 1619ms ago

root@PC1:/home/j# lsb_release -d
Description:    Ubuntu 7.10

root@PC1:/home/j# uname -mr
2.6.22-16-generic x86_64

root@PC1:/home/j# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 



---

### Post by Dusenberg on 2009-01-08
Anyone willing to help here???? :o

---

