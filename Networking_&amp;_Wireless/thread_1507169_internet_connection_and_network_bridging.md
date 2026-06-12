---
title: "internet connection and network bridging"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by XiaoHu on 2010-06-11
hello,

I have 2 computers in the following network configuration:
desktop: connected to router.
HTPC: connected to desktop.

i used this code in */etc/network/interface* to bridge the network:
[I]# Bridge between eth0 and eth1
auto br0
iface br0 inet dhcp
bridge_ports all[/I]

-- the bridge works, but i don't have an internet connection on the desktop.

so i have found that by running:
*sudo route add default gateway 192.168.2.1*

i get my connection back, the problem is that i can't find a way to run it on startup automatically

i tried writing it in a script in */etc/init.d*, and run *update-rc.d <script> defaults*
i also tried adding the add gateway line to */etc/rc.local*
nothing works...

what am i doing wrong?
please help

thanks,
Xiao Hu

---

### Post by cesargarcia on 2010-06-11
Try! activate ip_forward in the desktop:

echo 1 > /proc/sys/net/ipv4/ip_forward

This change is necessary every time you boot it.

---

### Post by alien878 on 2010-06-11
I had this happen once.  I could never figure out why it didn't pick up the GW from DHCP.

I think I fixed it by adding "gateway 192.168.2.1" to /etc/network/interface for the bridge.  It's been a while though.  I may have completely given up on DHCP and used static IP/Netmask too.

If that doesn't work, it might be that you need to set the IPs of eth0/eth1 to 0.0.0.0.  Unfortunately, the box I had with 2 eth ports died some time ago and I can't check.

---

### Post by XiaoHu on 2010-06-11
thanks a lot for your replies

i added the gateway line pretty much every second line in the /etc/network/interfaces file, and no luck

as for ip_forward, my problem is that i can't seem to add root commands to the startup. if i could i would add 'route add default gateway...' to startup.

here are the results of 'route' command before and after adding default gateway: (hope this helps...)
```
before gateway command:~> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 br0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    100    0        0 br0

after gateway command:~> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 br0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 br0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    100    0        0 br0

```

thanks,
Xiao Hu

---

### Post by alien878 on 2010-06-14
I think I see the problem.  Both eth1 and br0 show the same route and eth1 has a lower metric, so it is used.  However, with a bridge, the routing should be to br0.

Ideally, eth1 shouldn't have an IP address.  Only the bridge should have any IP address and routing.  I'm not 100% sure, but I think you can fix this by setting the ipaddress of eth0/eth1 to 0.0.0.0. (at least, all the bridge setups I've seen include ifconfig eth0/1 0.0.0.0)

If that doesn't work, force the metric of eth0/eth1 to be greater than br0.

---

### Post by XiaoHu on 2010-06-19
hi all and thank you for your replies.
especially alien878's that made me understand the cause for bridge+internet failure.
I tried zeroing the IPs of eth0/1, using *ifconfig eth0 0.0.0.0* but that simply took down the bridge altogether...

but, the good news, after some more seeking, i have found a solution that works for me (though i can't say i fully understand it).
this is how my new */etc/network/interfaces* file looks like:
```

auto lo
iface lo inet loopback

# Bridge between eth0 and eth1
auto br0
iface br0 inet dhcp
bridge_ports all

auto eth1
iface eth1 inet static
address 192.168.2.100
netmask 255.255.255.0
```

it is obvious that it works since the new route table looks like this:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         192.168.2.1     0.0.0.0         UG    100    0        0 br0
```
all br0 and no eth1

both bridge and internet work now.
thanks a lot!
XiaoHu

---

