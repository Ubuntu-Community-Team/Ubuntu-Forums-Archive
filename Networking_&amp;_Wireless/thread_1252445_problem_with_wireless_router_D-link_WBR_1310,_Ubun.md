---
title: "problem with wireless router D-link WBR 1310, Ubuntu 8.04"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by imapostdoc on 2009-08-28
Dear forum members,

today we installed our new D-link WBR-1310 router and tried desperately to connect wirelessly. I didn't have problems previously at airports and coffee shops. Right now only the ethernet cable connection functions. The cable company person didn't have problems to connect his Windows laptop. Here are some diagnostic data, I hope it is not too many (or too few). Any help is greatly appreciated.

Sincerely,
Peter
```

 lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

```

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:94:e6:1e  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe94:e61e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57279 errors:0 dropped:0 overruns:2 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65825978 (62.7 MB)  TX bytes:8460842 (8.0 MB)
          Interrupt:20 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110004 (107.4 KB)  TX bytes:110004 (107.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:c4:df:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:51300000-51304000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1a:73:c4:df:bd  
          inet addr:169.254.10.122  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:51300000-51304000 

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
  iwlist scan 
Cell 06 - Address: 00:1E:58:EE:4E:29
                    ESSID:"wevegotittoo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Please let me know if any other information is needed.
once again, many thanks.

---

### Post by jw5801 on 2009-09-10
So now that you've fixed your driver issues, can you connect to the router wirelessly? If not, what happens when you try?

---

### Post by imapostdoc on 2009-09-10
> **jw5801 said:**
> So now that you've fixed your driver issues, can you connect to the router wirelessly? If not, what happens when you try?

Hi, jw,
I still cannot connect wirelessly (it's only that firefox shows the usual message). We have a 24 character hexadecimal WEP, and a friend used it to hook up his Mac without problems. My wife had tried to connect with the network password disabled, that didn't work either. Are there any diagnostic commands that I could run?
Thank you much,
Peter

---

### Post by jw5801 on 2009-09-10
> **imapostdoc said:**
> Hi, jw,
I still cannot connect wirelessly (it's only that firefox shows the usual message). We have a 24 character hexadecimal WEP, and a friend used it to hook up his Mac without problems. My wife had tried to connect with the network password disabled, that didn't work either. Are there any diagnostic commands that I could run?
Thank you much,
Peter

The default gnome network manager has always been rather irritating and buggy. My first suggestion would be to try a different network manager. wicd is what I use.

---

### Post by imapostdoc on 2009-09-11
> **jw5801 said:**
> The default gnome network manager has always been rather irritating and buggy. My first suggestion would be to try a different network manager. wicd is what I use.

and that's all that was needed. It works perfectly.
So many thanks!
Peter

---

### Post by noelvh on 2009-09-11
I am glad you got it working, but my reply would have been to take that pice of crap back and get some thing better. D-Link is just plan junk!!!
And if the device is over a year old that do not offer the drivers for there stuff in the US.

Noel

---

