---
title: "Confusing network issue"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by lkhnet on 2009-01-28
Last night I did a fresh install of Ubuntu Server 8.04 on a Dell Optiplex GX620 PC as I am wanting to set up an IRC box for an online community.

Everything went fine during the install, and after selecting the SSH and LAMP servers, it booted up.

The problem is though that I am unable to ping any other IP addresses on the network and nothing else is able to ping this new Ubuntu server. I get "Destination unreachable" but when I do ifconfig it lists eth0 with having the right IP address, gateway, subnet mask, broadcast, etc. I have tried changing the cable, the port on the switch and have rebooted both the switch and router. My PC is connected to the same switch and router and doesn't have any problems at all.

I have an old copy of Ubuntu 7.10 here and with a fresh reinstall of this the same thing happens. Any ideas please? I'm completely stumped.

Cheers.
Liam.

---

### Post by Iowan on 2009-01-28
You might need to disable **ufw** and try it again.  I suspect you'll eventually want the firewall active, though.

---

### Post by lkhnet on 2009-01-28
Hey Iowan,

Thanks for the reply... I've actually tried sudo apt-get remove ufw just to see whether it made a difference, and it didn't :(

I've also changing the IP address and putting it on a completely seperate network and that didn't work either.

Any other ideas?

---

### Post by bgerlich on 2009-01-28
What does "route" say ?

---

### Post by albinootje on 2009-01-28
> **lkhnet said:**
>  The problem is though that I am unable to ping any other IP addresses on the network and nothing else is able to ping this new Ubuntu server. I get "Destination unreachable"

What gives :
```

mtr ping.xs4all.nl
sudo apt-get update

```
?
And forget about blaming ufw, 7.10 didn't have that.
Use this to check whether you have any firewalling or not :
```

sudo iptables -L -n

```

---

### Post by lkhnet on 2009-01-28
Hi,

When I run mtr ping.xs4all.nl nothing happens, but when I just run "mtr" on it's own I get the following?

Chain  INPUT    (policy accept)
Target  Prot  Op  Source       Destination

Chain  FORWARD  (policy accept)
Target  Prot  Op  Source       Destination

Chain  OUTPUT   (policy accept)
Target  Prot  Op  Source       Destination

Also when I run sudo iptables -L -n I get the following;

Host         Loss   SNT   Last   Avg   etc..
127.0.0.1    0.0%   0.0%  0.0%   0.0%  0.0%

I'm unable to run sudo apt-get update as there's no connectivity, but when I do it tries connecting to one of the repositories and then just times out.

Thanks for the help so far, but any other ideas please?

---

### Post by bgerlich on 2009-01-28
Post the output of "route".

Also try "ping localhost" - this one should be working fine, if not post the error message.

---

### Post by albinootje on 2009-01-28
> **lkhnet said:**
>  I'm unable to run sudo apt-get update as there's no connectivity

Can you post the output of :
```

ifconfig -a
route -n
cat /etc/resolv.conf
ping -c3 62.108.1.65

```

---

### Post by lkhnet on 2009-01-28
Here's the results;

**ifconfig -a**
Link encap: Ethernet
HWAddr: 00:13:72:D5:FF:68
Scope: Link Up BROADCAST RUNNING MULTICAST
MTU: 1500
Metric: 1
RX Packets: 3866
Errors:: 0
Dropped: 4381

**route -n**
Destination     Gateway     Genmask            Metric
78.32.11.*      0.0.0.0     255.255.255.240    0
0.0.0.0         78.32.11.*  0.0.0.0            100

**cat /etc/resolv.conf**
78.32.11.A and 78.32.11.B

**ping -c3 62.108.1.65**
Destination host unreachable

Apologies if I have missed something its just that I only have the one monitor and need to swap it back and forth.

Thanks.

---

### Post by albinootje on 2009-01-28
> **lkhnet said:**
> Here's the results;

**ifconfig -a**
Link encap: Ethernet
HWAddr: 00:13:72:D5:FF:68
Scope: Link Up BROADCAST RUNNING MULTICAST
MTU: 1500
Metric: 1
RX Packets: 3866
Errors:: 0
Dropped: 4381


Well, in your OP you wrote :
>  but when I do ifconfig it lists eth0 with having the right IP address, gateway, subnet mask, broadcast, etc. 

but here in your comment ifconfig doesn't show any ip address.
(And your /etc/resolv.conf looks weird, but maybe that's because you were writing it down yourself)
Can you do a :
```

sudo dhclient
ping -c3 62.108.1.65

```

---

### Post by lkhnet on 2009-01-28
Ah, sorry about that I missed half of the details out!

inet addr:   78.32.11.*
bcast:       78.32.11.*
mask:        255.255.255.240

I can't set it to pick up an IP via DHCP as there's no DHCP server on the network. I've configured (or should that be trying to) with a single external IP address.

Thanks

---

### Post by albinootje on 2009-01-28
> **lkhnet said:**
>  I can't set it to pick up an IP via DHCP as there's no DHCP server on the network. I've configured (or should that be trying to) with a single external IP address.

Okay, you wrote this in your OP
> 
My PC is connected to the same switch and router and doesn't have any problems at all.

Does that PC (MS-Windows? Ubuntu? or?) have the exactly the same settings except for the ip address ?

And I assume you're using the .* to cover your complete ip address (etc).
However, now we can't even see whether the broadcast address is correct.

---

### Post by lkhnet on 2009-01-28
I have changed the IP address of my PC (Windows XP) to the next IP. For example the Ubuntu server is .11, I've set my PC to .12. The broadcast address is correct as I have double checked this, and it's the one which was auto assigned when I configured the IP settings when installing Ubuntu. 

For info, the Subnet mask is 255.255.255.240.

---

### Post by albinootje on 2009-01-28
> **lkhnet said:**
> I have changed the IP address of my PC (Windows XP) to the next IP. For example the Ubuntu server is .11, I've set my PC to .12. The broadcast address is correct as I have double checked this, and it's the one which was auto assigned when I configured the IP settings when installing Ubuntu. 

For info, the Subnet mask is 255.255.255.240.

And you can ping the ip address of the XP machine from your Ubuntu box ?
And can you ping the ip address of your router ?

---

### Post by lkhnet on 2009-01-28
From the Ubuntu box I can't ping anything at all.. I have tried pinging the router, other computers and hosts out on the 'net and each time I get back host unreachable. The only thing I can ping from the Ubuntu box is it's own IP and localhost.

I can't ping the Ubuntu box from anywhere else either... just doesn't get through. Really weird.

---

### Post by albinootje on 2009-01-28
> **lkhnet said:**
>  I can't ping the Ubuntu box from anywhere else either... just doesn't get through. Really weird.

Can't you run a dhcp server on that XP machine, and see whether that change will work for your Ubuntu box ?

---

### Post by speed32219 on 2009-01-28
For grins, what is the output of ipconfig on the xp machine

---

