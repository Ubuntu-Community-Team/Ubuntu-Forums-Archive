---
title: "Guest - Host Can't ping each other"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by BaNzounet on 2012-09-26
Hi ! 

I'm trying to set up a virtual machine on an Ubuntu Server 12.04, but at the moment I've some difficulties to ping internet/host...

I'm really bad with network stuff so, If you could help me it would be great !!

So First of all I added a bridge br0 in my /etc/network/interface
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual 

auto br0
iface br0 inet static
        address 188.***.***.*** 
        network 188.***.***.0
        netmask 255.255.255.0
        broadcast 188.***.***.255
        gateway 188.***.***.254
        bridge_ports eth0
        bridge_fd 9
        bridge_stp off


```

After a restart there is my ifconfig : [http://pastebin.com/vySHFusF](http://pastebin.com/vySHFusF)

And there is the command I'm using to start my vm : 
```
qemu-system-x86_64 -hda vdisk.img -m 7168  -net nic,macaddr=DE:AD:BE:EF:49:46 -net tap,vlan=0,ifname=tap1 -vnc :0 -daemonize 

```

After that I'm lost, I don't know what to do to set up correctly an ip on my guest, and forwad stuff to it :confused:

Edit : There are my current route :
```

#route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
188.***.***.0   0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
10.0.42.0       0.0.0.0         255.255.255.0   U     0      0        0 tap0
0.0.0.0         188.***.***.254 0.0.0.0         UG    100    0        0 br0


```



Any help appreciated :)
BaNzounet

---

### Post by omegamu on 2012-09-26
Just a question did you set the ip for the VM? and have you looked in /etc/sysconfig/network

---

### Post by BaNzounet on 2012-09-26
Thanks for taking the time to help me :)

I'm not really sure how we do that so, let's say no :/
I tried : #ifconfig tap1 10.0.52.101 up (tap1 is the interface created when I'm lauching my vm)

But it's not really working(because when I'm doing ssh 10.0.52.101 I'm doing a ssh on the Host) so I guess it's not the right way to do that...s

---

