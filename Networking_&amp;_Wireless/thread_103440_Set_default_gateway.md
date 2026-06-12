---
title: "Set default gateway"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by xeo_pt on 2005-12-14
I have a server with 2 NICs eth0 and eth1, the eth0 conects to the internet, eth1 connects to the internal network, my problem is when the system goes down the default gateway (eth0) changes to eth1 preventing from the acess to the internet.

What file is the default gateway set?

Thanks.

---

### Post by yoyoned on 2005-12-14
/etc/network/interfaces

---

### Post by xeo_pt on 2005-12-14
[QUOTE=yoyoned]/etc/network/interfaces[/QUOTE]

Thanks but in interfaces the gateway is for that nic not for all the system.

---

### Post by afhp on 2005-12-15
Not sure I understand the nature of your problem. Do you mean eth0 and eth1 do come up, but the actual card each refers to is not the same on restart?

If that's the case you might want to look into the command ifrename and its configuration file, iftab. This pair allows you to force the identification (ethX) to a specific device (based on MAC for instance) regardless of how the kernel actually loaded them.

---

### Post by xeo_pt on 2005-12-15
[QUOTE=afhp]Not sure I understand the nature of your problem. Do you mean eth0 and eth1 do come up, but the actual card each refers to is not the same on restart?

If that's the case you might want to look into the command ifrename and its configuration file, iftab. This pair allows you to force the identification (ethX) to a specific device (based on MAC for instance) regardless of how the kernel actually loaded them.[/QUOTE]
I'm sorry but you didn't understand.
I have 2 cards eth0 and eth1!
When the system is restarted I don't have internet and can't ping IPs outside the LAN (connected eth1) because the default gateway of all system is eth1(my internal network), so I had to go to system->network a change the default gateway option to eth0 (the internet card) in order that when I type an address outside my internal network it *goes out *to the internet!

I need to set permanently the gateway to eth0.

Thanks for your help.

Regards.

---

### Post by afhp on 2005-12-15
[QUOTE=xeo_pt]I
When the system is restarted I don't have internet and can't ping IPs outside the LAN (connected eth1) because the default gateway of all system is eth1(my internal network), so I had to go to system->network a change the default gateway option to eth0 (the internet card) in order that when I type an address outside my internal network it *goes out *to the internet!

I need to set permanently the gateway to eth0.
[/QUOTE]

Oh, OK. I'm getting a better picture now, but I need another bit of info : how does eth0 gets its IP address ? Is it defined statically, or dynamic ? What is it connected to ?

> the gateway is for that nic not for all the system

As it should be, I think.

The way I understand it, the other machines on your network need to have the default gateway set to the IP address of your internet-connected machine's eth1, that seems to be the case. The internet-connected machine needs to have the default gateway set to the upstream address connected to eth0.

As an example from my own setup (which is the opposite of yours) :

eth0 connected to the LAN has an IP address of 192.168.0.10 : this is the default gateway for *all other machines* on the network. 

eth1 gets its IP address and default gateway from the DSL modem/router it's hooked into -- eth1's address is my public IP address and the default gateway is the endpoint at my ISP's.

So, back to your setup : if eth0 gets set from DHCP, it should have the default gateway set at the same time ; if that's not the case, there's a issue with the DHCP server's settings. If, on the other hand, eth0 is set statically, it is indeed in /etc/network/interface that the default gateway should be defined under the eth0 section, and set to the IP address of whatever eth0 connects to.

Unfortunately I can't give you file samples to clarify : my own gateway machine runs a specific, slackware-based distribution which is set differently -- the principles are the same but the files don't match those in debian/ubuntu.

---

### Post by mlomker on 2005-12-15
You'll want to use static addresses for both interfaces and only put a gateway (default route) on the one facing the Internet.  The problem with DHCP is that it always sets a default gateway and isn't configurable on an interface basis for that setting.

