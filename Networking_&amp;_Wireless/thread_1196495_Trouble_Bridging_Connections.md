---
title: "Trouble Bridging Connections"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by lateralus01 on 2009-06-25
I'm trying to bridge my wireless and wired connections.  I'm able to bridge them but not to get an IP after.  I believe the problem is because when I try the DHCP client on the bridge, it tries to get a lease from my wired card instead of my wireless card but I don't know how to fix that.

Here's what I do:
```

ifconfig wlan0 down
ifconfig eth0 down
brctl addbr bridge0
brctl addif bridge0 wlan0
brctl addif bridge0 eth0
ifconfig bridge0 up

```

Now, the community documentation tells me to enter this command to add the IP of my router (default gateway)

route add default gateway <default gateway ip address>

but for some reason that doesn't work:
```

root@Ubuntu:~# route add default gateway 192.168.2.1
SIOCADDRT: No such process

```

but I don't think that's the problem, here's what happens when I enter the last command:
```

root@Ubuntu:~# dhclient bridge0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/bridge0/00:13:a9:c0:62:7a
Sending on   LPF/bridge0/00:13:a9:c0:62:7a
Sending on   Socket/fallback
DHCPDISCOVER on bridge0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on bridge0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on bridge0 to 255.255.255.255 port 67 interval 17

```

notice the MAC address 00:13:a9:c0:62:7a, that's the address of my wired interface eth0 and I need it to be looking for a lease on my wireless card because that's the only place it's gonna get one.  I'm doing this so that I can plug another pc into my laptop and bridge wired through wireless connections.

Any suggestions?

Thanks,
Lateralus01

---

### Post by jhannah on 2009-06-25
I think you best bet is to stay away from DHCP on bridged interfaces all together. The route command you have been running is failing because the machine has no directly connected interfaces that can reach the specified IP.

I would recommend something like this in your /etc/network/interfaces file:
```

auto br0
iface br0 inet static
  bridge_ports eth0 wlan0
  address **192.168.2.100**
  netmask **255.255.255.255.0**
  gateway **192.168.2.1**

```

After this, simply restart networking and you should be all set. This will also setup your bridge group w/o needing to run the commands manually.

Hope that helps.

---

### Post by sadohert on 2009-07-06
Are you guys trying this with the network manager installed?  I'm trying to re-do a setup I had on my Gutsy install where I had eth0 and eth1 bridged (eth0 to the router, eth1 as a spare crossover connection), and then I could hook a laptop up to my network (DHCP would work fine too).  To get this setup to stay stable I had to uninstall network-manager, otherwise it seemed like the two systems (manual, versus auto from network-manager) were just fighting each other.

I'd really like to find a way to do this while still having network-manager going.

---

### Post by sadohert on 2009-07-19
So, I followed information at the following link to adapt my /etc/network/interfaces file, and my bridge seems to be behaving correctly now:

[http://mail.gnome.org/archives/networkmanager-list/2008-November/msg00217.html]("http://mail.gnome.org/archives/networkmanager-list/2008-November/msg00217.html")

My "interfaces" file looks like this:
```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down

auto eth1
iface eth1 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down

auto br0
iface br0 inet dhcp
  bridge_ports eth0 eth1

```

I *think* from the reading I was doing about network-manager that it will ignore interfaces that have their own custom lines in the "interfaces" file.  I wonder if maybe the lines for eth0 and eth1 (bring them up with no IP, then take them down) are somehow a kludge of some kind to make this work.  Either way, I'm doing fine now.

Incidentally, I was having trouble getting a laptop to get an IP through the bridge.  It turns out I have a flakey physical connector.  This website, and its discussion of ethtool, were a big help:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking)

Stu

---

