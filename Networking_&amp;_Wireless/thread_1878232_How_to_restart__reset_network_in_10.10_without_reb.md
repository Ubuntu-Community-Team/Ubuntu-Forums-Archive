---
title: "How to restart / reset network in 10.10 without reboot"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2011-11-09
Hello,

until recently I was facing a problem with my connection: while the system was booting, everything was ok, except the network connection-> it refused to connect, and no command was possible to enable networking without rebooting the system [the command /etc/init.d/networking restart did NOT work].

As a result:
i)navigate to
```
cd /etc/network
```
and change, as root, the contents of the file 
```
sudo vim interfaces
```
from
> auto lo
iface lo inet loopback
to this
> auto eth0
iface eth0 inet dhcp
if you have dynamic address.

If you cannot connect, the commands:
```
sudo ifdown eth0
sudo ifup eth0
```

would suffice.

Regards!

---

### Post by haqking on 2011-11-09
you can also just:

```
sudo service networking restart
```

or

```
sudo service networking start
```

or

```
sudo service networking stop
```

depending on what you want to do

---

### Post by Claus7 on 2011-11-09
Hello,

> **haqking said:**
> you can also just:

```
sudo service networking restart
```

or

```
sudo service networking start
```

or

```
sudo service networking stop
```

depending on what you want to do

thank you for the feedback! I have to admit that I hadn't checked the command with the service string. This problem was troubling me for a long time, and now it seems that it is "nailed", as it was one of the -final- bugs/problems that I was facing.

Regards!

---

### Post by haqking on 2011-11-09
> **Claus7 said:**
> Hello,



thank you for the feedback! I have to admit that I hadn't checked the command with the service string. This problem was troubling me for a long time, and now it seems that it is "nailed", as it was one of the -final- bugs/problems that I was facing.

Regards!

no worries you are welcome.

Remember to mark the thread as solved if yours or mine was a solution others can use.

Cheers

---

### Post by Claus7 on 2011-11-09
Hello,

> **haqking said:**
> no worries you are welcome.

Remember to mark the thread as solved if yours or mine was a solution others can use.

Cheers

since this thread is a how to, then is supposed not to be a question or query, yet to provide a guide or tips right away. If you check my other threads that I have created all these years, you will be able to see that I do keep in mind to mark a solved thread as such. Thank you for the nice conversation.

Regards!

---

### Post by Claus7 on 2011-11-13
Hello,

the other time I faced exactly the same problem, ALL the aforementioned solutions in this thread did not solve the problem. Those commands were working ONLY while the system had booted normally and I had the ability to switch on and off the network.

IF the system was booting without the network enabled, the aforementioned commands DID NOT work!

While searching a little bit more, I found out that this is a bug of dhcp which affects maverick and maybe other distros as well. As a result I decided to install the package dhcp3-server from 11.04 deb file.

I'll record what is happening, yet up to know things are booting normally.

Regards!

---

### Post by Claus7 on 2012-01-08
Hello,

with the aforementioned process, network was working nice for a couple of months with minor problems, yet the last week my network was horrible. 

I was trying to reboot at least 5 times before managing to connect. Also I was trying to shutdown and then starting my ubu box which finally resulted in connecting to the net.

I tried in-between this solution here:
[http://mydailyhash.wordpress.com/2010/10/11/ubuntu-10-10-maverick-meerkat-network-problem/](http://mydailyhash.wordpress.com/2010/10/11/ubuntu-10-10-maverick-meerkat-network-problem/)

to no avail (maybe things got worse).

Now I have removed:
network-manager
and
network-manager-gnome
from synaptic

and installed 
network-manager-kde

My system required restart. On my first reboot, things seems to work. I did not alter anything else.

Regards!

---

