---
title: "Configure internet network"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by ROBarber on 2009-06-24
Hello everybody.

I need some advices on configuring a LAN network consisting of two computers. First one is a HP ProLiant DL380 G3 with Ubuntu Intrepid installed on it (server version) and the other one is a Desktop computer with Vista Ultimate on it.

The HP is set up to run as a web server (LAMP), and it has 2 NIC's installed (Ethernet cards). I've configured it to work as a web server and made almost all configurations necessary to work properly and during this weekend I'll connect it to the Internet. The second computer I'll use it as a multimedia file storage with a connection (with Samba) to the HP server and to navigate on the Internet (through HP server or router).

I think I have to options for acquiring the goal I want: 

- first, to use a router and to create a local network for the 2 computers and to properly configure it for incoming HTTP requests to HP server;
- second, to connect the HP server directly to the Internet (I have a static IP) and using the other Ethernet card to make a connection with the Vista computer.

Any advice is welcome :).
Cristian

---

### Post by jhannah on 2009-06-24
It sounds like you have a few options here. I would recommend something like the below topology:

```

Modem
|
Switch ------------------> HP 1st NIC (Static IP from ISP, gateway from ISP)
|
Router (10.1.0.1/24) --> HP 2nd NIC (10.1.0.10/24) 
                             \--> Vista Box (10.1.0.11/24, gateway 10.1.0.1)

```

In this topology, the HP will send all traffic directly out to the Internet over it's first NIC and bypass the router all together. Traffic from the HP to 10.1.0.0/24 will of course still go out over the second NIC. The Vista machine will route it's traffic to 10.1.0.1, the IP for your router which can then route the traffic out to the internet.

If you wanted, you could also set the HP to use 10.1.0.1 as it's default gateway (omiting the gateway for your ISP as you should only have a single default gateway on any machine) and then it too will send all traffic through the router unless it receives it over the 2nd NIC but that might create an asyncronous path for some traffic.

Does that make sense and address what you are looking to accomplish?

---

### Post by ROBarber on 2009-06-25
Hello jhannah.

I've been searching for some information and I've found that there is a possibility to use the HP server as a gateway for the Vista machine' private network, and not to use the router.
One HP's NIC will be connected directly to the Internet and the other will be used to create a private network with the Vista machine (and maybe with a switch to add more computers to network). In this case I will have a connection for the two machines for file transfer, and enabling ip_forward on HP machine I can have access to the Internet for the Vista machine through the second NIC. I will not have a modem device in my location, it will be a fiber link cable.

I am thinking more like the following topology:

```

Cable
|
HP 1st NIC (Static IP from ISP, gateway from ISP)
ip_forward = 1
HP 2nd NIC (10.1.0.1/24)
  /--> (switch) ---> Vista Box (10.1.0.10/24, gateway 10.1.0.1)
```

In this case the router will not be necessary having the possibility to use HP machine as a gateway/router.

Because the HP machine will be always on (working as a web server) I think is a good option to use it as a gateway for the other computer(s) on the private network to connect it(them) to the internet. I also have to take into consideration the possibility to add a few other machines on the private network. 

At this moment I have a cable, One HP machine with 2 NICs, one Vista box and a routing device. I want to make it easy to maintain, and to configure for further modification because somebody else will take care of it and does not have good technical knowledge to take these actions.

Thank you for your reply :).
Cristian

UPDATE:

It seems that the HP server will be behind the router. The guy who has it told me that in his area are a lot of electrical storms, so it will be an extra protection using the wireless router (D-Link DI-524).

---

### Post by ROBarber on 2009-07-05
Update.

After a couple of unexpected issues with my connection to the ISP and with the router everything works fine.
Even the guy from the ISP company told us when he installed the wire that the connection is not configured to take care of computer's MAC address, after I spent more that 4 hours doing nothing, he called to tell us that in a couple of minutes he will change the MAC configuration so we will be able to use the Ubuntu server :lolflag: to connect to the Internet. I hope he didn't get injured accidentally :D .

In the meantime I've remove Network Manager and installed wicd. Looks to be more stable. I use Firestarter as firewall and to take care of sharing Internet Connection. 
If I connect the Vista computer directly to Ubuntu gateway, using a wire, the connection is up, but if I use the router the Vista machine is not able to reach the Internet. 

I'm using the following configuration:

```
Ubuntu gateway: address 10.1.1.1 (second NIC static IP) netmask 255.255.255.0

Vista Machine: address 10.1.1.2, netmask 255.255.255.0 gateway 10.1.1.1, 
primary DNS 10.1.1.1 secondary DNS 0.0.0.0
```

With this configuration everything works fine.

If I use the router I have the following configuration:

```
Ubuntu gateway: address 10.1.1.1 (second NIC static IP) netmask 255.255.255.0

D-Link Router: address 10.1.1.2, netmask 255.255.255.0 gateway 10.1.1.1, 
primary DNS 10.1.1.1 secondary DNS 0.0.0.0
``` 

and with DHCP enabled to give network address to the machines in the LAN, starting from address 10.1.1.4. But no connection to the Internet. In a couple of days I'll test the router on another network to see if it is working or not. It is really a pain in my @$$, an I don't know what to do to make it work.

---

