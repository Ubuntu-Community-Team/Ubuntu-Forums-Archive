---
title: "Ethernet cable modem can't connect to internet"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by mamastinky on 2011-05-04
I am a noob, so I need explicit detailed instuctions. 

I am using a cable modem wired to my PC via ethernet. My ISP is Road Runner, through Time Warner Cable.

I entered my IP address, Netmask, and DNS Servers into the network, not using DHCP. This was how I was able to achieve a network connection.

I am connected to the modem, but I cannot get internet.

here are my stats:
seymore@seymore-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:b5:c8:b2  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:feb5:c8b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16358388 (16.3 MB)  TX bytes:1435239 (1.4 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18032 (18.0 KB)  TX bytes:18032 (18.0 KB)

seymore@seymore-desktop:~$ sudo lshw -C network
[sudo] password for seymore: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:b5:c8:b2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.254.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:f8ff0000-f8ffffff(prefetchable) memory:febc0000-febdffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
seymore@seymore-desktop:~$

---

### Post by mamastinky on 2011-05-04
I am so sorry, those configurations were from the active modem I switch to. Here are the configurations from the cable modem I can't connect from:

seymore@seymore-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:b5:c8:b2  
          inet addr:127.0.0.1  Bcast:127.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2e0:4dff:feb5:c8b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30819223 (30.8 MB)  TX bytes:2320878 (2.3 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18032 (18.0 KB)  TX bytes:18032 (18.0 KB)

seymore@seymore-desktop:~$ sudo lshw -C network
[sudo] password for seymore: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:b5:c8:b2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=127.0.0.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:f8ff0000-f8ffffff(prefetchable) memory:febc0000-febdffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
seymore@seymore-desktop:~$

---

### Post by Iowan on 2011-05-04
???? How did **eth0** get the 127.0.0.1 address?

---

### Post by mamastinky on 2011-05-04
> **Iowan said:**
> ???? How did **eth0** get the 127.0.0.1 address?

Well, I am really not sure, all I changed is I entered the address 127.0.0.1 under IPv4 settings for "Wired Connection 1." 

It might be worth mentioning, I don't seem to have a driver for my ethernet card, although I am using it right now for a separate ISP. Also, under etc/network/interfaces it reads:

auto lo
iface lo inet loopback

I spent alot of time trying to work this out on my own reading forums before coming here; I got stuck trying to install the ethernet driver, since I need to take a few more crash courses in order to proceed further with it.

---

### Post by callenish on 2011-05-04
> **mamastinky said:**
> Well, I am really not sure, all I changed is I entered the address 127.0.0.1 under IPv4 settings for "Wired Connection 1."

If you are going to set a static IP address, it has to be one from your internal network and it cannot be one that is used by another machine. One thing you can be guaranteed is that 127.0.0.1 is NOT in your internal network. Packets sent there never go out on the network but stay in your machine.

If you don't know what you are doing, you should start out using DHCP. Also, your /etc/networking/interfaces file is missing the lines to autoconfigure your eth0 interface. I would recommend adding two lines:

```

auto eth0
iface eth0 inet dhcp    

```These lines are supposed to get your modem to automatically set up the networking on your machine. As well, make sure the network configuration tool you used to set the 127.0.0.1 address is configured to use DHCP. That will at least get you closer to a working solution. If you can see the subnet that the modem defines (usually the first 3 numbers in the IP address) as well as the range it starts assigning IP addresses at (usually not far from the last number in the IP address), you can probably figure out how to set a static IP address that the modem will NOT assign to anything else.

However, I am using the same Realtek chip that you are, and for me networking doesn't work ever since upgrading to 11.04, even with the fixes described above. I'll post my own thread about this soon.

---

### Post by mamastinky on 2011-05-04
> **callenish said:**
> 
If you don't know what you are doing, you should start out using DHCP. Also, your /etc/networking/interfaces file is missing the lines to autoconfigure your eth0 interface. I would recommend adding two lines:

```

auto eth0
iface eth0 inet dhcp    

```These lines are supposed to get your modem to automatically set up the networking on your machine. 

I thought so. How do i get that configured?

> **callenish said:**
> 
As well, make sure the network configuration tool you used to set the 127.0.0.1 address is configured to use DHCP. That will at least get you closer to a working solution. If you can see the subnet that the modem defines (usually the first 3 numbers in the IP address) as well as the range it starts assigning IP addresses at (usually not far from the last number in the IP address), you can probably figure out how to set a static IP address that the modem will NOT assign to anything else.

I originally was using DHCP. Since you suggested it I just now tried the connection with DHCP configured again, and it won't even connect to the network. So, either I may expect different results after I get my interfaces changed, or else I need to use a different IP address. How do I determine a static IP address, exactly?

---

### Post by mamastinky on 2011-05-06
I reconfigured my eth0 interface to use DHCP. Nothing. 

I couldn't help feeling that somehow there was a conflict between my ethernet driver and the modem.  Trying to install the correct driver (I apparently have the r8169 module for my r8168 card, noticed it's a common inconvenience). However, I have been avoiding having to install the new driver.

So, I downloaded dhcp3, and configured the definitions in /etc/dhcpd/dhcpd.conf as suggested in Ubuntu Documentation to those "common for all supported networks". Still, no success. Luckily, I still have internet access on my backup modem. I won't a week from now.

At this point, I have spent hours and hours reading forums in the middle of the night for days. It was time to reinstall the driver.

 I downloaded r8168-8.023.00 from the realtek site (for kernel 2.6.x). I have tried to follow the README instructions using terminal, but I can't even unpack the tarball. I tried installing from root per instructions on this thread [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411), but I am not sure if I am incorporating the terminal commands correctly and I am not apt to experiment using root. I think I did, however, successfully remove the r8169 module. 

It seems I might have missed some obvious portion of terminal commands during my crash courses, hopefully..  help!

---

### Post by mamastinky on 2011-05-06
Good news is, the r8169 module comes back on reboot. More good news, I unpacked the tarball. I feel like a dweeb; I wasn't including the directory in the command, I had to piece together three different information sources to figure that one. However, when I start ./autorun.sh, it stops short: 

[PHP]seymore@seymore-desktop:~$ sudo r8168-8.023.00/autorun.sh 
[sudo] password for seymore: 

Check old driver and unload it. 
rmmod r8169 
Build the module and install 
make: *** No rule to make target `all'.  Stop. [/PHP]

no rule to make target 'all'.  

What does that mean?

---

