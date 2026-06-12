---
title: "not able to &quot;enable wireless device&quot;"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by mcrene on 2009-12-10
I recently upgraded, as most others did, to Ubuntu 9.10
Not long after I tried Xubuntu after hearing its a little less intensive than Ubuntu. I did this with a terminal entry and consequent download/upgrade for Xubuntu. I can now choose between gnome or xcfce (or something like that)

Everything was working fine, however yesterday I lost my wireless connection.

When I hover over the network icon it shows no option to "enable wireless connection"

I am still used to going to network options in windose, but in ubuntu I can find no place to enable/disable the wireless connection.

so how do I go about fixing this?

this is on a brand new dell inspiron 15

---

### Post by ant2ne on 2009-12-10
> Everything was working fineSooo.. for awhile after the xfce "upgrade" everything was working fine? Soo... maybe not related to the xfce "upgrade"?

---

### Post by mcrene on 2009-12-11
noooo maybe its not, I really have no idea.
thats why I am here asking for some help.

thanks for clarifying that tho, it may in fact, not be related.

---

### Post by mcrene on 2009-12-11
ok, so any help out there?

where do I go to "enable" my wireless device?

how do I get my wireless working again?

---

### Post by uncaspi on 2009-12-11
You can try to remove all lines except auto lo and iface lo inet loopback in sudo gedit /etc/network/interfaces
MAke a copy of the file first.

After restart the network sudo /etc/init.d/networking restart

If this didn't help please post sudo /sbin/ifconfig
dmesg | grep -e eth -e wlan

---

### Post by mcrene on 2009-12-12
sudo /sbin/ifconfig

gives this info;

[I]eth0      Link encap:Ethernet  HWaddr 00:25:64:6f:62:45  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe6f:6245/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36689728 (36.6 MB)  TX bytes:987716 (987.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.1 KB)  TX bytes:1120 (1.1 KB) [/I]

dmesg | grep -e eth -e wlan

provides this information

[I][    3.112838] sky2 eth0: addr 00:25:64:6f:62:45
[   17.844399] sky2 eth0: enabling interface
[   17.844584] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.442982] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   19.443165] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.968052] eth0: no IPv6 routers present
thomas@thomas-laptop:~$ sudo /sbin/ifconfig[/I]

I have been looking all over the site, it seems this is a VERY common problem with those who upgrade to 9.10

I just installed xubuntu 9.10 today as a new stand alone install (had both ubuntu/xubuntu)

I have an intel wireless card on my Dell Inspiron 15

I also ran;

lshw -C network

and got this information;
[I]
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:24:d6:16:1b:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:6f:62:45
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.1.101 latency=0 multicast=yes
       resources: irq:30 memory:f68fc000-f68fffff ioport:de00(size=256)[/I]

if anyone needs anymore info let me know I am on stand by to get this figured out ASAP.

thanks

---

### Post by mcrene on 2009-12-12
well this is just silly, 
after searching and searching for the "button" or "switch" on the case of my laptop that switches the wireless ON/OFF I read a thread that mentioned the FN key possibility.

so now everything is working just fine.

I'll be hiding my head in sand for the next little while.

thanks to those who gave a helping hand.

---

