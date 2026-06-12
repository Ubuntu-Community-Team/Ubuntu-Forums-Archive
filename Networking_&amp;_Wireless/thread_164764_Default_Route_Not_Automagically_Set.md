---
title: "Default Route Not Automagically Set"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by OwlManAtt on 2006-04-23
Howdy, 

I've got a static IP set up in /etc/network/interfaces:

```
nevans@eron:/etc/init.d$ cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# mapping hotplug
#       script grep
#       map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.16.0.25
        netmask 225.225.0.0
        broadcast 172.16.255.255
        gateway 172.16.0.1
```

And eth0 comes up fine and dandy.

```
nevans@eron:~$ ping 172.16.1.40
PING 172.16.1.40 (172.16.1.40) 56(84) bytes of data.
64 bytes from 172.16.1.40: icmp_seq=1 ttl=64 time=0.216 ms
64 bytes from 172.16.1.40: icmp_seq=2 ttl=64 time=0.144 ms

--- 172.16.1.40 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.144/0.180/0.216/0.036 ms
```

Unfortunately, I cannot ping anything outside of my LAN. I have determined that the problem is my routes:

```
nevans@eron:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.0.0      *               255.255.0.0     U     0      0        0 eth0
```

Because when I do `sudo route add default gw 172.16.0.1`, it adds the appropriate route and this machine can access the Internet.

So my question: Why isn't this being set at boot? I have 172.16.0.1 as my gateway for the interface. What do I need to do to fix this so I don't have to run that command every boot?

Thanks in advance.

---

### Post by OwlManAtt on 2006-04-23
I solved the problem with a big ol' hack.

I added the route command to /etc/init.d/networking. 

I know it's not a clean solution. But it works.

---

### Post by mips on 2006-04-23
I don't know why it is not working but I could probably tell you how to fix it.

Edit your /etc/network/interfaces and add the following line after the gateway statement:
```
up route add default gw 172.16.0.1 dev eth0
```

---

