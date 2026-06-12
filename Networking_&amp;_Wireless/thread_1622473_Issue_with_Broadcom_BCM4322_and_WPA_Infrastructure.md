---
title: "Issue with Broadcom BCM4322 and WPA Infrastructure network"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by Anders H on 2010-11-15
Hello all, 

I have searched around and found nothing specific to my problem 

I am running a HP Pavillion DV6 - 1030us Laptop with a Broadcom BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) using the Broadcom STA wireless driver from the Add. Drivers list under "System -> Administration" Under a dual boot with Win 7 and Ubuntu 10.10 kernel 2.6.35-22-generic x86_64

Under Ubuntu 10.04 my wireless seemed to work fine but with the upgrade I have had difficulty accessing networks. Specifically my School's WPA Infrastructure based wireless network. I have spoken to the tech assistance department at my school and checked to make sure that my network settings were good, they were. 

I have attempted to reinstall the driver for the card and this trick,

[I]Go into synaptic package manager and... 
 
completely remove bcmwl-kernel-source AND dkms 
 
then, whilst still in synaptic  
 
install bcmwl-kernel-source 
[/I]
With no success. 

I believe I am using the right driver, however the most common error message that I get from the network "UNR-WPA" is a request for authentication, again these are the same settings that I have verified with my school's tech department. 

I don't know how much this will help but this is the output from the following commands. 

I know how to run in terminal and have fixed a number of issues just by looking at the boards, but "I don't speak geek" as it were so the out put below is useless to me without some help. 

Thank you in advance.

```
ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:23:8b:98:db:cc  
          inet addr:134.197.105.75  Bcast:134.197.105.255  Mask:255.255.254.0
          inet6 addr: fe80::223:8bff:fe98:dbcc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9791698 (9.7 MB)  TX bytes:1028285 (1.0 MB)
          Interrupt:46 

eth1      Link encap:Ethernet  HWaddr 00:21:00:ca:42:3c  
          inet6 addr: fe80::221:ff:feca:423c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:14896
          TX packets:5 errors:39 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2025 (2.0 KB)  TX bytes:130 (130.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:311853 (311.8 KB)  TX bytes:311853 (311.8 KB)

```

```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:16 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

```

```
lshw -C network

 CSI                      
  *-network        
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:ca:42:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:98:db:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=134.197.105.75 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

```

```
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:1E:87:B6:01
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1A:1E:87:B6:02
                    ESSID:"UNR-Outside"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 2E:22:64:D7:EE:43
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Frequency=2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-46 dBm  Noise level:-94 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 04 - Address: 00:1A:1E:87:BB:C0
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-40 dBm  Noise level:-94 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:1A:1E:87:BB:C1
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-43 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:1A:1E:87:C9:01
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-80 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 00:1A:1E:87:B5:40
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-62 dBm  Noise level:-91 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:1A:1E:87:B5:41
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 09 - Address: 00:1A:1E:87:B9:60
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-89 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 10 - Address: 00:1A:1E:87:B9:61
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 11 - Address: 00:1A:1E:87:B8:D0
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:5.19 GHz
                    Quality:4/5  Signal level:-62 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 12 - Address: 00:1A:1E:87:B8:D1
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=5.19 GHz
                    Quality:4/5  Signal level:-62 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 13 - Address: 00:1A:1E:87:B6:50
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:5.23 GHz
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 14 - Address: 00:1A:1E:87:B6:51
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=5.23 GHz
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 15 - Address: 00:1A:1E:87:B5:50
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:5.755 GHz
                    Quality:2/5  Signal level:-75 dBm  Noise level:-91 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 16 - Address: 00:1A:1E:87:B5:51
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=5.755 GHz
                    Quality:2/5  Signal level:-75 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 17 - Address: 00:1A:1E:87:BB:D0
                    ESSID:"UNR-Guest"
                    Mode:Managed
                    Frequency:5.795 GHz
                    Quality:5/5  Signal level:-53 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 18 - Address: 00:1A:1E:87:BB:D1
                    ESSID:"UNR-WPA"
                    Mode:Managed
                    Frequency=5.795 GHz
                    Quality:5/5  Signal level:-53 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on

```

