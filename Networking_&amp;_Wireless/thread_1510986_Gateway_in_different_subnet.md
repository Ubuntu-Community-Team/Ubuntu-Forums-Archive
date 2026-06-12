---
title: "Gateway in different subnet"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by Macsloverd on 2010-06-16
Recently I've got a commercial adsl connection (which means I have 8 static ip address), however I cannot get it work on either Ubuntu or Debian.

addresses 123.234.214.216
netmask 255.255.255.248
network 123.234.214.216
broadcast 123.234.214.223
gateway 123.234.214.217

the gateway ip is supposed to be the ADSL modem ip but it is not, it doesn't work. But I tried on the other windows box with dhcp, it works, only the gateway changed into 67.27.4.75 and the dhcp server is 192.168.1.254 (which is the internal ip of the modem) :confused:. The thing is that it works perfectly! And when I use DHCP in Ubuntu LiveCD with desktop environment it works as well. To be clearer in viewing:

addresses 123.234.214.216
netmask 255.255.255.248
gateway 67.27.4.75
dhcp server 192.168.1.254

Installing debian with DHCP, it doesn't work, manually type in the numbers it doesn't even allow me to do that because it gateway starts with 67 is in a different subnet!

Installing ubuntu with ignoring the dhcp configuration and manually modify the /etc/network/interfaces without gateway, there is no out going (no internet, no ping to any host) only incoming (I can use ssh to remove operate) since the ip is correct but the gateway is not.

Anyone has any idea how to solve this? Any idea will be appreciate.

------------------------------------------------------------------------------------------------------------------------------------


Problem Solved!
By taking a great help from everyone who concerned this problem and especially from bab1, this problem is solved and here I sum it up.

Firstly, gateway is not in the same subnet or totally different from the subnet of the IP address **is possible**. I tried to research for help in different places and 30% of people who answered with "It's impossible", and this recognition of network is incorrect.

