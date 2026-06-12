---
title: "Connecting two routers to each other?"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2013-04-10
Recently I got a second wireless router, along with a second DSL line.  I'm planning on running any bandwidth intensive applications on a computer using the second line, and the other devices will use the first.  The problem is, I want to be able to ssh into the computer, but it's not using the same router.  Is there any way I can connect the two routers together, so that a device connected to router A can communicate with a device connected to router B?

---

### Post by Doug S on 2013-04-11
You really have two independent networks. Set up router B to do port forwarding of whatever port is used for SSH (22 if default, or whatever you changed it to if not) to the computer on network B. Router A should not need any special setup.

---

### Post by Stonecold1995 on 2013-04-11
> **Doug S said:**
> You really have two independent networks. Set up router B to do port forwarding of whatever port is used for SSH (22 if default, or whatever you changed it to if not) to the computer on network B. Router A should not need any special setup.
Yeah I know they're independent.

How do I set up port forwarding to the second router?

---

### Post by ppjdee on 2013-04-11
Don't know if this really helps you or not. [http://www.wikihow.com/Set-Up-Port-Forwarding-on-a-Router](http://www.wikihow.com/Set-Up-Port-Forwarding-on-a-Router)

---

### Post by Doug S on 2013-04-11
There is also [http://portforward.com/](http://portforward.com/) which is a very popular site, and has insturctions for a great many routers.

---

### Post by Stonecold1995 on 2013-04-11
With this setup, can computers on router A communicate with computers on router B *and* the other way around?  And if so, how would I SSH into the computer, what internal IP adderss would I use to connect to a specific computer?

---

### Post by Iowan on 2013-04-11
I'll admit I haven't checked the links (perhaps I should). My perception of port forwarding is that all requests for a specific port (e.g. 22) would be forwarded to a specific computer. (probably not what you had in mind)

---

### Post by Hadaka on 2013-04-11
Hi, here is a little visual and starting point for you.

computer A
computer A's IP (192.168.1.102)
computer A's "listen" port (2224)
computer A's ROUTER IP (75.120.35.104)
computer A's ROUTER Portforward port 2224 to 192.168.1.102

computer B
computer B's IP (192.168.1.103)
computer B's "listen" port (2225)
computer B's ROUTER IP (75.120.35.105)
computer B's ROUTER Portforward port 2225 to 192.168.1.103

A to B    ssh -p2225 user@75.120.35.105 (B's listen port and router ip)
B to A    ssh -p2224 user@75.120.35.104 (A's listen port and router ip)

This is of course After you set up ssh on both networks.
some guides..
[http://canyouseeme.org/](http://canyouseeme.org/)       <- to find your routers ip
[https://help.ubuntu.com/11.10/serverguide/openssh-server.html](https://help.ubuntu.com/11.10/serverguide/openssh-server.html)
[http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/](http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/)
*Port forwarding is router dependant...
search....(example) Linksys port forwarding..

*   IMPORTANT * be certin to set security and have keys once you have it all
figured out...if not...atleast do ..
```
sudo service ssh stop
```
to turn off ssh while you figure it out.
have fun..

---

### Post by Stonecold1995 on 2013-04-20
> **Hadaka said:**
> Hi, here is a little visual and starting point for you.

computer A
computer A's IP (192.168.1.102)
computer A's "listen" port (2224)
computer A's ROUTER IP (75.120.35.104)
computer A's ROUTER Portforward port 2224 to 192.168.1.102

computer B
computer B's IP (192.168.1.103)
computer B's "listen" port (2225)
computer B's ROUTER IP (75.120.35.105)
computer B's ROUTER Portforward port 2225 to 192.168.1.103

A to B    ssh -p2225 user@75.120.35.105 (B's listen port and router ip)
B to A    ssh -p2224 user@75.120.35.104 (A's listen port and router ip)

This is of course After you set up ssh on both networks.
some guides..
[http://canyouseeme.org/](http://canyouseeme.org/)       <- to find your routers ip
[https://help.ubuntu.com/11.10/serverguide/openssh-server.html](https://help.ubuntu.com/11.10/serverguide/openssh-server.html)
[http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/](http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/)
*Port forwarding is router dependant...
search....(example) Linksys port forwarding..

*   IMPORTANT * be certin to set security and have keys once you have it all
figured out...if not...atleast do ..
```
sudo service ssh stop
```
to turn off ssh while you figure it out.
have fun..
So this has to go through the ISPs of both routers instead of directly?  How fast would this be (latency, bandwidth, etc)?  The main reason I ssh between computers is so I can use scp to transfer large files without needing to use a flash drive.  I assume going through two ISPs and two VPNs in a long detour around the world would be very impractical when the two computers I want to connect are probably only 50 feet away, or less.

Is there no way to *directly* connect the routers, via Wi-Fi or even solid Ethernet?

---

### Post by Hadaka on 2013-04-20
Hi,, the speed will be determined by your current
isp speed,your internal processor,and type of modem/router.
the distance is not important. I have a very like set up
running 2 routers on 2 different networks. one is Fios
one is not. I dont see any lag when doing local or sharing
files with someone 3,000 miles away. I would imagine there
may be a different or better way,as i am no expert i only
set it up to work with the knowledge i had. Try it, if nothing
else its a nice learning process.
good luck !

---

### Post by Stonecold1995 on 2013-04-22
> **Hadaka said:**
> Hi,, the speed will be determined by your current
isp speed,your internal processor,and type of modem/router.
the distance is not important.
My ISP speed is fairly low.  My CPUs are good though.  And my router is good.  Also each computer uses a VPN, so the packets would have to go from my computer, to Sweden, then to the Netherlands, then back to the other computer.  Each VPN is pretty slow, so if I have to go through both the speed would be unusable.

Also I thought distance was very important?  Higher distance means higher latency, and sometimes speed if it has to go through slow servers.

---

### Post by SeijiSensei on 2013-04-22
Personally I'd just throw another Ethernet card in the box that you want to connect to over SSH.  Then connect that card to the other router so the machine has an address in both subnets.  Just make sure the two routers allocate addresses in separate subnets, say 192.168.0.0/24 and 192.168.1.0/24.  

Say the computer you wish to connect to is attached to router B.  Add an ethernet card to this box, then connect it to one of the LAN ports on router A.  Now Linux will automatically route traffic for addresses managed by router A to that box.  If, for some weird reason, the computer connected to router B loses its Internet connectivity,  use static addressing for the interface that points to router B and set its default gateway to router B's LAN address.  This shouldn't be necessary in practice.

---

### Post by Stonecold1995 on 2013-04-22
> **SeijiSensei said:**
> Personally I'd just throw another Ethernet card in the box that you want to connect to over SSH.  Then connect that card to the other router so the machine has an address in both subnets.  Just make sure the two routers allocate addresses in separate subnets, say 192.168.0.0/24 and 192.168.1.0/24.  

Say the computer you wish to connect to is attached to router B.  Add an ethernet card to this box, then connect it to one of the LAN ports on router A.  Now Linux will automatically route traffic for addresses managed by router A to that box.  If, for some weird reason, the computer connected to router B loses its Internet connectivity,  use static addressing for the interface that points to router B and set its default gateway to router B's LAN address.  This shouldn't be necessary in practice.
How do I do this?

---

### Post by SeijiSensei on 2013-04-23
Hmm, I thought I was pretty clear before.

First, you need an Ethernet card and cable.  I don't know of an Ethernet card that isn't supported by the Linux kernel, but I generally stick to [Intel hardware]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033"), though it runs a bit more expensive than some budget cards.  Just make sure you have an available slot, and that you know what standard the motherboard connector uses.  The card I linked to is a PCI Express device, and it supports Gigabit Ethernet speeds.  Here's a [10/100 card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166004") that fits in a PCI slot and costs about $10.

If the target machine is a laptop, or you don't want to muck about inside the machine, you can add another interface with a [USB adapter]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010064%20600016288&IsNodeId=1&name=USB").  [This one](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166087) is known to be [supported]("http://cateee.net/lkddb/web-lkddb/USB_NET_MCS7830.html") by the Linux kernel.

Now the only thing you need is a length of Ethernet cable.  After you install the adapter on the target machine, running "ifconfig" should show you two interfaces eth0 and eth1.  Eth0 should be connected to this machine's Internet router, as it was before.  Now connect the new adapter to one of the LAN ports on the other router.  It should get an address via DHCP in the same subnet as the rest of that router's LAN. You should now be able to ping the address given to the new interface and connect to machine with SSH.

This is almost harder to describe than it is to do in practice!

---

### Post by Stonecold1995 on 2013-04-23
> **SeijiSensei said:**
> Hmm, I thought I was pretty clear before.

First, you need an Ethernet card and cable.  I don't know of an Ethernet card that isn't supported by the Linux kernel, but I generally stick to [Intel hardware]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033"), though it runs a bit more expensive than some budget cards.  Just make sure you have an available slot, and that you know what standard the motherboard connector uses.  The card I linked to is a PCI Express device, and it supports Gigabit Ethernet speeds.  Here's a [10/100 card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166004") that fits in a PCI slot and costs about $10.

If the target machine is a laptop, or you don't want to muck about inside the machine, you can add another interface with a [USB adapter]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010064%20600016288&IsNodeId=1&name=USB").  [This one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166087") is known to be [supported]("http://cateee.net/lkddb/web-lkddb/USB_NET_MCS7830.html") by the Linux kernel.

Now the only thing you need is a length of Ethernet cable.  After you install the adapter on the target machine, running "ifconfig" should show you two interfaces eth0 and eth1.  Eth0 should be connected to this machine's Internet router, as it was before.  Now connect the new adapter to one of the LAN ports on the other router.  It should get an address via DHCP in the same subnet as the rest of that router's LAN. You should now be able to ping the address given to the new interface and connect to machine with SSH.

This is almost harder to describe than it is to do in practice!
Both computers are laptops, and neither will be able to be plugged into Ethernet.

---

### Post by SeijiSensei on 2013-04-24
Use a [USB adapter]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010064%20600016288&IsNodeId=1&name=USB").

---

