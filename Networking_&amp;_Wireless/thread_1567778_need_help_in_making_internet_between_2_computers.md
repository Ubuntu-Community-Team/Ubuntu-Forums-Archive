---
title: "need help in making internet between 2 computers"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by snake444 on 2010-09-04
Hi, i have two computer
first one is the main computer, he is connected to the internet throught DSL
ubuntu 10.10 beta installed

the second is ubuntu 9.10, and i want this computer to connect to the internet of the first computer

they both connected to a B-FOCUS router 270pr but i dont want to make the router to be the one that connects to the internet
i want the first computer will connect to the internet and the second will be accessing the internet of the first computer connection.

how can i do it?

---

### Post by BkkBonanza on 2010-09-04
If your router is doing DHCP then you need to tell it to treat computer1 as the gateway. It will give out that IP as the gateway for other machines in the LAN.

Computer1 will have two interfaces, right? One for the LAN and one going to the DSL modem. On computer1 you will need to add some routing and iptables rules to configure it to be the gateway, and to route packets through to it's DSL connection.

In effect you are splitting the router functionality between the router and computer1. Of course, the router could be replaced by a switch and you could just configure computer1 to be the router alone.

The exact rules you need depend on the details of your system.

---

### Post by jroa on 2010-09-04
Is there a particular reason why you do not want the router to handle both connections?

---

### Post by snake444 on 2010-09-23
BkkBonanza can you explain how to do this? im not so good with networking and i dont understood how to do it

jroa - the router has bug and because of this i need to do it to act like modem

the thing that im trying to do is this:
[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)
this is how i had it on windows

now both computers have ubuntu 10.10
so can anyone help please??

---

### Post by mosquetero on 2010-09-23
Hi snake444!

I had the problem you are having some time ago. What I did was install a proxy in computer 1. Computer 2 should redirect all its internet traffic to that proxy. I used a proxy called squid which worked perfectly.

---

### Post by BkkBonanza on 2010-09-23
You could use a proxy but that's not really the right way to do this. It works for HTTP but if you need to use other software like email etc. then you need to configure computer 1 as your gateway.

It's not hard. Computer 2 needs to be set to use computer 1 as the gateway. That can either happen via DHCP, if you are using dynamic IPs or you can just give it static settings. If you only have the two systems then static method is probably easiest.

As an example static cfg using typical IPs you might have settings like this on computer 2, in the /etc/network/interfaces file,

```
auto eth0
iface eth0 inet static
    address 192.168.1.5
    netmask 255.255.255.0
    gateway 192.168.1.1
```

Over on computer 1 you want to assign it the gateway IP, enable forwarding and add a NAT rule in iptables. I think that will be enough probably. The DSL interface should be set to whatever you have working now. Again, the /etc/network/interfaces file,

```
#The DSL interface
auto eth0
iface eth0 inet dhcp

# The LAN interface
auto eth1
iface eth1 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
```

Then a small script to setup the forwarding that runs when the interfaces are brought up (this is a partial copy of mine - if you want a bit more firewall smarts I can post a more advanced version, but this is good just to see if it works, adjust to suit according to your desired IPs).
In /etc/network/if-up.d/gateway file,

```
#!/bin/bash

if [ "$IFACE" != eth0 ] || [ "$MODE" != start ]; then
  exit 0
fi

WANIF=eth0
LANIF=eth1
WANIP="`ifconfig $WANIF | awk '/inet/ {print $2}' | sed 's/addr://'`"
LANIP="`ifconfig $LANIF | awk '/inet/ {print $2}' | sed 's/addr://'`"
LAN="192.168.1.0/24"

echo 1 > /proc/sys/net/ipv4/ip_forward

/sbin/iptables-restore <<-EOF;

*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

-A FORWARD -i $WANIF -o $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i $LANIF -o $WANIF -j ACCEPT
COMMIT

*nat 
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

-A POSTROUTING -o $WANIF -j SNAT --to $WANIP

COMMIT
EOF
```

In my case I found using dnsmasq on the gateway for both DHCP and DNS was the simplest way to go but you could make use of the current router, or statically set DNS servers in each machine's /etc/resolv.conf. It kind of depends on how many systems you have and what options your router gives you in that area. dnsmasq is a package in the Ubuntu repos, so is a pretty easy install. Just a few settings and it works.

---

### Post by skywatcher on 2010-10-13
Hi all

I had a look at some of these posts and I find it somewhat bewildering! :)

A question: can I set up a network between two computers by simply connecting them with a network cable without additional hardware?

I have two laptop computers, one with Ubuntu 9.10 and the other with Ubuntu 10.04. The 9.10 laptop is connected to all my resources, i.e., printer, wireless 3G modem etc. I'd like to share these with the 10.04 laptop. Is this possible?

---

### Post by BkkBonanza on 2010-10-13
Yes. With most laptops now a regular cable will work because they can auto-detect the cable type. Older network adapters may require a crossover cable. This is a special cable (you can buy at any computer shop) that has the Tx and Rx lines cross-over for direct connections like this.

If you plug in the cable and can ping the IP of the other mahcine then it works. Of course, you would need to set the IP of each machine manually this way as there is no DHCP server to do it for you. As an initial test you can bring up an interface with the ifconfig command, eg.

sudo ifconfig eth0 192.168.1.1
(change IP for other machine)

Beyond that, for sharing your modem you would need some more config to handle forwarding and NAT routing. For printer sharing you can use CUPS, which no doubt has a tutorial written on the Ubuntu help site somewhere...

---

### Post by skywatcher on 2010-10-13
Thanks for the useful information. I'll give it a try.

---

### Post by skywatcher on 2010-10-15
Hi BkkBonanza

I have got as far as connecting the two laptops together, giving each a unique IP address, i.e. 192.168.1.1 and 192.168.1.2, and successfully pinged.

Please could you give me a few pointers as to how I must proceed from here? Let's start with something simple such as file sharing. I can graduate to configuring the modem and printer later.

Many thanks.

---

### Post by BkkBonanza on 2010-10-15
The easiest way is to go to menu item System, Preferences, Startup Programs and enable "Personal File Sharing". The more full way is to install package "Samba".

---

### Post by inobe on 2010-10-15
the easiest way possible even my son at twelve years old can do it.

if your pc has dual lan set the secondary lan to shared in network properties.

[IMG]http://aslakjohansen.files.wordpress.com/2009/10/screenshot-editing-share-connection.png?w=379&h=503[/IMG]

make sure that the secondary onboard lan is wired to the wan port on your router.

connect second pc to port one.

power router.

done

side note, i am using this setup rite now, it lacks file and printer sharing functions but the second pc gets internet.

this information is for the topic starter or anyone else that wishes to use ics "internet connection sharing"

---

### Post by inobe on 2010-10-16
> **snake444 said:**
> BkkBonanza can you explain how to do this? im not so good with networking and i dont understood how to do it

jroa - the router has bug and because of this i need to do it to act like modem


if you have a motoralla dsl modem like this one

[IMG]http://ecx.images-amazon.com/images/I/31Qoux06pYL._SL500_AA300_.jpg[/IMG]


you will need to change the routers default gateway to 192.168.**2**.1

now reboot modem and leave router powered down till the modem is fully lit, now start router.

---

