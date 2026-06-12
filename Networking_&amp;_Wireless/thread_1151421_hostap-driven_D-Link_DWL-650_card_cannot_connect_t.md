---
title: "hostap-driven D-Link DWL-650 card cannot connect to network"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Jockey on 2009-05-06
[FONT=Trebuchet MS][SIZE=2][COLOR=Red]_[SIZE=5]Problem[/SIZE]_[/COLOR]
The hostap-driven [COLOR=Blue]D-Link DWL-650 wireless card (Intersil Prism 2.5 chipset, PCMCIA interface)[/COLOR] does not connect to network, e.g. cannot [FONT=Courier New]ping[/FONT] other hosts that is in the same subnet. **It DOES associate with a proper AP and get enough network-layer parameters set** (whether via [FONT=Courier New]dhclient[/FONT] or manual assignment).


_[SIZE=5][COLOR=Red]Details[/COLOR][/SIZE]_
After I plug the DWL-650 card into PCMCIA slot, from the output of [FONT=Courier New]iwconfig[/FONT] (see below) I see the interface [FONT=Courier New]wlan0[/FONT] has automatically associated with the AP whose ESSID is "[FONT=Courier New]TP-LINK_JSK[/FONT]" and BSSID is [FONT=Courier New]00:23:CD:85:A8:E4[/FONT]. Hence, of course, I can assert the DWL-650 card has been set up correctly. Now, I manully assign network-layer parameters as followings:
[/SIZE][/FONT]```
$ **sudo ifconfig wlan0 down**
$ **[COLOR=Black]sudo ifconfig wlan0 192.168.1.100 broadcast 192.168.1.255 netmask 255.255.255.0 up[/COLOR]**
```[FONT=Trebuchet MS][SIZE=2]
and from the output of [FONT=Courier New]ifconfig[/FONT] (see below) I can see that the interface has been activated successfully.

However, I cannot even [FONT=Courier New]ping[/FONT] the NAT router (see output of [FONT=Courier New]ping[/FONT] below). Routing table is okay, as I argue, since 192.168.1.1 and 192.168.1.100 with mask 255.255.255.0 are in the same network so no packets need forwarding at all. Anyway I add one new entry in the table though this makes no difference (see output of netstat below):
[/SIZE][/FONT]```
$ **sudo route add default gw 192.168.1.1 dev wlan0**
```[FONT=Trebuchet MS][SIZE=2]

This problem flys away once I choose [FONT=Courier New]orinoco_cs[/FONT] instead of [FONT=Courier New]hostap_cs[/FONT] to drive the card. Just comment out the entry
[/SIZE][/FONT]```
blacklist orinoco_cs
```[FONT=Trebuchet MS][SIZE=2]
in [FONT=Courier New]/etc/modprobe.d/hostap-utils[/FONT]. Operations are the same as above except "[FONT=Courier New]wlan0[/FONT]" changed to "[FONT=Courier New]eth0[/FONT]".

Is it caused by hostap? The reason to choose [FONT=Courier New]hostap_cs[/FONT] rather than [FONT=Courier New]orinoco_cs[/FONT] is that[/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2] with the latter[/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2] I cannot set host roaming mode to manual control (since no such private parameters defined), which is the key to my current work that is to implement a smooth 802.11 handoff scheme run as a user process, which requires to disable automatic handoff operation performed by the firmware and device driver.

Any effective solution or even just constructive suggestion? Thank you all!


_[SIZE=5][COLOR=Red]Ubuntu release[/COLOR][/SIZE]_
Ubuntu 8.10 (Intrepid Ibex)


_[SIZE=5][COLOR=Red]Wireless NAT router side[/COLOR][/SIZE]_
IP: 192.168.1.1
Mask: 255.255.255.0
MAC: 00:23:CD:85:A8:E4
ESSID: TP-LINK_JSK
Frequency/Channel: 2.437GHz/06
DHCP Server: Off

**[COLOR=Black]No access control and filter machanism enabled[/COLOR]**, say, shared keys, firewall, MAC-based access control, etc.. Actually I've disabled all these complicated stuff that may cause problems.


_[SIZE=5][COLOR=Red]Hardwares all right?[/COLOR][/SIZE]_
Absolutely. On Windows I can surf on the Internet without pains, which means **[COLOR=Black]both wireless NAT router and DWL-650 card are just all right[/COLOR]**.


_[SIZE=5][COLOR=Red]Various outputs[/COLOR][/SIZE]_
[/SIZE][/FONT]```
$ **uname -a**
Linux ibm-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
```[FONT=Trebuchet MS][SIZE=2]

[/SIZE][/FONT]```
$ **pccardctl ident**
Socket 0:
  product info: "D", "Link DWL-650 11Mbps WLAN Card", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
```[FONT=Trebuchet MS][SIZE=2]

[/SIZE][/FONT]```
$ **lspcmcia **
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:13.0)
Socket 0 Device 0:    [hostap_cs]        (bus ID: 0.0)
```[FONT=Trebuchet MS][SIZE=2]

[/SIZE][/FONT]```
$ **iwconfig **
lo        no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"TP-LINK_JSK"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:CD:85:A8:E4   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"TP-LINK_JSK"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:CD:85:A8:E4   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-57 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:32  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

pan0      no wireless extensions.
```[FONT=Trebuchet MS][SIZE=2]

[/SIZE][/FONT]```
$ **ifconfig wlan0**
wlan0     Link encap:Ethernet  HWaddr 00:40:05:ae:b9:a1  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:6859 (6.8 KB)
          Interrupt:3 Base address:0x100
```[FONT=Trebuchet MS][SIZE=2]

[/SIZE][/FONT]```
$ **netstat -rn**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
```[FONT=Trebuchet MS][SIZE=2]

[/SIZE][/FONT]```
$ **ping -c 4 192.168.1.1**
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable
From 192.168.1.100 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3016ms
, pipe 3
```[FONT=Trebuchet MS][SIZE=2]

--EOF--
[/SIZE][/FONT]

---

### Post by Jockey on 2009-05-07
bump.

---

