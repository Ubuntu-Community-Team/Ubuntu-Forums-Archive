---
title: "dhcpd3 not configured to listen on any interfaces"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by generic-coder on 2009-07-10
Hello every body.
I have a problem with my dhcp3-server and i will like to get some help please.
I have two network cards on my pc. One is connected to a wired router and the other is connected to a wireless network access point (AP). I am running ubuntu 9.04 desktop.

Eventually i want all my wireless clients to get internet through the desktop using NoCat. 
I have installed a dhcp3-server to serve ip addresses to the AP connected to eth0.

This is what i have in my /etc/default/dhcp3-server
```

INTERFACES="eth0"

```And in my dhcpd.conf, this is what i have

```

subnet 192.168.1.0 netmask 255.255.255.224 {
  range 192.168.1.26 192.168.1.30;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  option subnet-mask 255.255.255.224;
  default-lease-time 86400;
  max-lease-time 86400;
}

```when i run dhcpd3 eth0, i get this error message
```

Wrote 3 leases to leases file.

No subnet declaration for eth0 (169.254.6.137).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **


Not configured to listen on any interfaces!

```Can somebody please tell me what i am doing wrong?
Cheers

---

### Post by superprash2003 on 2009-07-10
here is how my dhcp file looks

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.254;
option domain-name-servers 208.67.222.222, 208.67.220.220;
option domain-name &#8220;HOME&#8221;;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.15;
}

---

### Post by generic-coder on 2009-07-10
Nope, nothing is happening, still the same error message...

---

### Post by generic-coder on 2009-07-10
Anybody any idea please?

---

### Post by jonobr on 2009-07-10
Hello


Im not so sure about your subnetting,

Your using a /27 which should give a subnet range of
192.168.1.1 to 192.168.1.30 and a broadcast of 192.168.1.31

Your broadcast seems to be .255 Im not sure thats correct?

Im also wondering if you could not use classic IP without subnetting,
Ie using a regular /24 network?

---

### Post by generic-coder on 2009-07-10
Ok, I got the dhcp3-server working on eth0 by putting these lines in the interfaces file

```

iface eth0 inet static
    address 192.168.1.10
    network 192.168.1.0/24
    netmask 255.255.255.0
    broadcast 192.168.1.255
auto eth0

```

Currently i have a windows laptop connected to the AP, and an ubuntu desktop. I have tried to ping both machines from each other, but they are just not able to reach each other.... can somebody please help me out here.....

---

### Post by generic-coder on 2009-07-10
> **jonobr said:**
> Hello


Im not so sure about your subnetting,

Your using a /27 which should give a subnet range of
192.168.1.1 to 192.168.1.30 and a broadcast of 192.168.1.31

Your broadcast seems to be .255 Im not sure thats correct?

Im also wondering if you could not use classic IP without subnetting,
Ie using a regular /24 network?
I am very new to linux, i was trying out everything that could work hence inconsistency in my configurations... what is it supposed to be

---

### Post by jonobr on 2009-07-10
No problem, using subnetting makes things complicated, but using a class C range makes it so much easier.

The question now becomes, whats the question?

Are you not getting an IP address from the DHCP server?

---

### Post by generic-coder on 2009-07-10
> **jonobr said:**
> No problem, using subnetting makes things complicated, but using a class C range makes it so much easier.

The question now becomes, whats the question?

Are you not getting an IP address from the DHCP server?
yes i am, 192.168.1.28, subnet mask 255.255.255.0

---

### Post by jonobr on 2009-07-10
Super, you should be golden,
Hopefully your pinging around and all is ok,

I reckon you can increase your number of hosts, if you expect the need.

You can have 192.168.1.2 to 192.168.1.254

but you shouldn't have them all dhcp you should leave a whole lot empty in case you want to setup static addresses.

---

### Post by generic-coder on 2009-07-10
> **jonobr said:**
> Super, you should be golden,
Hopefully your pinging around and all is ok,

I reckon you can increase your number of hosts, if you expect the need.

You can have 192.168.1.2 to 192.168.1.254

but you shouldn't have them all dhcp you should leave a whole lot empty in case you want to setup static addresses.
My problem right now is that i am not able to ping either of them from anywhere.......

---

### Post by jonobr on 2009-07-10
Are these both ubuntu machines?

Whats the ip address of these machines?

Can you do an ifconfig on the terminal windows and post the results of the clients

---

### Post by generic-coder on 2009-07-10
One is ubuntu, the other is xp Here is the output for the ubuntu machine
```

eth0      Link encap:Ethernet  HWaddr 00:13:d4:5a:ec:03  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe5a:ec03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16530 (16.5 KB)  TX bytes:4068 (4.0 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:3f:df:c0:3b  
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fedf:c03b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3234547 (3.2 MB)  TX bytes:789078 (789.0 KB)
          Interrupt:16 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55253 (55.2 KB)  TX bytes:55253 (55.2 KB)


```

