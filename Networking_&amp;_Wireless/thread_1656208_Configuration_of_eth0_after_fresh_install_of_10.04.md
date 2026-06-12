---
title: "Configuration of eth0 after fresh install of 10.04"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by afrazin on 2010-12-30
I installed 7.10 (the version a friend had on disk) and went through the steps to upgrade it.  I got through 8.something and installed 9.10 when I could no longer access the internet.  I did some research, but decided it was easier to beg a disk from someone and create a disk of 10.04, my final destination.  I installed it as a fresh install, completely overwriting what was previously on the hard drive.  But now i still have problems accessing the Internet.  It's a wired connection on a desktop.  I can see that there are some parameters missing, but I can't see how to edit them (a bit of a newbie).

Please understand, I looked at the other solutions and they haven't been successful.  I already did:
sudo service network-manager stop
 sudo rm /var/lib/NetworkManager/NetworkManager.state
 sudo service network-manager start

and my /etc/network/interfaces shows
auto lo 
iface lo inet loopback

and /etc/NetworkManager/nm-system-settings.conf shows
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

and /var/lib/NetworkManager/NetworkManager.state shows
NetworkingEnabled=true


that being said, I do see:
alan@Development-server:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:4d:f5:89:8b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:a000(size=256) memory:e1000000-e1000fff memory:e2500000-e250ffff(prefetchable)

alan@Development-server:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
alan@Development-server:~$ 


Network device:    eth0
Hardware address:    00:1a:4d:f5:89:8b
Multicast:    Enabled
MTU:    1500
Link speed:    not available
State:    Active
Transmitted packets:    22
Transmission errors:    0
Received packets:    108
Reception errors:    0
Collisions:    0

which, even I can see that the eth0 device isn't set up properly, but I don't know how to do that.  can someone please let me know how?

thanks!

---

### Post by PatchesTheCaveman on 2010-12-30
If you have GNOME installed, its a lot easier to set up your connection using the graphical interface.  Right-click on the network icon on the top panel and hit Edit Connections.

If you only run on the console, you can configure NetworkManager using the *nmcli* command.  For details on how to do that, run
```
man nmcli
```

Also, if you know how to configure your network the old-fashioned way, you can disable NetworkManager all together by running
```
sudo apt-get remove network-manager
```

But I'm afraid complete manual CLI network setup is way above my pay grade.

I do have some experience with the *nmcli* command if you need help with that, though.

---

### Post by afrazin on 2010-12-30
I wish I could give you a graphic, but all I get when I do that (for the wired connection) is a MAC address and MTU of automatic bytes (that's adjustable).  There are checkboxes for connect automatically and available to all users (which are checked).

and for some reason I don't have a manual entry for nmcli. (but of course there's one online)

---

### Post by PatchesTheCaveman on 2010-12-30
> **afrazin said:**
> I wish I could give you a graphic, but all I get when I do that (for the wired connection) is a MAC address and MTU of automatic bytes (that's adjustable).  There are checkboxes for connect automatically and available to all users (which are checked).

You have to switch to the *IPv4 Settings* tab to change your IP address, subnet, gateway, and DNS settings.

---

### Post by afrazin on 2010-12-30
hot diggity dog, you're a genius!!  thank you!!!

sorry, have to take that back, didn't quite do it.

---

### Post by Iowan on 2010-12-30
I suspect **ifconfig -a** will only confirm that the interface has no IP address... If you're set up for DHCP address, you might post results of **sudo dhclient eth0**

Oops - typing to slow(ly) again...

---

### Post by afrazin on 2010-12-30
no, you're not too slow .. i'm just slow in checking results before i get excited.  what happened is that it now says that i'm connected, but i still can't ping the router.  here are the results you were asking for, mr. iowan:

alan@Development-server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:f5:89:8b  
          inet6 addr: fe80::21a:4dff:fef5:898b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26646 (26.6 KB)  TX bytes:10366 (10.3 KB)
          Interrupt:26 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:4d:f5:89:8b  
          inet addr:169.254.9.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

alan@Development-server:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 1591
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1a:4d:f5:89:8b
Sending on   LPF/eth0/00:1a:4d:f5:89:8b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
alan@Development-server:~$

---

### Post by PatchesTheCaveman on 2010-12-30
> **afrazin said:**
> sorry, have to take that back, didn't quite do it.

What's wrong?

---

### Post by afrazin on 2010-12-30
don't get me wrong, i'm sure you're a genius, but this didn't quite do the trick.  while it says that it's connected, i can't even ping the router, can't get out of the box.

I'm showing on my IPv4 settings:
Method: Manual
Address: 192.168.0.10
Netmask: 255.255.255.0
Gateway: 192.168.0.1
DNS servers: 212.143.212.143

I took all those (except for the 10 at the end of the Address) from my Win*cough* machine next to it.

---

### Post by PatchesTheCaveman on 2010-12-30
Did you have to manually configure your Windows machine or did it automatically get an IP address?

---

### Post by afrazin on 2010-12-30
automatic.  which is what i was expecting from ubuntu as well.  my windows machine has a dual-boot with ubuntu as well, and while i started from 7.04, i just upgraded and never had a problem.  i don't know why i would have a problem either with my original upgrade procedure or with this fresh install.  confounding, if you ask me.

---

### Post by t4thfavor on 2010-12-30
Did you try selecting DHCP under the IPV4 settings tab within network manager for the wired interface?

post some output from ifconfig -a and the contents of whatever file holds the DNS servers (anyone remember where those are?).

---

### Post by afrazin on 2010-12-30
it was originally under Automatic (DHCP) and didn't give any info on address or anything else and didn't get any internet access.  I had already posted ifconfig -a, see above.

---

### Post by afrazin on 2010-12-30
Thank you all for helping me with this.  I really have to go to sleep now, but I'll try to answer any questions about my system in the morning.  Again, thank you thank you thank you.

---

### Post by Iowan on 2010-12-30
Recheck/repost results of **ifconfig -a** after your latest configuration change. If address is still 169.254.X.X, then **avahi** is "helping". If it has the address you assigned, I'll wonder why it won't ping router.

Previous results suggested that either router didn't issue an IP address, or Ubuntu didn't receive/accept it.

---

### Post by afrazin on 2010-12-30
sorry, didn't understand.  here's the results:

alan@Development-server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:f5:89:8b  
          inet6 addr: fe80::21a:4dff:fef5:898b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:637733 (637.7 KB)  TX bytes:159979 (159.9 KB)
          Interrupt:26 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:4d:f5:89:8b  
          inet addr:169.254.9.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

alan@Development-server:~$

---

### Post by PatchesTheCaveman on 2010-12-31
Try stopping Avahi by running this command:
```
sudo service avahi-daemon stop
```

Have you tried resetting your router?  It's very odd that your Windows machines can get an automatic IP address but not your Linux machine.  Is there any difference in the wiring between your Linux box and the Windows one that you can discern?

After you've checked everything, try and force it to get an automatic IP address again by running
```
sudo dhclient eth0
```

---

### Post by afrazin on 2010-12-31
ok, patches, you've now justified your previous title of genius.  i stopped avahi and restarted the modem and it's now able to connect.  i had previously gone so far as to switch the cables between the two machines to make sure it wasn't the cable or anything outside the box.

thank you all so much for your help!

---

