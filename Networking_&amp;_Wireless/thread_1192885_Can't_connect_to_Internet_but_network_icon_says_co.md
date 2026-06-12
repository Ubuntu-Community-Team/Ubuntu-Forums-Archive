---
title: "Can't connect to Internet but network icon says connected to wifi"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by Binoy918 on 2009-06-20
Hi,
  I am using a Dell Inspiron 1525 and has configured the wifi card using the driver from Broadcom (hybrid_wl). When I modprobe ieee and insmod wl.ko I am able to see the wifi access point and the Icon in the panel says connected. But I cannot access the internet.
I am a noob in Linux so please bear with me.

I am here posting some of the results I got after these commands:
(If it helps:confused:)

~$ iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:233  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```~$ dmesg
```

......
......
[  154.194121] ieee80211_crypt: registered algorithm 'TKIP'
[  157.468171] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  157.468194] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[  157.486564] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[  159.633534] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  159.712157] NET: Registered protocol family 17
[  161.013369] eth1: no IPv6 routers present
[  252.861358] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  256.688177] eth1: no IPv6 routers present
[  310.641383] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  314.416415] eth1: no IPv6 routers present
```~$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:50:b0:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:53:38:41  
          inet6 addr: fe80::21f:e1ff:fe53:3841/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:11973
          TX packets:75 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7512 (7.3 KB)  TX bytes:14893 (14.5 KB)
          Interrupt:17 Base address:0xc000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1f:e1:53:38:41  
          inet addr:169.254.5.0  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13788 (13.4 KB)  TX bytes:13788 (13.4 KB)
```~$ lshw -C netwok
```
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:50:b0:56
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:53:38:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```

---

### Post by papangul on 2009-06-21
You may try the WICD network manager, it may work:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)

---

### Post by Binoy918 on 2009-06-21
Ok, I will try this and get back to you.
I do not have a wired connection. So I have to reboot to Vista to access the internet.

---

### Post by Binoy918 on 2009-06-21
> **papangul said:**
> You may try the WICD network manager, it may work:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)
Ok I have downloaded and installed Wicd Manager (after uninstalling network manager).

Now after different attempts to connect to the network I was finally able to connect to internet in unsecure mode (i.e no encryption enabled in router).

What should I do to connect in preferably WEP Open encryption.

Now I am updating xubuntu via Update Manager, hope this will help.

---

### Post by RedSingularity on 2009-06-21
It will give you an option to connect to a secured network when it finds one.

---

### Post by papangul on 2009-06-21
First, try to set the wep/wpa key without hiding the network essid.

---

### Post by Binoy918 on 2009-06-22
Yes, I tried to connect in wpa 1/2 all modes and wep all modes available in wicd. I could see that the access point was detected and was able to set the password in configuration menu in wicd manager but when I press connect it says validating authendication or something like that for sometime and stops.

I am using my mobile as a router (the Wifi is broadcasted by mobile from its 3G connection). It has only 3 options - Open(unsecured, WEP Open & WEP Shared). There is no option to hide the essid in this.

---

### Post by papangul on 2009-06-22
There are two types of WEP encryptions: 64bit and 128 bit, what are you using?
> Enter 13 ASCII characters or 26 hexadecimal digits for 128-bit encryption keys
 	Enter 5 ASCII characters or 10 hexadecimal digits for 64-bit encryption keys

If this does not sort out the problem, then there is definitely a driver issue for the broadcom card. I am afraid I won't be able to help in that case ,but you will find other people encountering and solving similar problem before you. You just have to search in this forum or the web.

---

### Post by Iowan on 2009-06-22
I'm still not good with wireless, but the avahi address suggests DHCP didn't work right.  Avahi gave it an address, but the interface is probably alone in it's own li'l world (subnet).

---

### Post by Binoy918 on 2009-06-22
I was using a 13 digit ASCII 128-bit encryption when I checked the connection. 

How can I get the DNS for manually setting the IP.

---

