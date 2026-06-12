---
title: "Error: &quot;Connection on WLAN interface failed&quot;"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by rsottini on 2009-07-10
Hello!
     I'm using Gnome on the great Ubuntu 9.04 but my boss teache me the new KDE (version 4.x), so I said "Why not? let's try this new gadget". I tried. Actually everything was going good, good colours, good software, I was going to "get married" with it untill I wanted to connect to a WiFi network and... "conection on WLAN interface failed" appeared on screen. Later the same luck happened with the wireless network of my house :mad:.
     I know, the problem is between the chair and the laptop :lolflag:, so please give me a hand 'cause I cannot solve this problem.

Roby
(Ushuaia, Argentina)

---

### Post by krush on 2009-07-11
&#1072; network-manager &#1089;&#1090;&#1086;&#1080;&#1090;?

---

### Post by Crafty Kisses on 2009-07-11
First we need some information about the wireless card. So open up a Terminal, **(Applications->Accessories->Terminal) ** then from there you need to run the following commands:
```
lspci
lsusb
ifconfig
iwconfig
lshw -C network
```
That will give me and other people some information on your current setup, then once we have the information we need, we can help you on your current problem.

---

### Post by djakay on 2009-07-27
I'm having a problem with WLAN as well i was able to connect to unsecured network, but when i try to connect at home it always fails, i've tried using different security modes and still no luck

```
alex@alex-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)                                                                                                   
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)                                                                                         
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)                                                                                            
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)       
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)                       
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)                       
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)               
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)               
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)               
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)               
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)                 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)                                       
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)                        
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)             
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller                            
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)       
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller                                         
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller             
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller              


alex@alex-laptop:~$ lsusb                                                                                    
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                               
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                               
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                               
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader                             
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                               
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                               


alex@alex-laptop:~$ ifconfig                                                                                 
eth0      Link encap:Ethernet  HWaddr 00:15:b7:7e:d6:ec                                                      
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                               
          collisions:0 txqueuelen:1000                                                                       
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                             
          Memory:ffce0000-ffd00000                                                                           

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                             
          RX bytes:7704 (7.7 KB)  TX bytes:7704 (7.7 KB)        

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:5c:e8:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-5C-E8-93-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                         
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                         
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                       
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

alex@alex-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

alex@alex-laptop:~$

```

---

