---
title: "Internet sharing to 2 subnets"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by david.ptm56 on 2009-07-18
Hello everyone. I really hate to start in this community asking instead of helping but I'm desperate now. I hope you can help me to figure out what am I doing wrong.

I'm running an undervolted and underclocked AMD X2 5050 as everyday internet browsing and music player computer, aswell as file and printer server and internet routing. OS is Ubuntu Linux 9.04 Server edition, Kernel Linux 2.6.28-13-generic on x86_64. There's 3 ethernet devices in this computer, eth0, eth1 and eth2. Eth0 is wired directly to my cable-modem, and gets its IP dynamically. Eth1 is connected to a 4 port router I had lying around and Eth2 is connected to a wireless acces point. The layout is like this:

[IMG]http://i101.photobucket.com/albums/m70/ptm56/para%20foros%20y%20tal/netscheme1.jpg[/IMG]


Now, this is the content of my**  /etc/network**  file:


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
    post-up iptables-restore < /etc/iptables.up.rules

auto eth1
iface eth1 inet static
        address 192.168.2.20
        netmask 255.255.255.0
        broadcast 192.168.2.255
        network 192.168.2.0

auto eth2
iface eth2 inet static
        address 192.168.2.3
        netmask 255.255.255.240
        broadcast 192.168.2.15
        network 192.168.2.0
```**sysctl.conf** (just a part):

```
##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
net.ipv6.conf.all.forwarding=1
```and **rc.local**
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sysctl -w net.ipv4.ip_forward=1
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE
exit 0
```At this point I was able to connect to internet from the wireless subnet with any laptop, but not from the wired subnet. Last night, following this Howto:  [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html) I managedto fix this with **Webmin**. Screenshots:

[IMG]http://i101.photobucket.com/albums/m70/ptm56/para%20foros%20y%20tal/webmin0.jpg[/IMG]
[IMG]http://i101.photobucket.com/albums/m70/ptm56/para%20foros%20y%20tal/webmin0.jpg[/IMG]
[IMG]http://i101.photobucket.com/albums/m70/ptm56/para%20foros%20y%20tal/webmin2.jpg[/IMG]

Everything was working fine in both subnets until I've rebooted the server/router thirs morning. Everything looks exactly the same in the configuration but nothing's working well.



[SIZE=3]**Things I can do now:**[/SIZE]
[B]
 * From Wireless subnet[/B]
___Wiht my laptop (IP 192.168.2.9, netmask 255.255.255.240, gw 192.168.2.3)** I can ping the Access Point** [192.168.2.2/28]
___Wiht my laptop (IP 192.168.2.9, netmask 255.255.255.240, gw 192.168.2.3) **I can ping device eth2 **[192.168.2.3/28]
___Wiht my laptop (IP 192.168.2.9, netmask 255.255.255.240, gw 192.168.2.3)** I can ping device eth1 **[192.168.2.20/24]

*** Fron wired subnet**
___From my sisters computer (IP 192.168.2.21, netmask 255.255.255.0, gw 192.168.2.20) **I can ping the stand-alone router** [192.168.2.1/24]
[B]
* From the server itself[/B]
___**I can ping eth1** [192.168.2.20/24],** eth2** [192.168.2.3/28]**, the wireless access point ** [192.168.2.2/28] and** computers connected to the wifi subnet **[192.168.2.9/28]
___I have** connection to Internet**




[SIZE=3]**Things I can not do now:**[/SIZE]

 *** From Wireless subnet**
___Wiht my laptop (IP 192.168.2.9, netmask 255.255.255.240, gw 192.168.2.3) **I can't ping the stand-alone router** [192.168.2.1/24]
___Wiht my laptop (IP 192.168.2.9, netmask 255.255.255.240, gw 192.168.2.3)** I can't ping a computer connected to the wired subnet** [192.168.2.21/24]
___**I don't have connection to Internet**

