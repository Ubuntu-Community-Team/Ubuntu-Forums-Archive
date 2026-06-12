---
title: "Wireless connects, but very slow and times out (12.04; Macbook 2,1)"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by Mak0rz on 2012-06-10
I'm using a Macbook 2,1 with Xubuntu 12.04 and it seems to have trouble connecting to my home network. The internet connection says the signal is strong, but items still take a very long time to load and often times out.

The system has no trouble connecting to the wireless networks at my university and my girlfriend's house, but for some reason is very crabby with the connection at *my* house. I'm dual-booting MacOSX and, for what it's worth, it and my Windows computer (Toshiba Satellite L675 running Windows 7) can connect to all of the above-mentioned networks without any issue.

I attempted the solutions in [this thread](http://ubuntuforums.org/showthread.php?t=1859558). Two common solutions were presented by Wildmanne39 in that thread. Disabling hardware encryption did help speed it up a little, but it is still slower than my other OSes most of the time and time-outs/disconnects are still very common. The other solution was to disabling 'n' protocols, however this results in an error message on my machine:

```

mak0rz@mak0rz-MacBook:~$ sudo ifconfig wlan0 down
mak0rz@mak0rz-MacBook:~$ sudo rmmod -f ath9k
mak0rz@mak0rz-MacBook:~$ sudo modprobe ath9k 11n_disable=1
FATAL: Error inserting ath9k (/lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
mak0rz@mak0rz-MacBook:~$ sudo ifconfig ath9k up
wlan0: ERROR while getting interface flags: No such device

```

**My hardware, drivers, and network information are as follows:**

```

mak0rz@mak0rz-MacBook:~$ lspci|grep Network
02:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)

mak0rz@mak0rz-MacBook:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"GammaNet 6"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:19:5B:5F:82:51   
          Bit Rate=162 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:116   Missed beacon:0

mak0rz@mak0rz-MacBook:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:19:e3:03:a3:93  
          inet addr:192.168.0.178  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe03:a393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:925442 (925.4 KB)  TX bytes:253204 (253.2 KB)

mak0rz@mak0rz-MacBook:~$ lsmod|grep ath
ath9k                 117425  0 
mac80211              436455  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath

mak0rz@mak0rz-MacBook:~$ dmesg|grep ath
[   21.418653] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.418669] ath9k 0000:02:00.0: setting latency timer to 64
[   21.548760] ath: EEPROM regdomain: 0x64
[   21.548763] ath: EEPROM indicates we should expect a direct regpair map
[   21.548767] ath: Country alpha2 being used: 00
[   21.548769] ath: Regpair used: 0x64
[   21.597466] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   21.600792] Registered led device: ath9k-phy0

mak0rz@mak0rz-MacBook:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:ef:f8:fc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:d0200000-d0203fff ioport:1000(size=256) memory:d0800000-d081ffff
  *-network
       description: Wireless interface
       product: AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:e3:03:a3:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic firmware=N/A ip=192.168.0.178 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d0100000-d010ffff

mak0rz@mak0rz-MacBook:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:5F:82:51
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"GammaNet 6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063dfe86180
                    Extra: Last beacon: 101312ms ago
                    IE: Unknown: 000A47616D6D614E65742036
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C334E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409070700000000000000000000000000000000000000
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D1609070300000000000000000000000000000000000000
                    IE: Unknown: DD980050F204104A000110103B00010310470010C6506C1BFD133407B38FA5EE0D267DDB10440001021021000E442D4C696E6B2053797374656D7310230019576972656C6573732044726166742031316E20526F75746572102400074449522D363535104200046E6F6E651054000800060050F204000110110019576972656C6573732044726166742031316E20526F75746572100800020004

eth0      Interface doesn't support scanning.

mak0rz@mak0rz-MacBook:~$ lsb_release -d && uname -mr
Description:	Ubuntu 12.04 LTS
3.2.0-24-generic i686

mak0rz@mak0rz-MacBook:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```

Thanks for your help.

---

### Post by Mak0rz on 2012-06-11
Sorry to bump, but this is affecting my computer's ability to update as well. Repositories often fail to update (takes several tries to get the update list) and packages often fail to download.

Does anyone have any idea what's happening?

---

