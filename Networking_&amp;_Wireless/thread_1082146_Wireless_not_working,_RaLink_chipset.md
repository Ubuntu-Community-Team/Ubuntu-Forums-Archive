---
title: "Wireless not working, RaLink chipset"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by Snyper64 on 2009-02-27
I have a EDIMAX EW-7128G IEEE 802.11b/g PCI Wireless Card and I can't get it to work on my 8.04 system. When I go into Networking Tools I get the choices for my Ethernet(that works properly) and my wireless card which shows up as a "lo" device. I use to have a D-Link card but I couldn't get it to work no matter what I did so its possible something I did trying to get it to work is messing around with my new card. I know the card works as I tossed it in an XP system and it works fine(picks up better than the old D-Link card I put in the machine). My network config file:```
auto lo
iface lo inet loopback
``` Right now I'm stuck using the Library's computers for net access but feel free to ask me anything and I will get back asap.

---

### Post by Snyper64 on 2009-02-28
Some more information:

In the &#8220;Edit Wireless Networks&#8221; dialog box it allows me to type in the Name field but won't allow me to type in the bssids field(I can click on it and its not grayed out but when I try to type in it it won't do anything?) and it is not showing anything in the networks list when I have 2 networks that iwscan(I guess this shows my card semi works) picks up, one of which is my router. Using a network monitor icon for wlan0 status shows up as &#8220;Disconnected&#8221; and clicking on &#8220;Configure&#8221; just brings up a box that says &#8220;The interface does not exist Check that it is correctly typed and that it is correctly supported by your system.&#8221; I've posted several readouts below.

lshw -C network
```
snyper64@snyper64-desktop:~$ sudo lshw -C network 
 [sudo] password for snyper64:  
 *-network:0              
       description: Wireless interface 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: b 
       bus info: pci@0000:00:0b.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:1f:1f:37:9b:02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g 
  *-network:1 
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 74 
       serial: 00:11:5b:51:05:8d 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s 
snyper64@snyper64-desktop:~$
```
iwlist scan
```
snyper64@snyper64-desktop:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:11:95:41:10:C5 
                    ESSID:"Snypers Den" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=53/100  Signal level=-38 dBm   
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=000000004450dbbf 
          Cell 02 - Address: 00:0F:B3:07:92:F2 
                    ESSID:"ZZMA0" 
                    Mode:Master 
                    Channel:9 
                    Frequency:2.452 GHz (Channel 9) 
                    Quality=46/100  Signal level=-82 dBm   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Extra:tsf=0000011e833a907a 
 
snyper64@snyper64-desktop:~$
```
/etc/network/interfaces
```
auto lo 
iface lo inet loopback
```
ifconfig -a
```
snyper64@snyper64-desktop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:11:5b:51:05:8d   
          inet6 addr: fe80::211:5bff:fe51:58d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2484 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1544 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:853482 (833.4 KB)  TX bytes:111874 (109.2 KB) 
          Interrupt:15 Base address:0xc000  
 
eth0:avahi Link encap:Ethernet  HWaddr 00:11:5b:51:05:8d   
          inet addr:169.254.4.144  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:15 Base address:0xc000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:3804 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3804 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:214530 (209.5 KB)  TX bytes:214530 (209.5 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:37:9b:02   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-37-9B-02-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
snyper64@snyper64-desktop:~$
```

---

### Post by Snyper64 on 2009-03-02
bump

---

### Post by Snyper64 on 2009-03-03
Anybody?

---

### Post by Snyper64 on 2009-03-04
Somebody has to know how to fix this, the card is partially working but it seems that network manager doesn't see/like it. I have tried going into my wireless cards properties and setting up the ssid and both static and automatic addressing but to no avail. Also occasionally the drop down box in the wireless properties box will show several networks but I can't connect to any of them either.

---

### Post by Snyper64 on 2009-03-06
bump

---

### Post by Snyper64 on 2009-03-07
Ok, after messing around with my router through my wired connection and enabeling 128 bit WEP Open Key Hex(I still can't figure out why I couldn't get it to connect to an open connection?) and directly typing in my wireless information in the wireless properties box(including static IP as it wouldn't automatically set it up?) I finally got my wireless working.

Now I just need to figure out how to get it working in Network Manager and I will be all set. Any Ideas?

---

### Post by Snyper64 on 2009-03-13
Ok, I finally managed to get everything working. For those that are having the same problem as me you need to remove Network Manager and install [WICD]("http://wicd.sourceforge.net/").

For those of you that can hook up a wired connection or that have some other form of internet access on their pc just follow the instructions on this page: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php").

If you don't have internet access on your pc like me use a friends/library's/work computer and go [HERE]("http://wicd.sourceforge.net/download.php") and download the stable release .deb file onto a usb drive(its small enough to fit on a floppy if you still use those). On your pc go into Synaptic and search for Network Manager and remove it(you don't have to completely remove it). Now copy the WICD deb file onto your desktop and double click it, follow the instructions and when finished restart your pc. After everything's loaded up your wireless should now work and you've just sent Network Manager packing to Dev/Null.

---