*** Fron wired subnet**
___From my sisters computer (IP 192.168.2.21, netmask 255.255.255.0, gw 192.168.2.20) **I can't ping device eth1** [192.168.2.20/24]
___From my sisters computer (IP 192.168.2.21, netmask 255.255.255.0, gw 192.168.2.20) **I can't ping device eth2** [192.168.2.3/28]
___From my sisters computer (IP 192.168.2.21, netmask 255.255.255.0, gw 192.168.2.20)** I can't ping the wireless acces point** [192.168.2.2/28]
___**I don't have connection to Internet**
[B]
* From the server itself[/B]
___**I can't ping the stand-alone router **[192.168.2.1/24]:
```
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.3 icmp_seq=1 Destination Host Unreachable
```__**_I can't ping a computer connected to the wired subnet** [192.168.2.21/24]:
```
PING 192.168.2.21 (192.168.2.21) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
```
I think that's all the information I have at this moment. I never thought it was gonna be so painful to get this thing working. I hope you can help me getting this machine working ASAP. If you need any more info just ask for it. Appreciate your help.

Cheers.

---

### Post by jonobr on 2009-07-19
Not sure if I can help here, and wow, thats an amazing amount of detail, however, I have one really stupid question for you.

You have a network card 1 and 2 and the first is standard class C and the second one is subnetted,

Why dont you keep that a regular class C also, just a different subnet?

The reason why I say that is if you look at the eth outputs,

you see ( and this is a wag)

you have two networks on two different interfaces down as 
 network 192.168.2.0

addtional  I notice in your routes, you also have two entries ,

one shows that to get to to the .2.0 network, go to the eth1 interface,

and for the .2.0 network, go to the eth2 interface.

---

### Post by spynappels on 2009-07-19
Hi,
I also have a stupid question or two.  Is the Wireless access point also a router and dhcp server or simply a WAP?

Is there a specific reason you want to separate the two sections of the network, Wired and Wireless?

It is just that with the current set up and IP addresses, your system is much more complex than it needs to be if all you want to do is share the Internet connection with all the computers. If you had a good reason for keeping them all separate, that changes matters a little, but then I would suggest different subnets such as 192.168.2.x for wired and 192.168.3.x for the wireless.

---

### Post by david.ptm56 on 2009-07-19
Thank you very much.

I know this is not an optimal solution. I'm doin' it this way just for the sake of it, I wanted to experiment a little. For the record **ALMOST** everything's currently working now. This is what I did:



**1.- I changed the topology to something not as "strange"**

 |-- **eth0 - Internet** [IP by DHCP]
 |                                                               
|
 |-- **eth1 - [192.168.1.1]** - Router [192.168.1.2] / DHCP Server - . . . . . . . - wired devices
| (Router DHCP server configured to provide IPs in range 192.168.1.3 - 192.168.1.254 and gateway 192.168.1.1)
|
|
|-- **eth2 - [192.168.2.1]** - WAP [192.168.2.2] / DHCP Server - . . . . . . . . . - wireless devices
  (WAP DHCP server configured to provide IPs in range 192.168.2.3 - 192.168.2.14 and gateway 192.168.2.1)





**2.- Rebuilt the routing tables to this**

```
david@servidor-david:~$ route
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.2.0     *               255.255.255.240 U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
84.127.80.0     *               255.255.240.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         84.127.80.1.dyn 0.0.0.0         UG    100    0        0 eth0

```[B]



3.- Took off the postrouting masquerade thing [/B](not sure of what this does anyway)

The whole scenario looked "prettier" now but still not working. Here comes the weird part:


**4.- Edited sysctl.conf again**

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
# net.ipv4.conf.default.forwarding=1

```**IT WORKS!!** Now I have connection to internet from both the wired net and the wireless one. **unfortunately not everything's working correctly** at this stage.

[SIZE=3]**I can**[/SIZE] ping from the server to the WAP and to the laptops connected to the WAP, and the other way around, I can ping from a wireless device to the WAP and to the different server net devices and services. OK.

[SIZE=3]**I cannot**[/SIZE] ping the router or the computers connected to it from the server:
```
david@servidor-david:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

``````
david@servidor-david:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