and then from the xp machine this is what i get when i do ipconfig

```

 DNS Suffix: Home
IP: 192.168.1.28
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.1

```

---

### Post by jonobr on 2009-07-10
On the ubuntu client I notice you have two ethernet interfaces,

I recommend for the time being, disconnect eth1 unless there is a major requirement for it.

Your ifconfig and windows setup look ok,

WHat happens when you do the following

on the ubuntu machine

ping 127.0.0.1
ping 192.168.1.10
ping 192.168.1.1
ping 192.168.1.28

ping 74.125.45.100

From the xp machine, the same type of drill 


ping 127.0.0.1
ping 192.168.1.28
ping 192.168.1.1
ping 192.168.1.10

ping 74.125.45.100

---

### Post by generic-coder on 2009-07-10
The ubuntu box responds ok to 127.0.0.1, 192.168.1.1 and 74.125.45.100
It says 192.168.1.28 is unreachable 

The xp box is happy with 127.0.0.1 & 192.168.1.28, it does not like the rest, it times out

---

### Post by generic-coder on 2009-07-10
The ubuntu box is also happy with 192.168.1.10

---

### Post by jonobr on 2009-07-10
Hello


I think you have an issue with your xp box

If you go to your ubuntu again and open a browser and put in
74.125.45.100

If that works 
then put in google.com , see if that works.

On your windows box, it sounds cable related.
Is the link led coming up?
Have you tried renewing

start->run->cmd
ipconfig /release
ipconfig /renew

Does that obtain an ip address?

---

### Post by jonobr on 2009-07-10
So just to explain

127.0.0.1 is its own local interface, it tests the ip stack without going onto the internet.

192.168.1.10
is the ip address it gets from the dhcp

the 192.168.1.1 is your router
and the 75 is google


Windows can ping its loopback address 127.0.0.1, its own interface but nothing on the general network.
If the cable was unplugged the wondows box would respond the same way.

Its billy gates, he has the problem.

---

### Post by generic-coder on 2009-07-10
yes it does obtain an ip address. Remember i stated that my xp connects through wireless not wire... i am dual booting xp and ubuntu on the laptop as well so, let me try to connect to the access point throgh ubuntu.... may be that will work.. but i doubt it

---

### Post by jonobr on 2009-07-10
Im not much help with wireless.
All the wireless I have used always works and have not had any need to learn a whole heap about it.

However, I will say, if your getting an IP, thats half the battle.

Im thinking if you check your wirelsss router it may show you something which may help.

Given your dhcp starts Im thinking you may need to open a new thread on doing wireless and having a problem with that.

---

### Post by generic-coder on 2009-07-10
> **jonobr said:**
> So just to explain

127.0.0.1 is its own local interface, it tests the ip stack without going onto the internet.

192.168.1.10
is the ip address it gets from the dhcp

the 192.168.1.1 is your router
and the 75 is google


Windows can ping its loopback address 127.0.0.1, its own interface but nothing on the general network.
If the cable was unplugged the wondows box would respond the same way.

Its billy gates, he has the problem.
192.168.1.10 is not the ip address assigned to the xp box. Its the address my dhcp server gives to the eth1 NIC which has the AP connected to it. The address assigned to the xp box is 192.168.1.28, its complicated i know.......................i am not very sure... but what i think is happening is that the AP is given the address 192.168.1.10 and some how given a range of address to give to all wireless clients ie 192.168.1.28 to some random range....

Of course i might be wrong and i welcome corrections,,.,

---

### Post by generic-coder on 2009-07-10
Its the same results from the ubuntu laptop. I get connected to the wireless provided by the AP, but i am not able to ping the dhcp server machine. is it possible that there might be some firewall rules blocking the communication.

---

### Post by jonobr on 2009-07-10
YEp 

Im a bit lost.


If you had a nw diagram it would help.

Or a top dopwn description of your network.

I.e. router is connected to this which is connected to that,.

---

### Post by generic-coder on 2009-07-10
Here is the diagram.

internet -----router ------ Ubuntu Desktop (Runs dhcp-server)-------AP----- Wireless Client     (Laptop running XP & Ubuntu)

I hope the diagram is clear. Essentially the dhcp-server there provides the AP with a static IP address ie 192.168.1.10 because that is the address being given to the NIC it is connected to.

---

### Post by jonobr on 2009-07-10
Yep

Given your setup I think you have two options when creating this kind of setup up.

You can setup the ubuntu server as a router where it knows how to route packets between interfaces,
This will require you to have 2 different networks and route between interfaces use bridge mode where it will bridge segments together in the one network.

If you go to synaptic and theres a package called bridge-utils which may sort your problem.
I have not used that before, but again, it may resolve your issues

---

