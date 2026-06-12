---
title: "No conection with WG311 or WET11"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by AcerM on 2009-10-30
Hello All

I was attempting a long overdue upgrade of my Ubuntu software. After the first upgrade from 8.4 to 8.10 (yes its that over due), my wireless PCI card (Netgear WG311) would not connect to the net. It had problems prior but was still usable. When the card was originally installed i got it to function through the instructions from WifiDocs. This involved the Windows drivers and ndiswrapper.

I attempted to circumvent the problem by connecting a wireless bridge (Linksys WET11) to my ethernet. However this has not helped me solve anything. Both the bridge and card works perfectly in Windows so i know the SSID and WEP are correct and the hardware hasnt failed.

Im looking for suggestions or instructions on how i can find the problem and correct it. Despite using Ubuntu alot, i dont know much about linux. I just know that Ubuntu (once you get it how you want it) is very stable. Hopefully one of you wise individuals will take pity on this incompetant user and provide some assistance.

Signed AcerM

P.S.
Dont know if it matters but once i have net connection again I will be upgrading to the current version of software. So if you think that the eventual solution might not make it through future upgrades. Do please mention that.

---

### Post by AcerM on 2009-10-31
Well after several attmepts to fix it myself i realized i hadnt posted any appreciable info about my situation so here we go.

```
$ lspci -nn | grep "Marvell"

00:07.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

$ ifconfig wlan2
wlan2     Link encap:Ethernet  HWaddr 00:1e:2a:c2:20:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:dffe0000-dfff0000 

$ iwconfig wlan2
wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod | grep "ndiswrapper"
ndiswrapper           196380  0 
usbcore               149616  5 ndiswrapper,usbhid,uhci_hcd,ehci_hcd

$ dmesg | grep "ndiswrapper"
[   21.601067] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   21.646224] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[   21.646680] ndiswrapper 0000:00:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.649671] ndiswrapper: using IRQ 18
[   21.910997] ndiswrapper: changing interface name from 'wlan0' to 'wlan2'
[   21.920567] usbcore: registered new interface driver ndiswrapper

$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: wlan2
       version: 03
       serial: 00:1e:2a:c2:20:9b
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.53+NETGEAR,02/22/2005,3.1.1.7 latency=32 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:76:b6:bf:f6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

$ iwlist wlan2 scan
wlan2     Scan completed :
          Cell 01 - Address: 00:0F:66:35:99:0E
                    ESSID:"CTHULHU"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:95:6C:99:54
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

$ lsb_release -d
Description:	Ubuntu 8.10

$ uname -mr
2.6.27-15-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan2.pid with pid 3999
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan2/00:1e:2a:c2:20:9b
Sending on   LPF/wlan2/00:1e:2a:c2:20:9b
Sending on   Socket/fallback
DHCPRELEASE on wlan2 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan2/00:1e:2a:c2:20:9b
Sending on   LPF/wlan2/00:1e:2a:c2:20:9b
Sending on   Socket/fallback
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                [ OK ]
  * Stopping NTP server ntpd
   ...done.
  * Starting NTP server ntpd
   ...done.

$ ifconfig wlan2:avahi
wlan2:avahi Link encap:Ethernet  HWaddr 00:1e:2a:c2:20:9b  
          inet addr:169.254.6.64  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Memory:dffe0000-dfff0000 
```

Now a few details that may be needed to understand all this. This is data i grabbed in relation to my WG311 pci card. My home router uses an SSID thats not listed on here because i turned SSID broadcast off. The final portion of data showed up after the prior commands. from what i understand it appears when the DHCP has failed.

Ive noticed that theres alot of activity on here due to the new ubuntu version. i really hope someone will help me soon.

---