There's a package called **ifmetric** that'll allow you to set a preference when there is more than one gateway (if both cards are using DHCP).  It's a bit of a pain, though, because you have to re-run the command-line tool each time that one of the cards gets an address....a problem because DHCP addresses renew at random times.  There should be a way to script it in the dhclient scripts, but I found it too much trouble and just went static.

---

### Post by xeo_pt on 2005-12-16
Thank you for your reply!
eth0 gets the adress from a DSL router, here is the draw:

[INDENT]DSL Router IP: 192.16.1.1

eth0 IP: 192.168.1.8
gateway: 192.168.1.1

eth1 IP: 192.168.0.1
gateway:192.168.1.8[/INDENT]

I hope this helps.

Thank you.

---

### Post by afhp on 2005-12-16
[QUOTE=xeo_pt]
eth0 gets the adress from a DSL router, here is the draw:
[/QUOTE]

Sounds like DHCP then.
> 
DSL Router IP: 192.16.1.1
eth0 IP: 192.168.1.8
gateway: 192.168.1.1

Looks right.

> 
eth1 IP: 192.168.0.1
gateway:192.168.1.8

Try removing the gateway definition on that one. As mlomker said, you should only have the "default gateway" (by definition there can be only one default) set for the router-facing interface. 

Do make sure that all other machines on the LAN have *their* gateway defined to 192.168.1.8, of course.

---

### Post by xeo_pt on 2005-12-17
> 
Do make sure that all other machines on the LAN have *their* gateway defined to 192.168.1.8, of course.

But all the computers in my internal network are from address 192.168.0.x!
I will try next Monday.

Thanks to all of you.

---

### Post by kosmic on 2005-12-17
yes but the gateway is 192.168.1.8 because it is eth0 who receives conections from the outside :)

---

### Post by Ahriman on 2005-12-18
I am having similar problems with my network connections. My Internet connected device is wlan0 and my LAn device is eth0. No matter how many times I change the Default Gateway Device in System -> Admin -> Networking to wlan0, on reboot it always comes back to eth0.

---

### Post by InDenial on 2005-12-19
Default gateway means nothing more than: If you are going to send data to an ip-address you do not know. send it to the default gateway.

so in your case you have an internal network which has a default gateway of the eth1 interface of the router. In other words. The client pc's all send their information to the eth1 interface if the destination ip-address is not within their subnet. 

In your case after a reboot, the server gets a default gateway from the modem which is the ip-address of the dsl router. It will send all his data he receives on eth1 interface (clientside) to the dslrouter through eth0.

so far so good. we are getting the data out from the clients to the internet. 

What happens next is that the data comming back (for instance the webpage you are wanting to see) comes into the dsl router. The dsl router will send it to the router on eth0 and... it stops. For some reason the router does not know that your clientside ip-range is behind eth1.

Could you copy paste the result of the command route? And.. further what does not work when this happens?.. is it just that you are not able to browse the internet? are you able to ping the dsl router from a client pc?

---

### Post by xeo_pt on 2005-12-20
> Try removing the gateway definition on that one. As mlomker said, you should only have the "default gateway" (by definition there can be only one default) set for the router-facing interface.
Thats it buddy:)  I remove the gateway and it work as expected.
Thanks a lot.

Regards.

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=mlomker]You'll want to use static addresses for both interfaces and only put a gateway (default route) on the one facing the Internet.  The problem with DHCP is that it always sets a default gateway and isn't configurable on an interface basis for that setting.

There's a package called **ifmetric** that'll allow you to set a preference when there is more than one gateway (if both cards are using DHCP).  It's a bit of a pain, though, because you have to re-run the command-line tool each time that one of the cards gets an address....a problem because DHCP addresses renew at random times.  There should be a way to script it in the dhclient scripts, but I found it too much trouble and just went static.[/QUOTE]

Will the "post-up" commands (from /etc/network/interfaces) be executed for an interface configured by DHCP?  If so, could the interface just have a "route del default" command?

---

