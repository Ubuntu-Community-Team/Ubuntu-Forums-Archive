---
title: "Network not working"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by zizther on 2011-02-22
Hi,

I am currently using a minimal version of 10.10. I was able to setup the network at my friends house where I installed Ubuntu, i have now tried to set it up at home, but i am unable to connect to the internet, i am using a ethernet cable to my router, the system itself is a Beagleboard.

To access the internet i have had to write these into the terminal:

sudo ifconfig eth1 192.168.1.15 netmask 255.255.255.0
sudo route add default gw 192.168.1.254

As you see i am having to use eth1, rather than eth0, which i had to use at my friend's.

I have looked at a range of threads on this and have tried a few things, but nothing has worked yet.


All that is in my /etc/network/interfaces is:

auto lo
iface lo inet loopback



The settings seem OK when i view ifconfig -a, i get:

inet addr: 192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0



Any help would be great.

---

### Post by Grenage on 2011-02-22
Your router isn't configured to give out IP addresses by DTCP?  Why are you using the terminal, rather than the GUI's Network manager?

How many network ports does your machine have?

---

### Post by zizther on 2011-02-22
Hi,

The beagleboard currently only has one ethernet port

---

### Post by Grenage on 2011-02-22
I've not heard of beagleboards before, they look great.  Does your router support DHCP, have you received an IP automatically with any other machines?

---

### Post by zizther on 2011-02-22
They are good little things, not much resource, thus me having to install the minimal version of 10.10, it did have a full version of Debian on it, but was un-usable.

All other PC's and Mac's receive an IP address OK. I don't think the minimal version came with the Network manager, or it is not turned on, but without the internet I cannot install it.

---

### Post by Grenage on 2011-02-22
> **zizther said:**
> They are good little things, not much resource, thus me having to install the minimal version of 10.10, it did have a full version of Debian on it, but was un-usable.

All other PC's and Mac's receive an IP address OK. I don't think the minimal version came with the Network manager, or it is not turned on, but without the internet I cannot install it.

Well you've added an IP and route, but what about DNS servers?  Add your router's IP in */etc/resolv.conf*.

```
nameserver 192.168.1.254
```

---

### Post by zizther on 2011-02-22
Thanks, that has sorted it!
I guess if i want to use another network i may have to change this?

---

### Post by zizther on 2011-02-22
**duplicate**

---

### Post by Grenage on 2011-02-22
> **zizther said:**
> Thanks, that has sorted it!
I guess if i want to use another network i may have to change this?

Great!

Yes, if you're sticking with static IP addresses.  I've never used DHCP via a command line, but I imagine it would automatically put in the DNS addresses when it gets a lease.

---

### Post by Charlietje on 2011-02-22
Why do you need eth1? Does it exist? Is it up?
What is default gateway?  192.168.1.254 are you sure of that?

What is the output of:
```
ip a
```

---

