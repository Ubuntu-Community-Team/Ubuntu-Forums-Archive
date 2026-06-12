---
title: "Need help setting up as a router in 12.10 (Wireless AP enabled)"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by Apache0715 on 2012-12-21
Ive been using Ubuntu since 7.10, casually. I am still new at a lot of commands, google helps me a lot. I have an issue with trying to get my network to work. 

Information on setup:
Ubuntu 12.10 PC:
Mini ITX Gigabyte H61N USB3 mobo 
8GB Memory
Intel G640T @ 2.4ghz
60Gb HD
Zyntel Wireless N dongle

Client PC
Lenovo Y480 with Windows 7

Other Clients:
Motorola Droid X
Apple Ipad Gen 4
Apple MBP
Asus TF201 droid tablet

Network Setup:
ISP: Sniperhill
Connection type: Cat 5e hardwire only 
To connect to internet, Web based authentication (think of hotel internet access)

Issue: 
Would like to set up ubuntu 12.10 as wireless AP so devices may connect to the network via wireless.  Preferably without having to login on each device, but if I can only set it up to where each device can sign in individually that will work too.

I have already successfully set up Hostapd to act as a AP with DHCP capabilities. Devices can connect to the hotspot and obtain a local IP address (Behind the Ubuntu PC)

Im primarily testing with my Windows laptop. I have been able to get to load the login page and successfully login. After that, I can not browse the internet. I have also tried logging in on the Ubuntu computer, with success I can access the internet on the Ubuntu computer, but not any clients.

I am using HOSTAPD for the AP, IPTABLES for nat and filtering, and ISC-DHCP-SERVER for DHCP.

Others here have succesfully used TPLINK routers to allow one person to login, and the others on the TPLINK AP to browse without signing on. This is my goal with the ubuntu computer.

ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 90:2b:34:38:11:14  
          inet addr:10.165.0.13  Bcast:10.165.3.255  Mask:255.255.252.0
          inet6 addr: fe80::922b:34ff:fe38:1114/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13609799 (13.6 MB)  TX bytes:2736418 (2.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:564780 (564.7 KB)  TX bytes:564780 (564.7 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 50-67-F0-11-45-3E-3A-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18580188 (18.5 MB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 50:67:f0:11:45:3e  
          inet addr:10.10.0.1  Bcast:10.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5267:f0ff:fe11:453e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:860247 (860.2 KB)  TX bytes:1312260 (1.3 MB)

```iptables --list output:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  10.10.0.0/16         anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```Not sure if the iptables --list command is right, but i figured i would post that. 

Any help would be appreciated. I have been using howto's found online and Im not 100% sure on how iptables work.

I hate having to use this ISP but its the only thing we have here in Afghanistan. I know Ubuntu can be made to do it if a TPLink router can do it. Its funny how only certain models can. I think I have to also mask the traffic's MAC addresses so that all traffic to the ETH0 port appears to be originated from a single MAC address, not sure if IPTABLEs can do that.

---

