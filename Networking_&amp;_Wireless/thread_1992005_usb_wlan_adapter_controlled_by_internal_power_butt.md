---
title: "usb wlan adapter controlled by internal power button"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by eddski on 2012-05-31
I have a realtek rtl8191s wlan adapter and it appears to be working except that power is controlled by wireless switch for my internal card, I know it sounds crazy. But with my internal card turned on I can plug in my 802.11 usb and get connected to my home network along with my internal card. Then I click wireless icon on my panel and disconnect wlan0(internal card) and still have connection thru usb, I can tell the same when I run ifconfig:
root@laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:b7:0c:28:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15536 (15.5 KB)  TX bytes:15536 (15.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:53:62:b0  
	INTERNAL CARD
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:62038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72775935 (72.7 MB)  TX bytes:6886123 (6.8 MB)

wlan2     Link encap:Ethernet  HWaddr 00:02:72:9a:74:2c  
	USB WLAN ADAPTER
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe9a:742c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:274 errors:0 dropped:7 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12460 (12.4 KB)  TX bytes:6575 (6.5 KB)

am I missing something, how can my internal wifi power turn off my usb wlan adapter?

---

### Post by chili555 on 2012-05-31
> am I missing something, how can my internal wifi power turn off my usb wlan adapter?Because it's designed and built that way, I believe. One of my laptops works the exact same way. I believe that many laptops are built to be able to affirmatively disable wireless in response to flight rules. As your airplane approaches Paris, the avionics would like to hear the landing beacon and not Youtube. 

Why do you need a USB in preference to the internal? Do we need to do some troubleshooting?

You could certainly disable the internal by blacklisting its driver.

---

### Post by eddski on 2012-05-31
thanks for the reply, but sometimes, on my windows side, i get better reception when the usb adapter is connected to an extension and elevated. by the way how would i disable the internal driver? also on the windows side the switch for the internal antenna is indepedant of the usbwifi adapter. i am just trying to get more things to operate similar to windows so i can depend on it less and less.

---

### Post by chili555 on 2012-05-31
> by the way how would i disable the internal driver?By blacklisting its driver. Please run:```
sudo lshw -C network
```Post it and we'll find out what to do.```
i am just trying to get more things to operate similar to windows
```Hmmm. I think Windows should operate more like Ubuntu! Once you get more accustomed to it, I think you'll find Ubuntu easy and logical.

---

### Post by eddski on 2012-06-01
here is the output from lshw -C network:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:53:62:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-15-generic firmware=15.32.2.9 ip=192.168.1.70 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:ffcff000-ffcfffff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:15:b7:0c:28:57
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:ffaff000-ffafffff ioport:bf40(size=64)


you're right about windows, sorry
the output is with the internal activated only, which is the driver i would like to disable.
is it easy to re-enable the driver?
the other reason i want to do this is because the internal card is a/b/g not n, want to keep 11a, may go back to @ home. dont know if they make an a/n mini-pci card, will be checking though.

---

### Post by chili555 on 2012-06-01
> description: Wireless interface
product: [COLOR="Red"]PRO/Wireless 3945ABG [/COLOR][Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 02
serial: 00:18:de:53:62:b0
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] driverversion=2.6.38-15-generic firmware=15.32.2.9 ip=192.168.1.70 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
resources: irq:42 memory:ffcff000-ffcfffffTo disable it, please do:```
sudo modprobe -r iwl3945
sudo gedit /etc/modprobe.d/blacklist.conf
```At the end of the file add a single line:```
blacklist iwl3945
```Proofread carefully, save and close gedit. If you don't have the text editor gedit, use kate, leafpad, nano, vim or any other text editor.

To re-enable it temporarily, just load the driver:```
sudo modprobe iwl3945
```To re-enable it permanently, simply edit the blacklist file as above and comment out the line so it looks like this:```
#blacklist iwl3945
```Lines preceded with # are human-readable comments only and ignored by the system.

---

### Post by kurt18947 on 2012-06-01
I'm not nearly as savvy as Chili555 but here is my experience with an R61i Thinkpad.  I have installed Ubuntu 12.04 and Mint 13 based on Ubuntu 12.04.  I have a USB Wifi adapter, Edimax EW-7811Un.  The only way I've found to get that adapter to work well is with RealTek's drivers; the one included in 12.04 seems flawed.   

With 12.04 I can turn off the physical wifi/bluetooth switch and the Edimax adapter still functions. Also in 12.04, blacklisting iwl3945 disables the integral wifi adapter.  In Mint Maya,  if I turn off the physical switch **all** wifi adapters die so the switch must remain on.  I wanted to disable the integral g speed adapter so  did 'lsmod' and blacklisted all the modules that seemed to control the internal wifi adapter.  The thing *still* came on; the wifi adapter that would not die :shock:.  I was able to turn it off in Network Manager and so far so good.

---

### Post by eddski on 2012-06-01
thanks chilli555, worked like a charm. i was also worried about flipping the switch on/off, now i can just leave it on and uncomment the blacklist. thanks kurt18947 for info, i am still learning but how would you disable it in network manager, can't seem to find where

---

### Post by chili555 on 2012-06-01
Awesome! Glad it's working. Would you please use thread tools at the top to mark Solved? The searchers will appreciate it.

---

### Post by eddski on 2012-06-01
thanks again for your help

---

