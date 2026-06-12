---
title: "ubuntu as a router not working/ can't get to internet"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2010-04-29
I am trying to set up a basic router.  I am running ubuntu server 10.04(just installed it today!)  I have a verizon aircard(mobile broadband card) that is connected via usb.  I am using wvdial to "dial-up" the connection.  This works just fine and gives me a device on ppp0.  There is a single lan connection on eth0 set up as a static ip address under /etc/network/interfaces.  I don't even have any firewall running yet.  For whatever reason, I can only get out on the internet when eth0 is set to get its ip address through dhcp.  When I set it up with a static ip, I get for example:

$ping 4.2.2.2
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable.  

$ping google.com
ping: unknown host google.com


If, however, after I have booted and the wvdial has been started, I set up eth0 as dhcp, run /etc/init.d/networking restart, set it back as static, run /etc/init.d/networking restart again, all work well.  When I reboot the system with the static ip on eth0, and connect to wvdial, I get no internet again.  What am I doing wrong?!@?!?

---

### Post by DGortze380 on 2010-04-29
> **senor_smile said:**
> I am trying to set up a basic router.  I am running ubuntu server 10.04(just installed it today!)  I have a verizon aircard(mobile broadband card) that is connected via usb.  I am using wvdial to "dial-up" the connection.  This works just fine and gives me a device on ppp0.  There is a single lan connection on eth0 set up as a static ip address under /etc/network/interfaces.  I don't even have any firewall running yet.  For whatever reason, I can only get out on the internet when eth0 is set to get its ip address through dhcp.  When I set it up with a static ip, I get for example:

$ping 4.2.2.2
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable.  

$ping google.com
ping: unknown host google.com


If, however, after I have booted and the wvdial has been started, I set up eth0 as dhcp, run /etc/init.d/networking restart, set it back as static, run /etc/init.d/networking restart again, all work well.  When I reboot the system with the static ip on eth0, and connect to wvdial, I get no internet again.  What am I doing wrong?!@?!?

You're going to have to be a little more specific.

Which connection is going to be your WAN?
Which is LAN?
What is your LAN address scheme (IPs and Netmask)?
Have you enabled IP Forwarding?
Are you sure the firewall is open?
What do you mean it works when eth0 is DHCP? If there another DHCP Server on the network somewhere? Is this a stub network (One way in, one way out)?

Post the output of:

```
ifconfig
```

```
netstat -rn
```

```
cat /etc/network/interfaces
```

```
sudo iptables -L
```

---

### Post by Iowan on 2010-04-29
Server (*/etc/network/interfaces*) or desktop (Network Manager) install? (You did say server, but just to be sure...)
Did you set up DNS (*/etc/resolv.conf*), and what are results of **route -n**?

---

### Post by senor_smile on 2010-04-29
> **Iowan said:**
> Server (*/etc/network/interfaces*) or desktop (Network Manager) install? (You did say server, but just to be sure...)
Did you set up DNS (*/etc/resolv.conf*), and what are results of **route -n**?

Thanks for all of the advice guys.  I figured out that there was a default route being set up that was messing up the internet connection.  I fixed it by adding the following in my wvdial startup script:

```

route add gw dev ppp0

```

I left the device at my office so I don't have all of the specifics.  I will post the entire set up tomorrow so that any else that might be suffering similar problems can perhaps benefit.

---

