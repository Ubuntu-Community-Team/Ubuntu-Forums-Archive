---
title: "Problems using MoBo NIC"
date: 2007-10-25
forum: Mythbuntu
---

### Post by fatemonkey on 2007-10-25
Hey,  I recently decided to reinstall on my mythTV box and tried mythbuntu 7.1.  The installation went smoothly except that my NIC card is not working.  On Ubuntu desktop 7.1 the NIC card works perfectly, on mythbuntu it does not.  

Is there any way to install the driver from the Ubuntu desktop CD?!

I've got it so close!  I have my schedules direct membership all entered and I can surf all of my "adding channel"s.  I just can't run mythfilldatabase.

---

### Post by napsilan on 2007-10-25
what motherboard (and NIC) do you have?

---

### Post by fatemonkey on 2007-10-25
The MoBo is a hand me down and the NIC is integrated.  Is there any way to find out the relevant info from the terminal?

---

### Post by napsilan on 2007-10-25
```
lshw > hardwarelist

```

then pose the contents of the hardwarelist file

---

### Post by fatemonkey on 2007-10-25
Ok.  I entered that command and opened the file that was outputted in nano.

Here are what seem to be the relevant parts:

*-core
      description: Motherboard
      product: nVidia-nForce
      physical id: 0
    *-firmware
           description: BIOS
           vendor: Phoenix Technologies, LTD
           physical id: 0
           version: 6.00 PG (03/10/2004)
           size: 128KB

[bunch of other stuff, processor, AGP, memory, etc]

*-network
       description: Ethernet interface
       product: nForce2 Ethernet Control
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial:  00:e0:4c:bc:db:1d
       capacity: 100MB/s
       width: 32 bits
       clock: 6MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation on boradcast=yes driver=forcedeth driverversion=0.60 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes part=MII

Any thoughts?  Because of a bad router setting that cannot be changed I have been spoofing the mac address on this machine by editing the /etc/network/interfaces file and adding 

       hwaddress ether 01:02:03:04:05:06

after

auto eth0
iface eth0 inet dhcp

but that entry does not even show up.  I previously tried adding it, but it did not work.  This is a fresh install, I have not modified anything.

Any advice would be greatly appreciated! Thanks!

---

### Post by napsilan on 2007-10-25
```

lsmod | grep forcedeth

```
Should output something if the driver is loaded

Have you also tried manually resetting the connection?
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up

```

---

### Post by superm1 on 2007-10-25
Also, you can checkout network manager from the top right corner of the screen.  You can renew your address by reselecting your network up there.

---

### Post by fatemonkey on 2007-10-25
I have tried manually resetting and it does not seem to do the trick.  It looks to you guys like the driver is properly configured?

It may be a router problem.  I don't have full admin access to the router and the admin screwed up port forwarding to the mac address of this NIC, that's what forced me to spoof the mac before.  I thought he had deleted those changes but maybe he hasn't.  I'll check with him tomorrow.

---

