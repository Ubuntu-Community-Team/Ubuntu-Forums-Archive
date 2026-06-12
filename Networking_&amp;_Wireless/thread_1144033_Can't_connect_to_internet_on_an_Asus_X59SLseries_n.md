---
title: "Can't connect to internet on an Asus X59SLseries notebook"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Aljosha on 2009-04-30
Dear ubuntu users,

I'm having an internet problem with both 32/64-bit Ubuntu version 8.10 and 9.04 on an Asus X59SLseries. My connection is wired and works perfectly on Windows Vista. Yes, I tried restarting my router and what not but it seems the problem really lies in the OS, not somewhere else.

Ubuntu is able to provide me with a correct IP address and also figures the broadcast address and the router's address correctly, but I still can't use any internet features: can't ping anything, not even computers on my local network. Neither can I visit any web pages or connect to MSN using kopete or download a simple html page using wget.

Could somebody please give me some hints to connect me to the rest of the world? Live without internet sucks.

Aljosha.
[IMG]http://img232.imageshack.us/img232/9008/paininthearse.png[/IMG]

---

### Post by chili555 on 2009-04-30
Did you plug in those numbers, xx.70, etc., by hand or did you let your computer find them out by DHCP? If you put them in by hand, as I suspect, will you try DHCP and let us know the result? Thanks.

---

### Post by Aljosha on 2009-04-30
Thanks for replying,

Nope, these numbers are not hand written, DHCP got them for me, and as I already said, Vista uses these too! So the addresses shouldn't be the problem. Or am I wrong?

By the way, reconnecting like hundred times or executing dhclient doesn't work either.

---

### Post by chili555 on 2009-04-30
> DHCP got them for me....So the addresses shouldn't be the problem.Quite correct. Perhaps we can see something in *dhclient*. Please open a terminal and do:```
sudo dhclient eth0
cat /etc/resolv.conf
```Please post the result. Thanks.

---

### Post by Aljosha on 2009-05-01
Thanks a lot for reading and replying!

I did your commands on both my Asus notebook and another similar one with different hardware, but on the same network/router which CAN connect to the internet out of the box.

The working one:

```
julia@julia-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:f3:b7:8c:7d
Sending on   LPF/eth0/00:18:f3:b7:8c:7d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of *SECRET*.68 from *SECRET*.65
DHCPREQUEST of *SECRET*.68 on eth0 to 255.255.255.255 port 67
DHCPACK of *SECRET*.68 from *SECRET*.65
bound to *SECRET*.68 -- renewal in 18297 seconds.
julia@julia-laptop:~$ cat /etc/resolv.conf
nameserver *SECRET*
nameserver *SECRET*
```

The broken one:
```
ubuntu@ubuntu:~$ sudo dhclient eth0
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:23:54:50:9d:9f
Sending on   LPF/eth0/00:23:54:50:9d:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of *SECRET*.70 from *SECRET*.65
DHCPREQUEST of *SECRET*.70 on eth0 to 255.255.255.255 port 67
DHCPACK of *SECRET*.70 from *SECRET*.65
bound to *SECRET*.70 -- renewal in 18231 seconds.
ubuntu@ubuntu:~$ cat /etc/resolv.conf
nameserver *SECRET*
nameserver *SECRET*
```

Again, the addresses are exactly the same, except the .70/.69/.65/.71 stuff which is of course correct. The addresses after ```
nameserver
``` are the same on both machines as well. 

Any more hints for me? Could it be the drivers not working properly with my machine?

Thanks,

Aljosha.

---

### Post by chili555 on 2009-05-01
Ahhh! My favorite type of question: everything looks perfect but it doesn't work.

On the not-working machine, please let us see:```
sudo ethtool eth0
```Can you please verify the driver each machine is using is the same, and tell us what it is?```
sudo lshw -C network
```You don't have to post the whole thing, just the *driver=**** part. Thanks.

---

### Post by Aljosha on 2009-05-03
The driver doesn't seem to be the same, though I'm not sure which of the three network drivers I have to look at. 

Here's the working machine (which is by the way 64, I'm not sure if this matters or not because my not-working one 32. Strange, it should be the other way round.)

You have to scroll sideways to see the driver=* line, I guess the driver of the broken on is sis190 and the working one is r8169. I'm not really sure, as the command gives me several different interfaces.

```
julia@julia-laptop:~$ sudo ethtool eth0
[sudo] password for julia: 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes
julia@julia-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:b7:8c:7d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=*SECRET* latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:95:87:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:60:da:53:55:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
```

The broken one:
```
ubuntu@ubuntu:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:23:54:50:9d:9f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=*SECRET* latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:1f:c0:bb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:1e:76:60:88:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
	Link detected: yes
 
```

The second command took over one hour (!!) to execute. I'm not really sure whether this is usual or not, I think it shouldn't be.

Please help,

Aljosha

---

### Post by chili555 on 2009-05-03
> The second command took over one hour (!!) to execute. I'm not really sure whether this is usual or not, I think it shouldn't be.You are right. It shouldn't be! It sounds like you have a much bigger issue than your wired connection! Please do:```
dmesg > dmesg.txt
tar cvf dmesg.tar dmesg.txt
```You will then have an archive file called *dmesg.tar* that you can post here for the gurus to examine. If the commands take a while to finish, that's fine.

---

### Post by Aljosha on 2009-05-04
Thanks again for the replies,

The file is in the attachement.

---

### Post by chili555 on 2009-05-05
Wow! That is a very interesting *dmesg*! It shows that your computer takes a long time to boot, it looks like almost 3 minutes. My dual core laptop boots in a bootchart-documented 16 seconds. The thing that's most interesting is that I really don't see anything terribly alarming. I did see this:> APIC error on CPU1: 00(40)Let's try a boot parameter and see if we can fix a few things. Please sudo gedit */boot/grub/menu.lst* to add two parameters. Look for the first kernel line in the list and add as shown here; using mine as an example:```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            c2667fe5-c412-4d68-bbf0-43c81363d405
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c2667fe5-c412-4d68-bbf0-43c81363d405 ro [COLOR="Red"]noapic nolapic[/COLOR] quiet splash 
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

```Your UUID and other details may vary. Proofread twice, save and close gedit. Reboot. Now run dmesg and see what the last timer line is. Is it faster than it was? And, more importantly, did we help your ethernet come to life?

If, by chance, we didn't improve anything, it costs nothing to remove those two parameters.

---

### Post by Aljosha on 2009-07-05
First, thank you for all the replies, and second, excuse me for not replying earlier. But anyway, these parameters did at least improve something. The slow boot time is actually caused by the fact that I was using the live CD. Just to be sure, I installed ubuntu 9.04 on a spare 50 gig partition, but that alone did nothing.

With the two parameters noapic & nolapic in the kernel line in grub enabled I could actually go to google, do some searching, read my mail. But 99% of all other internet pages didn't work. I could visit some Dutch (.nl) news site and an, again Dutch (.nl), music review site, but nothing else. Just keeps loading for ages. 

Makes totally no sense to me? I'm pretty sure the google pages no matter if I type in .ch or .com or .nl are downloaded from a Dutch mirror too, but I'm not sure.

---

