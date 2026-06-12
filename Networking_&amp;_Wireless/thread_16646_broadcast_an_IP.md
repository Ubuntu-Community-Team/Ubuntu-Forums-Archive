---
title: "broadcast an IP"
date: 2005-02-22
forum: Networking &amp; Wireless
---

### Post by Rule on 2005-02-22
Hi

I have 2 nics in my computer, the first nic(eth0) is connected to my modem and my 2nic(eth1) is connected to my router but eth1 doesn't have an IP so I have it one 

```
sudo ifconfig eth1 192.168.1.105 broadcast 192.168.1.1 netmask 255.255.255.0
``` 
I think I did it right 

but my router doesnt have IP :-?  so how do I assign it one?

TIA
Rule

---

### Post by az on 2005-02-23
If I understand:

You have a computer which is connected directly to the internet through a modem.  You want to route (share) this connection to a router.  The router will then service other computers.  
The reason why you want to connect the interent directly to the computer is so that you can use it as a webserver, or something else.  Otherwise, you would just connect the modem to your router and then connect your computer to the router.

If this is not correct so far, please explain. why.

What you need to do is called masquerading or NAT (network address translation) to share the internet connection.

sudo apt-get install etherconf.

This wil configure your two cards.  You should give the card which will be connected to your internal network (the router) a network address that is different then the network address of the router.

Example:
WAN                  -> DMZ           -> Router           ->other computers
64.65.66.76    192.168.50.1    192.168.0.1    192.168.0.101, 192.168.0.102, 192.168.0.103

So that your router knows what address to use, you can either set it up to have a static ip address or you can run a dhcp server on your DMZ computer.  In that case, you just tall your router to make a dhcp request.

sudo apt-get install shorewall shorewall-doc #This is to set up NAT and some firewalling
sudo apt-get install dnsmasq  #You need to tell the other copmuters about DNS, so you will need this package, too.  It includes a dhcp server!  Great stuff.  Really easy to get going.

---

### Post by Rule on 2005-02-23
well I installed shorewall and I flollowed this guide [http://www.shorewall.net/two-interface.htm#id2496032](http://www.shorewall.net/two-interface.htm#id2496032) but nothing is happening, my router still isn't getting an IP  :?  :-s

---

### Post by alastair on 2005-02-23
What is the "router" - something more than a hub or switch? 
Is it a device that is managed somehow?

---

### Post by Rule on 2005-02-23
it's a linksys router (befsr41) I can change it's setting through a web browser.

---

### Post by alastair on 2005-02-23
OK - so it's just a 4 port switch + DHCP server essentially.

The router IP address is set via its management (web) interface. I looked at the user guide :

[ftp://ftp.linksys.com/pdf/befsr41V3_ug.pdf](ftp://ftp.linksys.com/pdf/befsr41V3_ug.pdf)

and this appears to default to 192.168.1.1 - unless you changed it.

To me, it sounds like your modem (DSL?) should be connected to the router - as should your PC.

If you "manage" your router - I assume you do it through a web browser e.g. [http://192.168.1.1](http://192.168.1.1) - this is its IP address.

What was the problem again? :-)

---

### Post by gylf on 2005-02-23
It sounds like your problem is DHCP, not shorewall.  That link above is just for shorewall firewall.  To setup DHCP you can use dnsmasq, as azz mentioned above.  It looks like DHCP is disabled by default, so make sure its enabled.  Check out: [this site](http://leaf.sourceforge.net/doc/guide/user-bering-uclibc/bucu-dnsmasq.html) , specifically section 3.4 on enabling DHCP.

Then, double check the easy stuff.  Make sure the computer w/ shorewall on it is plugged into the WAN port on the router.  Then you can try disabling DHCP on the router and see if any of the computers on the network get an IP from the shorewall computer (or, plug one directly into the shorewall computer)  That way you can test if DHCP is properly working on the shorewall computer, or if the router is being wierd, etc.

---

### Post by Rule on 2005-02-23
well I enables dhcp, but my laptop doest get an IP. now also when I connect the laptop back into the router I can;t access the web interface anymore haha odd very odd

---

### Post by Rule on 2005-02-23
also form my 2nd nic(eth1) i'm very confused to what IP, subnet mask and default gateway to give it.

EDIT:well my laptop can access the router now, but it seems like the routers dhcp wanst working so once I put in an IP manually it worked once agian. :smile:

---

### Post by alastair on 2005-02-23
Why do you need 2 ethernet devices in your PC? Are you sure you need 2?

You have a router already.

DSL modem --> router ---- 1 LAN port ----> PC ethernet eth0

Have you ever connected to the router's web interface? Did you change it's IP address? If not :

 - connect a router LAN port via ethernet to eth0
 - make sure eth0 has an IP address on the router's network e.g. eth0 == 192.168.1.2
 - go to the web interface ([http://192.168.1.1](http://192.168.1.1)) and check what you need to check

Please specify what you are trying to do - access the internet via the router/modem?

---

### Post by Rule on 2005-02-23
my motherboard came with 2 10/100 10/100/1000

what i'm trying to do is DSL > pc > router > 3 other windows PCs

I just notied this [http://www.shorewall.net/bridge.html](http://www.shorewall.net/bridge.html) so i'm not sure if I can do this since I don't have a switch.

---

### Post by alastair on 2005-02-23
The router is a 4 port switch as well - so your config is no problem.

DSL modem --> router DSL/internet port

4x PC''s --> router LAN ports (yours and up to 3 others)

That's it really. By all means run a firewall on your PC, but it is not needed (at least not initially, to get it all working).

There's no need to use more than 1 ethernet device on your PC.

On your PC, the router IP (e.g. 192.168.1.1) is the default route for you (and the other router connected PC's). The router knows how to get to the internet, and route LAN traffic to/from - this is its reason to exist.

Hope that helps.

---

### Post by alastair on 2005-02-23
P.S.

For the moment - forget about firewall on the PC (Shorewall etc.). I think the router seems to have a basic firewall anyway.

Get connected as I say above and make sure you can access the router web management. Turn off eth1 - use eth0 just now. 1 PC (e.g. eth0)  -- 1 ethernet port --> 1 router LAN port.

---

