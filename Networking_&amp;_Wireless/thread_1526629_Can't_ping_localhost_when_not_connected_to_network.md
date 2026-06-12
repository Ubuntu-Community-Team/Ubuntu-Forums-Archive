---
title: "Can't ping localhost when not connected to network"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by DanDare on 2010-07-08
Hi there, 

As the title says, I'm having trouble pinging localhost, specifically, pinging localhost when I'm not connected to a network.

When I try it keeps telling me the operation is not permitted:
```
matt@mubuntu:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```

But if I connect to the network, start pinging then disconnect it continues pinging.

Google seems to think it could be something to do with my iptables setup:
```
matt@mubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        
```

Or my routes:

When connected to network
```
matt@mubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```


When not connected to network
```
matt@mubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo

```

But as far as I can tell there isn't anything in there which would stop me connecting to the localhost (I also can't connect to my local apache instance when offline)...

I'm at a loss as to what to do, does anyone have any ideas as to what I'm doing wrong. :(

(It's worth mentioning that a couple of weeks ago I had the pc setup to share it's internet connection with a laptop, ala [this guide]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), however I've since disabled the iptables rules and disabled ip forwarding.)

---

### Post by DanDare on 2010-07-08
Ok, [turning off iptables]("https://help.ubuntu.com/community/IptablesHowTo") got it working but I have no idea why...

Is there a reason behind it blocking access to localhost only when disconnected from the network and is there some way to fix this?

---

### Post by Iowan on 2010-07-08
Apparently, I'm already off-base, but...
What is in your **/etc/hosts** file?

---

### Post by DanDare on 2010-07-09
Hi Iowan,

Not quite sure how but since iptables was disabled everything's been working fine, even when iptables was re-enabled.

It seems very odd... :confused:

Thanks for your help anyway!

---

### Post by Iowan on 2010-07-09
Odd, indeed...
Give it a couple of days to see if it *stays* working before marking the thread [SOLVED]. :)

---

### Post by laugh on 2011-10-31
i have the same problem but it didn't get resolved by switching off iptables.

as soon as i disconnect from internet (with gui networkmanager), both "ping localhost" and "ping 127.0.0.1" return:

ping: sendmsg: Operation not permitted

i switched off iptables, "iptables -L" gives:

```
Chain INPUT (policy ACCEPT)

target prot opt source destination

Chain FORWARD (policy ACCEPT)

target prot opt source destination

Chain OUTPUT (policy ACCEPT)

target prot opt source destination
```

/etc/hosts contents:

```

127.0.0.1	localhost
127.0.0.1	glocalhost
127.0.1.1	ubuntu.ubuntu-domain	ubuntu

```

route -n with network on

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```

route -n with network off is empty:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

### Post by laugh on 2011-10-31
oh, right, i don't have loopback interface

it's described in /etc/network/interfaces though

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

what should i change to turn it on?

---

### Post by laugh on 2011-11-01
ps.

```
sudo ifconfig lo up
```

doesn't change anything

---

### Post by laugh on 2011-11-05
help anyone?

i am a web developer and live in country where electricity often goes off, so i cannot develop when i don't have wireless :(
because localhost is inaccessible and all my local servers stop being accessible(i have apache and nginx)

---

### Post by laugh on 2011-11-05
help anyone?
it's bigger than it seems - i am a web developer and live in country where electricity often goes off, so currently i cannot develop when i don't have wireless :( because localhost is inaccessible and all my local servers stop being accessible(i have apache and nginx and rack)

---

