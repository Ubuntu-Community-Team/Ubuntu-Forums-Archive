---
title: "Wireless connection issue"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by kircher on 2009-06-15
Hi,

[solved by uninstalling drivers I compiled from source - the ubuntu drivers work 'out of the box'. I guess all I needed to get them to work was reboot, rather than install the ones from source]

After following this thread [http://ubuntuforums.org/showthread.php?t=732827]("http://ubuntuforums.org/showthread.php?t=732827") to install the drivers for my netgear wireless usb adapter I ran into some problems actually getting my computer to connect to my router. At first I thought it was a problem with WPA-PSK, so I tried using WEP, but with no success. I then tried with no security on the router at all, and there was no success either. I then tried one of the unsecured connections in my neighbourhood to rule out fault of my router, but have had no success there either. In both cases my sister's laptop with Vista connects without issue.

I am confused because clicking the network notification icon in the top panel shows that there are wireless networks available - mine and others nearby, but trying to connect just fails.

The output of lsusb is this:```
james@james:~$ lsusb
Bus 001 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

and lshw -C network: ```
james@james:~$ sudo lshw -C network
[sudo] password for james: 
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (CNR) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 81
       serial: 00:00:e2:88:53:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=10.1.1.3 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1e:2a:d2:b2:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:92:07:3d:5c:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

iwconfig: ```
james@james:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

ifconfig: ```
james@james:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:e2:88:53:83  
          inet addr:10.1.1.3  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e2ff:fe88:5383/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12015508 (12.0 MB)  TX bytes:1727752 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4740 (4.7 KB)  TX bytes:4740 (4.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1e:2a:d2:b2:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-2A-D2-B2-D9-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I do not know where to begin with sorting this out. Perhaps a manual configuration? Using a static IP?

This is my first time trying to get wireless to work, so thank you for your time.

---

### Post by kircher on 2009-06-16
update: I just realised I should probably do a search on RTL8187B drivers, rather than the ones I used. I'll post back when I've sorted that out

---

### Post by MaindotC on 2009-06-16
I'm monitoring [another thread](http://ubuntuforums.org/showthread.php?t=1184100) with the same adapter and my information shows the WG111 is using a Broadcom chip.  Perhaps [his lsusb output](http://ubuntuforums.org/showthread.php?t=1184100) is showing that his machine is incorrectly detecting, but see if the device is using Broadcom and if so you may wish to use a different driver.  I'm also going to let him know that your system is detecting the proper drive for the card as the RTL8187B.  Hopefully the both of you can come to a solution.

---

### Post by kircher on 2009-06-16
I've also been watching this thread here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7353295]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7353295"), and the person with problems there has the same wg111v3 card with RTL8187B drivers. He followed the same thread I did to set mine up and seemed to have the same problems, however when he unsecured his wireless network he was able to connect. I on the other hand can't connect when I make it unsecure. I might try a different set of drivers. For RTL8187B in particular, rather than the wg111v3 drivers I used from the thread I listed up top in my first post. I'll post back If I am successful, or unsuccessful for that matter.

---

### Post by kircher on 2009-06-16
I was going to try reinstalling the drivers from a newer version of the source code, and after uninstalling, I decided to restart to check if it worked without having to reinstall, and Yes, it works with the preinstalled ubuntu drivers. I don't know why it wasn't working intially. I probably should have fiddled more before jumping in and using the drivers from source.

---