```From the other, side, I mean, from a computer connected to the router, [ie.: 192.168.1.3] I can ping the router [192.168.1.2] but not the gateway [192.168.1.1] but still I can browse internet. It sounds very strange to me. I suppose it's the router dropping the ICMP packets of ping requests coming from non-DHCP-assigned IPs. Anyone has an idea for solving this issue (an idea that doesn't involve buying a switch or changing the topology, of course).
EDIT: Uhm... another thing that isn't working now is apt-get, which tries to connect to repositories through 192.168.2.3. I don't know how to change this behavior. This is affecting gDesklets that need internet connection too, like weather forecast.

Thank you very much, everyone.


Cheers.

---

### Post by varun1786 on 2009-07-20
Your network setup does n seem right. The two interfaces of the router and the network seem to been on the same subnet in (1) and (2) i've marked them below. This usually leads to a lot of confusion and never works perfectly.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121731&stc=1&d=1248074813[/IMG]

I've drawn up a different network setup for you this should work perfectly.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121732&stc=1&d=1248074813[/IMG]

Make sure u configure the interfaces on the comp and the inside interface of the router in the same subnet and the outside interface of the router on a different subnet.Let me know how it works

---

### Post by varun1786 on 2009-07-20
**1.- I changed the topology to something not as "strange"**

 |-- eth0 - Internet [IP by DHCP]
 |                                                               
|
 |-- eth1 - [192.168.1.1] - Router [192.168.1.2] with a*** subnet of 255.255.255.252 ***


 DHCP Server - . . . . . . . - wired devices
| (Router DHCP server configured to provide IPs in range 192.168.1.***4*** - 192.168.1.254 with ***subnet 255.255.255.0*** and gateway 192.168.1.1)
|
|
|-- eth2 - [192.168.2.1] - WAP [192.168.2.2] with a [I][B] subnet of 255.255.255.252 

[/B][/I]/ DHCP Server - . . . . . . . . . - wireless devices
  (WAP DHCP server configured to provide IPs in range 192.168.2.4 - 192.168.2.***16*** with ***subnet 255.255.255.240*** and gateway 192.168.2.1)

Make sure the e0 dhcp ip is also not in the 192.168.1 or .2 subnet

---

### Post by spynappels on 2009-07-20
> **varun1786 said:**
> Make sure the e0 dhcp ip is also not in the 192.168.1 or .2 subnet

It won't be as the ISP will not give an IP in the 192.168.x.x range, this interface should have his ISP supplied global IP.

---

### Post by joebeasley on 2009-07-20
"Operation not permitted" messages are coming from iptables.  Check your firewall settings.

---

### Post by david.ptm56 on 2009-07-20
> **joebeasley said:**
> "Operation not permitted" messages are coming from iptables.  Check your firewall settings.

That was the problem! I was sure it was something minor. I had something wrong with my firewall settings, don't know exactly what because I directly changed the rule for eth1 incoming packages. Everything's working now. Thank you very much everyone.

OTOH, varun1786, why are you suggesting to use a 30bits netmask for the server ethernet cards and router/WAP while using another for the devices connected to its subnet? Is it for security reasons? I found it interesting, but I don't know if it could make things difficult when sharing resources like FTP and printer server.

I'm using a 28b netmask for the wireless net [192.168.2.0] to limit the amount of devices accesing the net, and since the wired net won't use more than a 4 port router by now I could use a 29b netmask for 192.168.1.0, but unfortunately, my router is a piece of c*#! and only accepts 255.255.255.0. I was under the impression that all the subnet needed to use the same netmask for things to work correctly, but the varun1786 advice  got me thinking that I might be wrong.

Once again thank you all. This community's great, isn't it?

Cheers.

---

### Post by varun1786 on 2009-07-20
when u connect two eth devices all you need is 2 ip's. we use a 30 subnet mask in such situations cas it gives u only 2 ip. this addressing scheme is used more for conserving ip's than security.

It does not make things difficult when sharing resources like FTP and printer server. A network with this type of addressing is called VLSM(variable length subnet mask). It is widly supported and as long as u have a dynamic routing protocol like RIPv2 or eigrp running on the router u should have no problems at all.

---

