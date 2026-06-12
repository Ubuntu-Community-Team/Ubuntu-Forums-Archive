---
title: "screwed up my ethernet connection while trying to setup the wireless"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by chechojp on 2009-02-10
I was living happily with ubuntu in a NEC laptop..no problems and working perfect except for the wireless internet connection.

When I tried (fool of me!!!) to take care of the wireless connection to access the wireles of  my university the ethernet conncetion in my house stopped working...I really don't know what I did wrong or where I messed up....I am not an expert in linux but I managed to work fine for a year or so without problems...I really need help. I didnot use the terminal for anything and only made changes by the GUI interface

By the way  the connection is working fine because i am using it with my other windows laptop.

perhaps necessary:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:4c:fe:f1:9a  
          inet addr:202.238.95.24  Bcast:202.238.95.255  Mask:255.255.255.0
          inet6 addr: 2001:c90:3286:a15e:200:4cff:fefe:f19a/64 Scope:Global
          inet6 addr: fe80::200:4cff:fefe:f19a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16664 (16.2 KB)  TX bytes:13413 (13.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:49:d0:6f  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x8000 Memory:ff9fd000-ff9fdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84048 (82.0 KB)  TX bytes:84048 (82.0 KB)


~$ sudo lshw -C net
  *-network:0             
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:00:4c:fe:f1:9a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 04
       serial: 00:04:23:49:d0:6f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.36 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated


```

---

### Post by alenis on 2009-02-10
You might try this
```
dpkg-reconfigure network-manager
dpkg-reconfigure net-tools
```
to restore the network configuration that Ubuntu sets up during the installation.

---

### Post by Iowan on 2009-02-10
When it worked, did ethernet connection get address via DHCP or was it static?  If DHCP, check */etc/network/interfaces* file.  (That file should be empty except for "lo" definition if Network Manager is in control.)

---

### Post by chechojp on 2009-02-12
Thanks alenis, but I tried reconfiguring the network and didn't work.

Iowan, to tell you the truth I don't know...but I checked the /etc/networ/interfaces file and this is what i got:

auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 202.238.95.24
netmask 255.255.255.0

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf







auto eth0


iface eth1 inet static
address 192.168.1.36
netmask 255.255.255.0
wireless-essid any

auto eth1


Is this enough info??? I really need help with this so please be patient.

---

### Post by superprash2003 on 2009-02-12
well is your wifi router's ip at home 192.168.1.1 ??if so add the line gateway 192.168.1.1 after 

iface eth1 inet static
address 192.168.1.36
netmask 255.255.255.0

and before

wireless-essid any

or.. if DHCP is enabled in your wifi router ( which is usually the case)
 just set iface eth0 inet dhcp and remove those address and netmask lines..

also remember to restart networking by typing **sudo /etc/init.d/networking restart** and then type **sudo dhclient eth1** to get an ip

---

### Post by Iowan on 2009-02-12
Which interface is more important to have working?  Quick fix (wishful thinking) *might* be to save a copy of /etc/interfaces file, then delete everything but the "lo" definition.  The address and netmask on eth0's "dhcp" definition probably isn't helping. As I'm not running Intrepid, I can't check what is supposed to be in /etc/NetworkManager (supposed to be where Network Manager keeps it's information).

---

### Post by chechojp on 2009-02-12
Thanks guys for the swift responses.

superprash, at home I'm using an ethernet connection...no wifi...but that address (192.168.1.1) is the wireless network at the university.....I believe i dont need that to get my ethernet conncetion working at home....

Iowan..i forgot to mention that I am not using intrepid but hardy heron....also...is the "lo" definition the first 2 lines??? or only the first line???

I will try to change the file and tell you what happened

Thanks

---

### Post by chechojp on 2009-02-14
Finally I solved the problem.....

alenis solution was correct...after opening a root terminal with sudo -i...after that restoring the network worked perfectly...thanks.....

By the way...I didn't figure out how to label this thread as solved....sorry about that

---

### Post by ugm6hr on 2009-02-14
Your wifi should work using the default settings if the University network uses DHCP (which is likely).

If you need advice - just point us to the instructions on getting connected to your University wifi network (for Mac or Windows or Linux), and we'll help from there.

---

### Post by zander1013 on 2009-02-14
the wifi card may not be supported by linux. i had to replace an intel wifi card with a cisco wifi card to get wifi to work with linux on a ibm thinkpad t40.

everyone was shocked that the intel wifi card would not work under linux but when i changed to a cisco card wifi started right away.

oh yes the shock and awe over the intel wifi card not working was at the ibm thinkpad forums. :P

if eth0 is working (your wired connection) then you likely need to find a wifi card that is linux compatible for your nec.

the corollary is look for a list of supported wifi cards for your laptop.:(
i don't think yours is listed in the sticky list at the top of the forum.
i got mine off ebay for about $20.

peace and good luck!

zander

---

### Post by ugm6hr on 2009-02-14
The Intel 2100 is supported by the ipw2100 driver very well in Linux.  Sometimes the ipw2200 driver is loaded instead (or vise versa where the ipw2100 is loaded for the 2200 chipset); if this is a problem you can just blacklist the one you don't need.

---

