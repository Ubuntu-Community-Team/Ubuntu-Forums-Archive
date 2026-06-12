---
title: "IBM X60s Wireless"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by Vampyer on 2009-09-18
Hey guys, 

I have been trying to get my IBM X60s to connect to my network for a couple of days now but it won't seem to work. The good news is that I have found out that it uses an Intel 3945 802.11g Wireless chip but I have no idea where to go to get the drivers or how to install them. If there are any...

I might also have to accept that my card my not be compatible and would appreciate any recommendations :)

Thanks

---

### Post by chili555 on 2009-09-18
Your drivers are in your computer right now! Please try:```
sudo modprobe iwl3945
ifconfig
```Do you have a new interface, wlan0? If not, please let us see:```
sudo lshw -C network
```If so, can you click the Network Manager icon and see and connect to your network?

---

### Post by Vampyer on 2009-09-18
I don't use network manager, I use wicd instead but I typed in all the stuff you wanted me to and this is what came up:

---------------------------------------------------------------

flash@flash-laptop:~$ sudo modprobe iwl3945
[sudo] password for flash: 
flash@flash-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:9d:27:78  
          inet6 addr: fe80::216:cfff:fe9d:2778/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:16:d3:2e:f4:88  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe2e:f488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:76629889 (76.6 MB)  TX bytes:2512641 (2.5 MB)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-9D-27-78-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85075 errors:0 dropped:0 overruns:0 frame:41973
          TX packets:823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:10490291 (10.4 MB)  TX bytes:41616 (41.6 KB)
          Interrupt:17 

flash@flash-laptop:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
flash@flash-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:2e:f4:88
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.5-1 ip=192.168.1.3 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:9d:27:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:52:9c:16:ab:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by chili555 on 2009-09-18
> product: AR5212 802.11abg NIC
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wifi0
version: 01
serial: 00:16:cf:9d:27:78
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=[COLOR="Red"]ath_pci[/COLOR] latency=0 module=ath_pcIt looks like it uses an Atheros chipset, not an Intel 3945. As you can see, it has a driver attached. Wicd will probably connect if you first detach the ethernet cable, so that you have just one interface active at a time. Please try and let us know.

---

### Post by Vampyer on 2009-09-18
wicd is unable to obtain an ip address for some reason but it's been doing that for the past 2 days, even with network manager.

I'm really confused :(

---

### Post by chili555 on 2009-09-18
I suggest you reboot without the cable attached. Do you have any encryption in place? WEP, WPA, etc.? Have you double-checked that the right encryption key or password is being put in the right place?

---

### Post by Vampyer on 2009-09-18
I've already rebooted but I'll try it again just to be sure :)

My router doesn't have any security on it at all. I removed it to try and make it work but had no luck, still the same errors (unable to obtain ip)

When I do ifconfig wlan0 up, it says there's no such device.

Also, when I had WEP set up, it would ask me to input the WEP key and then do all the loading ect then it would take me straight back to the same screen and ask me to input the WEP key again. So I clicked "show key" just to make sure I wasn't making any mistakes then it kept showing a completely different key to the one I was typing... everytime :confused:

Anyway, rebooting, BRB :)

---

### Post by Vampyer on 2009-09-18
The reboot was unsuccessful :( any other ideas? Maybe I need to update or change some drivers or something... :confused:

---

### Post by chili555 on 2009-09-18
> ifconfig
[COLOR="Red"]ath0[/COLOR] Link encap:Ethernet HWaddr 00:16:cf:9d:27:78
inet6 addr: fe80::216:cfff:fe9d:2778/64 Scope:LinkYour interface is ath0 and it's already up. I suggest you remove the encryption temporarily from the router. Then, after you detach the ethernet cable, that you do:```
sudo ifconfig eth0 down
sudo iwconfig ath0 essid nameofyournetwork
sudo dhclient ath0
```Post the result, please.

The interface *wlan0* was my supposition, assuming you had an Intel chipset.

---

### Post by Vampyer on 2009-09-18
I've done that and I'm still unable to connect. Here's what happened:

------------------------------------------------------------------------

flash@flash-laptop:~$ sudo ifconfig eth0 down
[sudo] password for flash: 
flash@flash-laptop:~$ sudo iwconfig ath0 essid flashdrive
flash@flash-laptop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:cf:9d:27:78
Sending on   LPF/ath0/00:16:cf:9d:27:78
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2009-09-19
May we please see:```
sudo iwlist ath0 scan
```Thanks.

---