---

### Post by bkratz on 2010-11-15
post 2 in this report may help, but it refers to 10.04 so read with care.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/560434](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/560434)

---

### Post by Anders H on 2010-11-15
First of all thank you for your help 

Just so I'm reading this right, this work around calls for running 

"modprobe" with the arguments (correct term?) "-r wl" 

then uninstalling the current version of "bcmwl-kernel-source" what ever that may be (I need to look this up in Synaptic right?)  

and install "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4"

and run "modprobe" again with the argument "wl" 

In that case is "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4" compatable with Ubuntu 10.10 and my current Kernel? 

I just want to make sure because this seems to be messing with the Kernel and I don't want to do that without knowing if it will screw anything up.

---

### Post by bkratz on 2010-11-15
The 5.1xx version is actually the older version, the newer one (and the only one I see in Synaptic) is 5.60.246.6. You correctly understand what they are saying though. I will spend a little time with googlubuntu and see if I can find it.

---

### Post by bkratz on 2010-11-15
A bit more information--if you look at the actual STA site

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The most current version is 5.60.246.6 ( it appears to have been just released in Oct) while your listing above shows

 [COLOR="DarkOrange"]driverversion=5.60.48.36[/COLOR].
 Perhaps their latest version corrects the WPA deficiency. At least it would be worth your time to look at the readme on that site.

I did find the old files, at

[http://pf.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://pf.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)  , but you should probably consider the first option.

---

### Post by Anders H on 2010-11-17
I currently don't have 5.60.246.6 listed in my Synaptic. I've tried to reload the synaptic files list several times with no new results. I have a copy of the driver downloaded from the website but I don't have any idea on how to get it insalled. I'm looking at the reme file but I'm unfamilar with the insturctions.

---

### Post by mkiwala on 2010-11-28
I'm having this problem on my macbook pro which also using the bcm4322 chipset.

I've installed the 5.60.246.6 version of the broadcom drivers successfully, but still am not able to log onto my home wpa network.  I used iwevent to log these messages while I used nm-applet to try to log into my home network:


```
21:55:09.568788   eth1     Set Mode:Managed
21:55:09.568830   eth1     Set Frequency:24.12 GHz
21:55:09.568970   eth1     Set ESSID:"boomshakalaka"
21:55:14.674298   eth1     Custom driver event:Conn AuthTimeout 02 00
21:55:14.674350   eth1     Custom driver event:Conn ConfigMismatch 01 00
21:55:25.599051   eth1     Set Mode:Managed
21:55:25.599095   eth1     Set Frequency:24.12 GHz
21:55:25.599146   eth1     Set ESSID:"boomshakalaka"
21:55:30.691532   eth1     Custom driver event:Conn AuthTimeout 02 00
21:55:30.691553   eth1     Custom driver event:Conn ConfigMismatch 01 00
21:55:41.628408   eth1     Set Mode:Managed
21:55:41.628447   eth1     Set Frequency:24.12 GHz
21:55:41.628497   eth1     Set ESSID:"boomshakalaka"
21:55:46.761583   eth1     Custom driver event:Conn AuthTimeout 02 00
21:55:46.761631   eth1     Custom driver event:Conn ConfigMismatch 01 00

```


Next I think I might try going a back to an older version of the driver if that's possible.

---

### Post by uncaspi on 2010-11-29
No don't go back to the older version. Check with lsmod if the security modules for the driver is loaded. Either lib80211 or 
ieee80211_crypt_tkip should be used by the wl driver.

---

### Post by zdenal on 2010-12-02
I had same problems with Broadcom driver on Lucid and Maverick.

In my post

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

I summarize some facts so you can check

a) If your Broadcom card is supported by the wl.ko driver
b) Use step by step HowTo to try fix your wireless problem

Hope this helps..

---

