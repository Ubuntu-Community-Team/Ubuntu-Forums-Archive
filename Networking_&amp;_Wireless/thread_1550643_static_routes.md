---
title: "static routes"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by fdelval on 2010-08-11
Hello all, watch this setup


[IMG]http://img268.imageshack.us/img268/7132/dibujojza.jpg[/IMG]


i dont know if the setup is incorrect setting up 2 hosts in different subnets in the switch but the phone works with the 192.168.1.1 router and the pc connecting to the ubuntu server surfs the net through the 192.168.7.7 degault gw, so it doesnt conflict each other...

the question is, how can i add the 192.168.1.0 subnet to the ubuntu server routing tables so i can reach any host there???

---

### Post by fdelval on 2010-08-11
reuploaded picture

---

### Post by Iowan on 2010-08-11
I'd need to research - but **route add** sounds likely. 
**man route** might provide an answer faster than I can...

---

### Post by fdelval on 2010-08-12
> **Iowan said:**
> I'd need to research - but **route add** sounds likely. 
**man route** might provide an answer faster than I can...


i tryed:
[COLOR=#000000]route add -net 192.168.1.0 netmask 255.255.255.0 dev eth0

and 

[COLOR=#000000]route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.50.251 dev eth0[/COLOR]
[/COLOR]
Its a command like that which creates the entry in the table that i signaled with "?????"
neither of them worked

---

### Post by pat_bateman on 2010-08-12
Sorry but your diagram is not very clear.
I would route the 192.168.1.0 towards ubuntu eth2.
Maybe routes back on the hosts from 192.168.1.0 subnet are missing?

-Pat

---

### Post by fdelval on 2010-08-12
> **pat_bateman said:**
> Sorry but your diagram is not very clear.
I would route the 192.168.1.0 towards ubuntu eth2.
Maybe routes back on the hosts from 192.168.1.0 subnet are missing?

-Pat


mmm i dont know, but pings from ubuntu to the 192.168.1.0 ended with a "unreacheable" message


First of all, is it possible to combine devices in different subnetwoks in the same switch??

is there other setup more simple than this?

---

### Post by pat_bateman on 2010-08-12
> **fdelval said:**
> 
First of all, is it possible to combine devices in different subnetwoks in the same switch??

Depends on your switch.

> mmm i dont know, but pings from ubuntu to the 192.168.1.0 ended with a "unreacheable" message
well, maybe "ping request" can reach the device on 192.168.1.0 but then the device doesn't know how to reply to you because route back is missing.
So, on your local machine, you see that the network is unreachable because your local machine never get the "ping reply".

Why don't you want to have everything in the same subnet? what kind of network is it? home network?

-Pat

---

### Post by fdelval on 2010-08-12
> **pat_bateman said:**
> Depends on your switch.


well, maybe "ping request" can reach the device on 192.168.1.0 but then the device doesn't know how to reply to you because route back is missing.
So, on your local machine, you see that the network is unreachable because your local machine never get the "ping reply".

Why don't you want to have everything in the same subnet? what kind of network is it? home network?

-Pat

i have 4 adsl

2 with wan failover with 192.168.1.0

the other 2 with wal failover too with 192.168.50.0 .

The only link between both could be either a VPN, or... a switch with alltogheter...

---

### Post by jherasb on 2010-08-12
If you want  to connect to another network that is directly connected to the same interface, you can use an ethernet alias that have and ip in the network.

you can do this by using the virtual interface eth2:0 for example. 

with the command 
sudo ifconfig eth2:0 192.168.1.2 up 

you assigned this ip to yor ubuntu. The phone probably have internet through 192.168.1.1 not through you ubuntu, because you need that the default gateway be in the same network.

Jesus de las Heras

> **fdelval said:**
> reuploaded picture

---

### Post by fdelval on 2010-08-12
wow jherasb, your solution looks so promising!
i made a test in my home with a simple setup and worked, i will try it tomorrow
thank you a lot


just a question, this is so useful that.... what are static routes good for? i mean, adding an alias i get a new ip and also a new route i saw... why would i want to use only routes adding to the routing table a new net???

---

### Post by jherasb on 2010-08-14
You want to use static routes when you want reach a target through an specific gateway. 

For example: If you have 2 broadband connection, one cheap asimetric with only 256kbits for upload and 10mbps for download and a second connection with simetric 1mbps, probably you want that all the web traffic goes through the first connection and use the second for uploading files to your FTP.

Jesus de las Heras

> **fdelval said:**
> wow jherasb, your solution looks so promising!
i made a test in my home with a simple setup and worked, i will try it tomorrow
thank you a lot


just a question, this is so useful that.... what are static routes good for? i mean, adding an alias i get a new ip and also a new route i saw... why would i want to use only routes adding to the routing table a new net???

---

### Post by fdelval on 2010-08-14
Ok, problem now 

I heard iptables doesnt support ip aliases in an easy way, i didnt go further because i use shorewall and shorewall can handle well aliases, so i went for it

Somehow i read this:

> Sometimes multiple IP addresses are used because there are       multiple subnetworks configured on a LAN segment.** This technique does       not provide for any security between the subnetworks if the users of the       systems have administrative privileges because in that case, the users       can simply manipulate their system's routing table to bypass your       firewall/router. **Nevertheless, there are cases where you simply want to       consider the LAN segment itself as a zone and allow your firewall/router       to route between the two subnetworks.


[http://www.shorewall.net/Shorewall_and_Aliased_Interfaces.html](http://www.shorewall.net/Shorewall_and_Aliased_Interfaces.html)


Coming back to my example, i guess that the 192.168.1.1 device could add a route to 192.168.2.0 subnet and somewhat bypass all rules set in the 192.168.2 subnet to the firewall or to the net or the the other 192.168.1 subnet, right??
to sum up, instead of having as gw the .2.254 firewall address which is filtered, i would change it to the 1.254 and pass it

**i guess that is all the problem right?? can you confirm it?**

---

