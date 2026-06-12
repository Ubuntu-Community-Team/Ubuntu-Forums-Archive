---
title: "Cant' ping OWN eth0"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by Roque on 2009-04-02
I reinstalled kubuntu 8.04 in PC#1 and made no change to its configuration.

Plugged the ethernet cable to the Realtek 8139/8139C/8139C+ card, the green light turned on. The machine at the other end of the cable (PC#2, Kubuntu 8.04 **untouched**) also has the same Realtek card. 

In PC#1 did:
```
sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0
sudo ifconfig eth0 up

```
In PC#2 did:
```
sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0
sudo ifconfig eth0 up

```

In PC#1 tried to ping **its own** eth0 interface:
```
ping 192.168.0.1
connect: Network is unreachable

```

Then in the same PC#1 tried to ping **the other** PC ethernet interface:
```
ping 192.168.0.2
connect: Network is unreachable

```

This works perfectly if both PCs are running Knoppix (versions 4.0 and 6.0). And also I can ping both machines from each other.

If I leave Knoppix running in PC#2 and run Kubuntu in PC#1 the problem appears again.

What could be causing this? iptables is set to ACCEPT everything by default policies, so it can't be the firewall's fault.

---

### Post by gdave on 2009-04-02
likely an issue with your routing table.  what's it look like?

---

### Post by Roque on 2009-04-02
Well, I (kind of) found what was going wrong. I was taking for granted that only the ethernet interface of the rebooted PC needed to be reset and re-upped, but apparently even if only one of the two machines is rebooted then the interfaces in **both** PCs need to be reconfigured and re-upped again. 
Is this true? Seems to be very inconvenient...

> likely an issue with your routing table. what's it look like?
Thanks for the help. But aren't both PCs in the same subnetwork? In this case a routing table isn't needed, right?

---

### Post by gdave on 2009-04-02
no, of course you do not need to reconfigure both machines after one reboots.  that will never happen.

you still need a routing table that routes 192.168.0.0/24 out eth0 on both computers, assuming eth0 is the correct interface.

you should see an entry like this:

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

---

### Post by Roque on 2009-04-02
> no, of course you do not need to reconfigure both machines after one reboots. that will never happen.
 
Thanks for the help. However, the opposite *seems* to be the case. I reboot PC#1 and then of course I must do:
```
sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0
sudo ifconfig eth0 up

```
because the network is still not permanently configured. But I also *must* reconfig PC#2:
```
sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0
sudo ifconfig eth0 up

```

Otherwise I can't ping PC#2 from PC#1 anymore:
```
ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable

```

Weird...

---

### Post by superprash2003 on 2009-04-03
how about specifying the gateway and stuff.. for 1 machine , enter ip as 192.168.0.1 and gateway 192.168.0.1 .. for other machine enter ip as 192.168.0.2 and gateway 192.168.0.1  . make these changes in the /etc/network/interfaces file and restart networking by typing sudo /etc/init.d/networking restart

---

### Post by namaku0 on 2009-04-03
Do you have loopback interface? If not set it on
*/etc/network/interface* by adding these lines:
[B]auto lo
iface lo inet loopback[/B]
and then restart the networking by running this
command:
**sudo /etc/init.d/networking restart**

---

### Post by gdave on 2009-04-03
no gateway needed for LAN-only access.  

We still need to see your routing table. and also show your interface configuration/setup.  display the results from these 3 commands:

```
route -n

ip link show

cat /proc/net/dev
```

---

### Post by Roque on 2009-04-03
> how about specifying the gateway and stuff.. for 1 machine , enter ip as 192.168.0.1 and gateway 192.168.0.1 .. for other machine enter ip as 192.168.0.2 and gateway 192.168.0.1 . make these changes in the /etc/network/interfaces file and restart networking by typing sudo /etc/init.d/networking restart
A gateway setup is not needed for this most basic ethernet connection. But I made the interfaces' new configuration persistent in /etc/network/interfaces and now I can reboot each machine independently without needing to reset the iface at the other end.

> Do you have loopback interface? If not set it on
 /etc/network/interface by adding these lines:
 auto lo
 iface lo inet loopback
 and then restart the networking by running this
 command:
 sudo /etc/init.d/networking restart
Thanks, but everything is Ok there.

> no gateway needed for LAN-only access. 
 
We still need to see your routing table. and also show your interface configuration/setup. display the results from these 3 commands:

I just solved the problem: everything works fine, but thanks anyways. 

Again, many thanks for the help guys, now I have a persistent working connection between my PCs.

---

### Post by CyberMando on 2009-04-03
Some NICs will rengotiate without being forced to and others will not.

---

