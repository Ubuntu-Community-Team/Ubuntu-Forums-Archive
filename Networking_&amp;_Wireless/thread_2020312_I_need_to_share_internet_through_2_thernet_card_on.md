---
title: "I need to share internet through 2 thernet card on my Ubuntu"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by dhirajpatra on 2012-07-08
I have Ubuntu 12.04 in my desktop along with 2 ehternet card.

eth0 is connected with my fiber optic broad band internet connection and setting is DHCP.

eht1 is trying to share the internet with cross over cable to my laptop (Windows xp).

eht1 IP setting is 192.168.0.1, mask:255.255.255.0, gateway:192.168.0.1, dns:208.67.220.220 and 208.67.222.222

Client / windows xp IP setting as 192.168.0.2, 255.255.255.0, 192.168.0.1, 208.67.220.220,208.67.222.222

Also use this url [https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

Now I can ping from cleint and also from server and sucessfull. But internet not sharing.

Please give me suggestions and fix to share the internet with 2 cards.

Thanks a lot in advance.

---

### Post by praseodym on 2012-07-08
Try:

Host (Ubuntu):
eth0 DHCP

eth1 static, add the MAC-address of eth1, and use "together with other clients" (dont know the english phrase ;-) )

Client (Windows):

DHCP

Check the MAC with:

```
ifconfig eth1 | grep Hard | awk {'print $1,$4,$5,$6'} 
```

---

### Post by sona1111 on 2012-07-08
I have done this. This is the kind of thing you want:

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

after installing bridge utils you should put something like this in your /etc/network/interfaces file:

```

#connection1
auto eth0
iface eth0 inet manual
up ip link set eth0 up

#connection 2
auto eth1
iface eth1 inet manual
up ip link set eth1 up

#main bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1
bridge_fd 0
bridge_hello 2
bridge_maxage 12
bridge_stp on

```

(and also anything else you had there, like the lo interface)

after this try a sudo /etc/init.d/networking restart and that should do the trick. at least it did for me.

---