After a lot of researching, Bab1 provide me a "hack" which is a SysV init style script originally from [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384271"). Unfortunately it is not applicable with Lucid. I read the script and used the command manually to add the gateway address as a host address and then make this address as a gateway. "What the user did was add a route from his computer to the default gateway router and then declared it the default gateway." quoted from bab1.

the command that I used:

```
route add -host x.x.x.x dev eth0
      route add default dev eth0 gw x.x.x.x
```

* x.x.x.x is the gateway address

with this, I think a shell script with these commands will be better since this shell script can be used with rc at init.d.

---

### Post by Macsloverd on 2010-06-16
anyone?

---

### Post by bigmojo74 on 2010-06-16
Before I start guessing can you clarify your network setup abit?

> addresses 123.234.214.216
netmask 255.255.255.248
network 123.234.214.216
broadcast 123.234.214.223
gateway 123.234.214.217

Is this from your router?
> 
addresses 123.234.214.216
netmask 255.255.255.248
gateway 67.27.4.75
dhcp server 192.168.1.254

What is this from?? Also when you use DHCP what is the IP/mask/etc that is getting leased to the client?

At first glance I can tell you that if the modem is routing - and given that it has an internal IP, I'd say it is - that you can't use the external/public IPs on internal machines but you could use NAT on the modem (if it supports it) to forward requests to the public IPs to the appropriate internal IPs.

---

### Post by bigmojo74 on 2010-06-16
I think I maybe misreading something here along the way - but you say you can remote into it from the outside but not get out with it? If it can be reached from outside it's routing out properly... do you have some sort of firewall in place on the local box that might be blocking traffic? i.e. If you deny ICMP or HTTP to the box the web and pings will fail.

---

### Post by jonobr on 2010-06-17
Hello

I got to working out your subnetting as in all these questions they are invariably wrong and lead to the problem, however, your Kung Fu is strong!!

I just want to get my head around what your saying.

It sounds as if your DHCP is doing internal 192.168 assigning then your just doing a typical home network NAT, where the devices are getting an internal IP and natting through your adsl device. Is that correct?

If thats the case then I figure that should work.

Im trying to visualize your setup.
Im thinking you have some device between the ADSL connection and the devices, is that just a switch or doing something fancy?

IT sounds almost as if you should have an "internal" or LAN IP address of the 123.234.214.217.
All devices on you LAN side should have that as their gateway, and then the device will route from there to the external WAN address space of 67.27.4.75

Bad form on the part of the ISP not helping you more with this?

---

### Post by Macsloverd on 2010-06-19
Thank you for all your help.

Here I put one of the computer which is able to get the IP address from DHCP

(some of them are fake for security)
addresses 123.234.214.221
netmask 255.255.255.248
gateway 67.27.4.75
dhcp server 192.168.1.254
dns1 192.168.1.254
dns2 213.75.63.36
dns3 213.75.63.70
bcast 123.234.214.223
network 123.234.214.216

(I have 8 ip addresses start from 216 to 223)

these ips can be got when:
using windows 7
using ubuntu live CD to install and works after the installation
installing asterisknow, trixbox, switchvox and afterwards

and these ips cannot be got when:
installing Debian (text install)
installing ubuntu server (means that without Live CD, just text install)

And together I use route command to check out the routings after the Ubuntu live CD install, here are the info

Destination      gateway   netmask          flags metric ref  use iface
-----------------------------------------------------------------------
62.12.4.75       0.0.0.0   255.255.255.255  UH     0      0    0   eth0
123.234.214.216  0.0.0.0   255.255.255.248  U      1      0    0   eth0
169.254.0.0      0.0.0.0   255.255.0.0      U      1000   0    0   eth0
0.0.0.0        62.12.4.75  0.0.0.0          UG     0      0    0   eth0

is there any way to use the ip route command to manually add above routes to the route table and make it work?

And for what it is worth, I think my DSL modem (router) is more like working in bridging mode but still can be visited through web using 192.168.1.254, but what is the public IP of the router?I have no idea, I tried to connect only one computer and ping every of the 8 ip I have got, nothing but this computer, so probably the modem is using ip in the 62 range like the gateway. The model of th modem is Thomeson 789vn
with a custom firmware from Dutch KPN.

For the network structure, DSL--->modem(router)--->computer, no firewall, no additional router.

---

### Post by Macsloverd on 2010-06-19
oh~~ I forgot to use the CODE mark, here the route info again:

```
Destination      gateway   netmask          flags metric ref  use iface
-----------------------------------------------------------------------
62.12.4.75       0.0.0.0   255.255.255.255  UH     0      0    0   eth0
123.234.214.216  0.0.0.0   255.255.255.248  U      1      0    0   eth0
169.254.0.0      0.0.0.0   255.255.0.0      U      1000   0    0   eth0
0.0.0.0        62.12.4.75  0.0.0.0          UG     0      0    0   eth0
```

---

### Post by tad1073 on 2010-06-19
your subnet for 123.234.216.216 is incorrect. the .248 only allows 4 usable address. try .240 which allows for 13 usable addresses

---

### Post by Macsloverd on 2010-06-19
I have thought about this before, however, I tried with BitTorrent IP check, I can use bittorrent without any problem as it was saying that IP=public. Actually, I don't quite care about what IP i am using, I just want install ubuntu server using DHCP, or install ubuntu server with no configuration and configure the network afterwards. I cannot do this because using the gateway which starts with 62 is not possible as it is in different subnet, and configure network after the install, I can't do that because I have no idea how to use the route command properly. :confused:

> **jonobr said:**
> Hello

I got to working out your subnetting as in all these questions they are invariably wrong and lead to the problem, however, your Kung Fu is strong!!

I just want to get my head around what your saying.

It sounds as if your DHCP is doing internal 192.168 assigning then your just doing a typical home network NAT, where the devices are getting an internal IP and natting through your adsl device. Is that correct?

If thats the case then I figure that should work.

Im trying to visualize your setup.
Im thinking you have some device between the ADSL connection and the devices, is that just a switch or doing something fancy?

IT sounds almost as if you should have an "internal" or LAN IP address of the 123.234.214.217.
All devices on you LAN side should have that as their gateway, and then the device will route from there to the external WAN address space of 67.27.4.75

Bad form on the part of the ISP not helping you more with this?

---

### Post by Macsloverd on 2010-06-19
I have 8 ip addresses start from x.x.x.216 to x.x.x.223 and 6 are usable.

This netmask is given by the ISP and besides, 256-8=248, so I think it is correct.

> **tad1073 said:**
> your subnet for 123.234.216.216 is incorrect. the .248 only allows 4 usable address. try .240 which allows for 13 usable addresses

---

### Post by tad1073 on 2010-06-19
[http://www.subnet-calculator.com/](http://www.subnet-calculator.com/)

---

### Post by JKyleOKC on 2010-06-19
I have a somewhat similar setup with multiple static addresses and they work just fine. However the gateway address that my ISP provided was 5 higher than the first usable address, not just 1 more as you showed in the first post of this thread. Specifically, here's my working setup:

```
LAN: x.x.x.32/29
Primary: x.x.x.33
Gateway: x.x.x.38
Netmask: 255.255.255.248
DNS 1: 151.164.23.201
DNS 2: 151.164.1.7
DNS 3: 151.164.1.8
```The "/29" on the LAN entry indicates 8 addresses but only 5 of them are usable. "32" refers to the entire subnet as a group, and "39" is the broadcast address for the subnet, while "38" is my gateway. The first two of these (network and broadcast) are standard conventions throughout the Internet; the gateway address can be set by the ISP but should always be outside the range of usable addresses so I would expect it to be just below "broadcast" as is mine.

If you convert these address numbers to binary and look at just the lowest three bits you will see that "network" is "0," "gateway" is "6," and "broadcast" is "7." The usable addresses are always 1 through 5, with 1 being the primary.

Hope this helps!

---

### Post by jonobr on 2010-06-19
The resident network is (in the last octet) 
.216
the valid usable addresses are .217 to .222
the broadcast address is .223 ,
so anything in that subnet is ok.

The 123 at the start is incorrect, but Im guessing you modified and is in the Class B range, but Im guessing you changed that so as to hide your real IP addresses.

All that being said, I still thing your subnetting is correct
or maybe I need a red bull

---

### Post by JKyleOKC on 2010-06-19
Try the .222 address for the gateway and see if it doesn't work properly. You absolutely MUST use the address on which your ISP's router is listening, for the gateway to work, and I've never before heard of having a gateway address configured in the middle of the usable range...

---

### Post by redmk2 on 2010-06-19
> **JKyleOKC said:**
> Try the .222 address for the gateway and see if it doesn't work properly. You absolutely MUST use the address on which your ISP's router is listening, for the gateway to work, and I've never before heard of having a gateway address configured in the middle of the usable range...

This doesn't sound right at all.  You don't "try an address".  The gateway is the LAN side interface IP address of the router (gateway device).  This can be any legitimate address in that LAN network.  The user can assign any IP address in that range to that interface on the gateway device (router/modem/whatever).

Typically this is controlled by the users router, but not always.  If the LAN is controlled by the ISP it can have many subnets in a larger network.

The gateway is really the IP address (interface that you send all traffic that is not LAN based (e.g. needs to be routed to the WAN)

It must be logical though.  The OP first mentions a 67.x.x.x address for a gateway.  This leads me to believe that he has located the WAN side IP address.  This is not the gateway.  The other interface on the device appears to be configured for a private network IP range (192.168.what.ever).  This can be changed to the IP range the ISP has assigned to the user.  One of users addresses should be the router/modem/gateway interface on the LAN side.  The gateway in this instance is the users device and his/her responsibility.   It therefore uses one of the users IP addresses.

---

### Post by JKyleOKC on 2010-06-20
> **redmk2 said:**
> This doesn't sound right at all.  You don't "try an address".  The gateway is the LAN side interface IP address of the router (gateway device).  This can be any legitimate address in that LAN network.  The user can assign any IP address in that range to that interface on the gateway device (router/modem/whatever).

 ...  

The gateway in this instance is the users device and his/her responsibility.   It therefore uses one of the users IP addresses.We're using the word "gateway" with two different meanings. When using multiple static addresses provided by the ISP, the ISP will assign a gateway address that the ISP's router will be listening on. That's the gateway that I've been describing. The user is NOT free to just pick one of the static addresses at random and use it; the ISP should specify the address to use but apparently failed to do so in this case. That's why I suggested to "try" the usual address that ISPs supply.

The other meaning, which you appear to be using, is the address on each client box that it uses to get out to the outside world. If there's a user's router, or if the modem is doing NAT, then the router or modem's LAN-side address would be what to use as this gateway. In this case only one of the static IPs from the ISP would be recognized and the rest would be wasted. Most home-level routers are unable to handle multiple IPs on the WAN side, although AT&T does make available a unit that can (but with a mandatory $250 installation fee).

In my setup, I have one Xubuntu box configured to do my routing. It has two network cards. Eth0 serves the LAN and is connected to a switch; it has a local address of 192.168.0.2, and all other boxes on the LAN have this set as their gateway address for routing. Eth1 connects to the Internet, has an address of x.x.x.33, and uses x.x.x.38 as its gateway address. The kernel takes care of routing LAN traffic to the Internet by switching between the interfaces as necessary.

To make full use of my multiple static IPs, I have my DSL modem connected to a hub, and one line from that hub feeds eth1 on the Xubuntu router box. A second line connects to my wife's WinXP machine (that refuses to connect to my Linux-based LAN) and it has the address x.x.x.34, which is another of my 5 statics. Finally, a third line from the hub feeds a Linksys router with wireless capability at x.x.x.35, which lets my laptop and those of visiting family members connect to the Internet but not to my LAN. The other two IPs are presently unused; I had to buy five in order to get even one. It's all somewhat of a kluge but it does what I need.

---

### Post by Macsloverd on 2010-06-20
Thanks for all of your help, I really learnt a lot from you guys.

The things is that the ISP did send me a letter said that the 216 adn 223 is not usable and the 217 is the gateway, but hey, the 217 is DHCPly assigned to one of my Asterisk Box! So it is absolutely NOT the gateway, and in one of my other office, the same network is applied, and the gateway is also 62.12.4.75, but the letter said something else. Most amazing part is that these are all automatically assigned, if I put up something according to the ISP, it won't work, I don't even have internet connection.

I can't call them because the people who works in the helpdesk, they know even less then I do (How can they can the job, I am always wondering).

So, here I am, asking help from the most experts.

The network is like something "Huh???", but hey, I am using the IP with gateway that's not in the same subnet to post this thread, so it is possible and working. So, I actually just want to know: how to install ubuntu server without configure the network first and then after the installation, reconfigure the network with the gateway that's not in the same subnet.

Thank you guys a lot.

P.S. some part of the IP addresses I posted is modified for reasons.


> **JKyleOKC said:**
> We're using the word "gateway" with two different meanings. When using multiple static addresses provided by the ISP, the ISP will assign a gateway address that the ISP's router will be listening on. That's the gateway that I've been describing. The user is NOT free to just pick one of the static addresses at random and use it; the ISP should specify the address to use but apparently failed to do so in this case. That's why I suggested to "try" the usual address that ISPs supply.

The other meaning, which you appear to be using, is the address on each client box that it uses to get out to the outside world. If there's a user's router, or if the modem is doing NAT, then the router or modem's LAN-side address would be what to use as this gateway. In this case only one of the static IPs from the ISP would be recognized and the rest would be wasted. Most home-level routers are unable to handle multiple IPs on the WAN side, although AT&T does make available a unit that can (but with a mandatory $250 installation fee).

In my setup, I have one Xubuntu box configured to do my routing. It has two network cards. Eth0 serves the LAN and is connected to a switch; it has a local address of 192.168.0.2, and all other boxes on the LAN have this set as their gateway address for routing. Eth1 connects to the Internet, has an address of x.x.x.33, and uses x.x.x.38 as its gateway address. The kernel takes care of routing LAN traffic to the Internet by switching between the interfaces as necessary.

To make full use of my multiple static IPs, I have my DSL modem connected to a hub, and one line from that hub feeds eth1 on the Xubuntu router box. A second line connects to my wife's WinXP machine (that refuses to connect to my Linux-based LAN) and it has the address x.x.x.34, which is another of my 5 statics. Finally, a third line from the hub feeds a Linksys router with wireless capability at x.x.x.35, which lets my laptop and those of visiting family members connect to the Internet but not to my LAN. The other two IPs are presently unused; I had to buy five in order to get even one. It's all somewhat of a kluge but it does what I need.

---

### Post by JKyleOKC on 2010-06-20
It might help if you tell us the name of the ISP provider. Some of them, like AT&T, use "sticky static" addresses that are assigned via PPPoE (I'm fortunate in that mine are true static, grandfathered in so long as I don't make any changes to my account) while others may still be using DHCP. It sounds as if your provider might be one of the latter.

In most cases, addresses provided via DHCP include the DNS and gateway IPs as part of the notification package. If your ISP has told you to use a gateway address that's being handed out elsewhere via DHCP, that's a fatal error in their setup that they will have to fix. Their DHCP servers should exclude all static addresses from the list they use for assignment!

It will help us if you use "x" instead of a fictitious number for the first three octets of the addresses. That still preserves your security while making it obvious to us that it's been blanked out.

Finally, if none of us here can come up with a solution for you, you might visit [http://www.dslreports.com/]("http://www.dslreports.com/") and see if your ISP is represented by one of the group's forums. It's one of the best sources of help that I've found over the years, and is free. Several ISPs provide special "direct" forums there that are staffed by their own techs, so you can bypass the helpdesk droids who simply read from a script. It's also a great source for security information. If you type the address in, be careful about transposing letters: at one time a hardcore porn site existed with the same URL except that two letters were transposed!

You don't have to register in order to leave public questions, but use of the private "direct" areas does require (free) registration. The site is ad-supported, but in 8 years of visiting it daily I've yet to receive any spam from them.

---

### Post by Macsloverd on 2010-06-20
Thanks for the guiding,

here are some details:

ISP: Royal KPN (the Netherlands)
Package: Zakelijk ADSL - in English is Business ADSL
Connection: PPPoA
IP Range: x.x.x.216-x.x.x.223
Gateway: x.x.x.217 (what they say)
DNS: 213.75.63.36, 213.75.63.70

Modem(Router): Thomson 789vn with KPN customized Firmware (means most interesting functions have been disabled, basically it is a modem, router and VoIP telephony gateway, and there is no way to see what the external ip is for the router), it works much more like a bridge but the internal ip 192.168.1.254 of the router can be visited. Computers which connected to this router either use DHCP to get one of the 8 external IPs or manually type the internal IP as 192.168.1.10 with gateway 192.168.1.254 can connected to the internet without any problem and can ben ping though each other.

x.x.x.217 does not work, and it can be automatically assigned to any computer that is connected to the router.

Using DHCP will provide the gateway as 62.12.4.75 no matter the x.x.x.217 is used or not. This is not just to my connection, in my another office, same contracted connection, gateway is still 62.12.4.75, and ISP announced gateway does not work either.

My problem is that I need a server which has to be External IPed and Ubuntu based (or Debian but Ubuntu is much preferred), but using DHCP when installing Ubuntu server does not work, says not a DHCP network, manually type in the IPs doesn't work either, says gateway is in different subnet.

But booting into Ubuntu Live CD and install the Ubuntu desktop works perfect DHCP automatically recognized the SO CALLED not-same-subnet gateway.

What I want to know is that: Is there any way for me to manually set up the Ubuntu Server like the Ubuntu Desktop automatically configured the network so that I can have my ubuntu server online with a gateway that is not in the same subnet.





> **JKyleOKC said:**
> It might help if you tell us the name of the ISP provider. Some of them, like AT&T, use "sticky static" addresses that are assigned via PPPoE (I'm fortunate in that mine are true static, grandfathered in so long as I don't make any changes to my account) while others may still be using DHCP. It sounds as if your provider might be one of the latter.

In most cases, addresses provided via DHCP include the DNS and gateway IPs as part of the notification package. If your ISP has told you to use a gateway address that's being handed out elsewhere via DHCP, that's a fatal error in their setup that they will have to fix. Their DHCP servers should exclude all static addresses from the list they use for assignment!

It will help us if you use "x" instead of a fictitious number for the first three octets of the addresses. That still preserves your security while making it obvious to us that it's been blanked out.

Finally, if none of us here can come up with a solution for you, you might visit [http://www.dslreports.com/]("http://www.dslreports.com/") and see if your ISP is represented by one of the group's forums. It's one of the best sources of help that I've found over the years, and is free. Several ISPs provide special "direct" forums there that are staffed by their own techs, so you can bypass the helpdesk droids who simply read from a script. It's also a great source for security information. If you type the address in, be careful about transposing letters: at one time a hardcore porn site existed with the same URL except that two letters were transposed!

You don't have to register in order to leave public questions, but use of the private "direct" areas does require (free) registration. The site is ad-supported, but in 8 years of visiting it daily I've yet to receive any spam from them.

---

### Post by JKyleOKC on 2010-06-20
> **Macsloverd said:**
> What I want to know is that: Is there any way for me to manually set up the Ubuntu Server like the Ubuntu Desktop automatically configured the network so that I can have my ubuntu server online with a gateway that is not in the same subnet.It's my understanding that the only serious difference between the server and desktop editions is that the server edition omits the GUI and the desktop applications, which include the Network Manager. I suspect that it's Network Manager that is making the difference for you.

My boxes here are all using the light desktop version, Xubuntu; none of them use a server edition, yet I'm able to provide both FTP and Web servers that are adequate for my needs, and run a worldwide database recovery service that depends on the FTP capability to handle multiple-gigabyte data transfers. It's definitely not necessary to have the server edition in order to run servers!

I don't know how much traffic you need to handle, but it might be worthwhile trying a desktop installation to get everything working. If you disable the GDM service once all is going, that should stop the GUI from using resources, and most of the other desktop services use resources other than disk storage only when they are running.

---

### Post by bab1 on 2010-06-20
> **Macsloverd said:**
> ...

here are some details:

ISP: Royal KPN (the Netherlands)
Package: Zakelijk ADSL - in English is Business ADSL
Connection: PPPoA
IP Range: x.x.x.216-x.x.x.223
Gateway: x.x.x.217 (what they say)
DNS: 213.75.63.36, 213.75.63.70

Modem(Router): Thomson 789vn with KPN customized Firmware (means most interesting functions have been disabled, basically it is a modem, router and VoIP telephony gateway, and there is no way to see what the external ip is for the router), 
I believe you can see the external IP address by going to this site: [_[COLOR="Blue"]http://www.whatismyip.com/[/COLOR]_]("http://www.whatismyip.com/") with your browser when your computer is connected to the internet.  Could you post the results back here? > 

it works much more like a bridge but the internal ip 192.168.1.254 of the router can be visited. Computers which connected to this router either use DHCP to get one of the 8 external IPs 
Are you sure that the DHCP server is configured to supply you with external addresses?  Do you know the ip address of this DHCP server? > 

or manually type the internal IP as 192.168.1.10 with gateway 192.168.1.254 can connected to the internet without any problem and can ben ping though each other.

The Thompson sounds like it is for home use only.  The internal side is NAT'd to the private addresses in the 192.168.1.x range.> 

x.x.x.217 does not work, and it can be automatically assigned to any computer that is connected to the router.

Using DHCP will provide the gateway as 62.12.4.75 no matter the x.x.x.217 is used or not. This is not just to my connection, in my another office, same contracted connection, gateway is still 62.12.4.75, and ISP announced gateway does not work either.

My problem is that I need a server which has to be External IPed and Ubuntu based (or Debian but Ubuntu is much preferred), but using DHCP when installing Ubuntu server does not work, says not a DHCP network, manually type in the IPs doesn't work either, says gateway is in different subnet.

This really is not a DHCP vs. static issue, more like a  config issue.  I use both methods to configure multiple hosts in my network.  I have wireless using DHCP for all laptops and static (manual config) for the desktops.  They all work in the same subnet and can see each other with Samba, etc. > 

But booting into Ubuntu Live CD and install the Ubuntu desktop works perfect DHCP automatically recognized the SO CALLED not-same-subnet gateway.

It would help if we could see these spec's.  Boot using the LiveCD post the results of ```
sudo ifconfig -a
```> 

What I want to know is that: Is there any way for me to manually set up the Ubuntu Server like the Ubuntu Desktop automatically configured the network so that I can have my ubuntu server online with a gateway that is not in the same subnet.

You certainly can manually setup the servers IP addresses to use your public IP's.  See if you can provide the external IP of the ADSL modem and the networking spec's when booted into the Live CD.

---

### Post by Macsloverd on 2010-06-21
Thanks for the reply.

The Thomeson Modem is with a custom firmware for Business Use, and the same Modem for house uses another kind firmware - although they are the same product.

I tried the link you provided, it's really depends on witch computer I use, because any computer which connected to the Modem is having EXTERNAL IP - NOT NATed, NOT DMZ.

Most amazing part is that the DHCP server is 192.168.1.254 but the gateway is 62.12.4.75.

I'll come back with the ifconfig -a results. I have the route -n results on the first page if it does anything good.

One of the computer using ifconfig -a:

wlan0   link encap: ethernet  macaddress xx.xx.xx.xx.xx.xx
        inet4: x.x.x.219 bcast: x.x.x.223 netmask:255.255.255.248
        inet6: (ignore)
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        (Ignore)


> **bab1 said:**
> I believe you can see the external IP address by going to this site: [_[COLOR="Blue"]http://www.whatismyip.com/[/COLOR]_]("http://www.whatismyip.com/") with your browser when your computer is connected to the internet.  Could you post the results back here? Are you sure that the DHCP server is configured to supply you with external addresses?  Do you know the ip address of this DHCP server? The Thompson sounds like it is for home use only.  The internal side is NAT'd to the private addresses in the 192.168.1.x range.This really is not a DHCP vs. static issue, more like a  config issue.  I use both methods to configure multiple hosts in my network.  I have wireless using DHCP for all laptops and static (manual config) for the desktops.  They all work in the same subnet and can see each other with Samba, etc. It would help if we could see these spec's.  Boot using the LiveCD post the results of ```
sudo ifconfig -a
```

You certainly can manually setup the servers IP addresses to use your public IP's.  See if you can provide the external IP of the ADSL modem and the networking spec's when booted into the Live CD.

---

### Post by bab1 on 2010-06-21
> **Macsloverd said:**
> Thanks for the reply.

The Thomeson Modem is with a custom firmware for Business Use, and the same Modem for house uses another kind firmware - although they are the same product.

Are you saying you have one of each?> 


I tried the link you provided, it's really depends on witch computer I use, because any computer which connected to the Modem is having EXTERNAL IP - NOT NATed, NOT DMZ.

I'm not sure we are using the term "EXTERNAL" in the same manner.  The common meaning for  external is the the WAN side of your Thompson.  This is the side that has PPPoA (ATM).  I'm guessing that what you mean by "EXTERNAL" is known as the "public" IP address (e.g. the 216 - to 223 addresses).
> 

Most amazing part is that the DHCP server is 192.168.1.254 but the gateway is 62.12.4.75.


Are you aware that in your first post you used 67 as the first octet.  It wasn't until later that you changed to 62 as the first octet.  Could that be your part of your problem?

The DHCP servers address of 192.168.1.254 would be unusual but is not technically wrong.  The DHCP server does not have to be in the same subnet if DHCP forwarding is working.  

If indeed the gateway is at **[COLOR="Red"]62 [/COLOR]**.12.4.75 this also would be correct. From the ISP's point of view the gateway address is in both your and their network.  The ISP owns all of the 62.0.0.0/8 network (62.0.0.1 to 62.255.255.255).  Your subnet is but a small part of their network.  It is entirely possible for you subnet to be directly connected the ISP's router at 62.12.4.75.

Here are some examples of what I mean:

The 62.12.4.0/24 network has both the gateway IP (62.12.4.75) and the address range of 62.12.4.1 to 62.12.4.255 -- or we could use 62.12.4.0/23 with a range of 62.12.4.0 to 62.12.5.255 (note the 3rd octet).  To encompass everything in 62.12.x.x w would use 62.12.0.0/16 giving us a range of 62.12.0.1 to 62.255.255.254.

This would make sense if your Thompson was not doing more that DHCP and layer2 protocol conversion from ATM to Ethernet.> 

I'll come back with the ifconfig -a results. I have the route -n results on the first page if it does anything good.

One of the computer using ifconfig -a:

wlan0   link encap: ethernet  macaddress xx.xx.xx.xx.xx.xx
        inet4: x.x.x.219 bcast: x.x.x.223 netmask:255.255.255.248
        inet6: (ignore)
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        (Ignore)

What I am interested in seeing is the ***spec's of a working computer on your subnet*** (one the can see the internet (Microsoft is okay).  

This means:```
IP address 
b'cast address
subnet mask
default gateway address

route -n (or equivalent) 

```

---

### Post by Macsloverd on 2010-06-21
Your really helping me a lot, thanks mate!

the 67 is my wrong typing, sorry for that. It is indeed 62.

The route -n results are provided on the first page of this post. I will copy it here. I hope it can do something good for you to help me solve this.

And it is, indeed, what I mean by External, is what you can set DNS records with an A record - link the Domain name to the IP. This IP is what I meant for the External. Not something that simply generated by the router for internal LAN use.

route -n Results:
```
Destination      gateway   netmask          flags metric ref  use iface
-----------------------------------------------------------------------
62.12.4.75       0.0.0.0   255.255.255.255  UH     0      0    0   eth0
x.x.x.216        0.0.0.0   255.255.255.248  U      1      0    0   eth0
169.254.0.0      0.0.0.0   255.255.0.0      U      1000   0    0   eth0
0.0.0.0        62.12.4.75  0.0.0.0          UG     0      0    0   eth0
```

This result is generate when this computer is using the IP as x.x.x.219






> **bab1 said:**
> Are you saying you have one of each?I'm not sure we are using the term "EXTERNAL" in the same manner.  The common meaning for  external is the the WAN side of your Thompson.  This is the side that has PPPoA (ATM).  I'm guessing that what you mean by "EXTERNAL" is known as the "public" IP address (e.g. the 216 - to 223 addresses).

Are you aware that in your first post you used 67 as the first octet.  It wasn't until later that you changed to 62 as the first octet.  Could that be your part of your problem?

The DHCP servers address of 192.168.1.254 would be unusual but is not technically wrong.  The DHCP server does not have to be in the same subnet if DHCP forwarding is working.  

If indeed the gateway is at **[COLOR="Red"]62 [/COLOR]**.12.4.75 this also would be correct. From the ISP's point of view the gateway address is in both your and their network.  The ISP owns all of the 62.0.0.0/8 network (62.0.0.1 to 62.255.255.255).  Your subnet is but a small part of their network.  It is entirely possible for you subnet to be directly connected the ISP's router at 62.12.4.75.

Here are some examples of what I mean:

The 62.12.4.0/24 network has both the gateway IP (62.12.4.75) and the address range of 62.12.4.1 to 62.12.4.255 -- or we could use 62.12.4.0/23 with a range of 62.12.4.0 to 62.12.5.255 (note the 3rd octet).  To encompass everything in 62.12.x.x w would use 62.12.0.0/16 giving us a range of 62.12.0.1 to 62.255.255.254.

This would make sense if your Thompson was not doing more that DHCP and layer2 protocol conversion from ATM to Ethernet.

What I am interested in seeing is the ***spec's of a working computer on your subnet*** (one the can see the internet (Microsoft is okay).  

This means:```
IP address 
b'cast address
subnet mask
default gateway address

route -n (or equivalent) 

```

---

### Post by bab1 on 2010-06-21
> **Macsloverd said:**
> Your really helping me a lot, thanks mate!

the 67 is my wrong typing, sorry for that. It is indeed 62.

The route -n results are provided on the first page of this post. I will copy it here. I hope it can do something good for you to help me solve this.

Copying what you did yesterday is not what I need.  Specifically I need to see what is currently working.

What works automatically (i.e. with DHCP)?  What works with a Windows machine?> 

And it is, indeed, what I mean by External, is what you can set DNS records with an A record - link the Domain name to the IP. This IP is what I meant for the External. Not something that simply generated by the router for internal LAN use.

You can generate legit (Public IP addresses) on an internal LAN.  I do it all the time.  The ADSL modem may not be able to do this though.  Another reason to see what you can configure "automatically" with DHCP.

> 

route -n Results:
```
Destination      gateway   netmask          flags metric ref  use iface
-----------------------------------------------------------------------
62.12.4.75       0.0.0.0   255.255.255.255  UH     0      0    0   eth0
x.x.x.216        0.0.0.0   255.255.255.248  U      1      0    0   eth0
169.254.0.0      0.0.0.0   255.255.0.0      U      1000   0    0   eth0
0.0.0.0        62.12.4.75  0.0.0.0          UG     0      0    0   eth0
```

This result is generate when this computer is using the IP as x.x.x.219

And with this setup you can see the internet.  It works?  If it doesn't what does?

---

### Post by Macsloverd on 2010-06-22
> **bab1 said:**
> Copying what you did yesterday is not what I need.  Specifically I need to see what is currently working.

What works automatically (i.e. with DHCP)?  What works with a Windows machine?You can generate legit (Public IP addresses) on an internal LAN.  I do it all the time.  The ADSL modem may not be able to do this though.  Another reason to see what you can configure "automatically" with DHCP.



And with this setup you can see the internet.  It works?  If it doesn't what does?

I have sent you detailed info with PM, and yes, the route -n command was using up on a machine that with internet.

---

### Post by Macsloverd on 2010-06-25
Problem Solved and it is updated in the first post.

---

