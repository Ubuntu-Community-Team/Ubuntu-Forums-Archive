---
title: "System monitor doesn't show internet traffic"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by zizaoui on 2011-03-08
Hi all.

Ubuntu system monitor applet doesn't show internet traffic although my wireless is working just fine.
I use a conky to monitor bandwidth through vnstat and had no problem till I upgraded to maverick. 

statistics:

**ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:24:d2:c4:3e:da  
          inet adr:192.168.0.100  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::224:d2ff:fec4:3eda/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:19 Mémoire:f80e0000-f80e0100

**lspci -nn
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. 
RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 
02)

14:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)


**iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"Tsl0919"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:F9:55:20   
          Bit Rate=54 Mb/s   
          Retry0n   RTS thr0ff   Fragment thr0ff
          Power Management0ff
          Link Quality=86/100  Signal level=-57 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

**iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:F9:55:20
                    ESSID:"Tsl0919"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key0n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=84/100  Signal level=-55 dBm  Noise level=-112 dBm
                    Extra: Last beacon: 3ms ago

vboxnet0  Interface doesn't support scanning

**"/etc/network/interfaces" output:
auto lo
iface lo inet loopback

**"sudo /ect/init.d/networking restart"  reads:
 sudo: /ect/init.d/networking: command not found


**uname -r
2.6.35-27-generic

How can I get traffic network showing in system monitor? 

Thanks.

---

### Post by zizaoui on 2011-03-09
Installing the latest rtl8192e linux driver resolves the problem. There was a conflict between rtl8192e_pci and rtl8192se_pci that the new driver fixes.
All credits to **[eldergs]("http://ubuntuforums.org/member.php?u=1245408") **([http://ubuntuforums.org/showthread.php?t=1689148&page=4](http://ubuntuforums.org/showthread.php?t=1689148&page=4) ).

---

