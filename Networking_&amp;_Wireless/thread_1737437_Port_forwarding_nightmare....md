---
title: "Port forwarding nightmare..."
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2011-04-23
This is of the simplest things to do when running a web server at home.  However I cannot, for the life of me, figure out why nothing is working. It just happened recently as I have had this working perfectly before.

I have a Westell adsl modem on AT&T dsl service.  Connected to that, is one of the newer linksys E2000 routers.

My setup is a little different but I don't think that changes anything.  OR, it could be everything.

Modem is connected to the internet obviously.


Modem Internet IP:   (DHCP)

Modem LAN Settings.

Modem IP(Static): 1.1.1.1
Netmask:  255.255.255.0

Router IP:  1.1.1.2
Netmask:    255.255.255.0
Gateway:    1.1.1.1
DNS:        8.8.8.8
Sec DNS:    1.1.1.1

Router LAN settings:  (DHCP)
IP:  2.1.1.1

DHCP settings:

Start with 2.1.1.2 with 5 clients allowed.

DHCP reservation 2.1.1.3 - Web Server

Web server DHCP with address of 2.1.1.3 connected via ethernet to router.

I have the modem set to IP passthrough giving the router outside access.

all the necessary ports are forwarded to 2.1.1.3 from the router.

My website is [www.bencookemusic.com](www.bencookemusic.com)  it gets forwarded to dyndns.com acquiring the name patriotsystems.thruhere.net.

the router's DDNS settings are correct, however, it thinks that the internet IP is 1.1.1.2.  Therefor, dyndns.com thinks that 1.1.1.2 is my internet address also.  When I try to go the dyndns.com and manually change it to the correct Internet address, it still doesn't work.

I don't have an outside Internet source to trace route so I don't know where the packets get stopped at.

---

### Post by kelt65 on 2011-04-23
> **pepsifx357 said:**
> This is of the simplest things to do when running a web server at home.  However I cannot, for the life of me, figure out why nothing is working. It just happened recently as I have had this working perfectly before.

I have a Westell adsl modem on AT&T dsl service.  Connected to that, is one of the newer linksys E2000 routers.

My setup is a little different but I don't think that changes anything.  OR, it could be everything.

Modem is connected to the internet obviously.


Modem Internet IP:   (DHCP)

Modem LAN Settings.

Modem IP(Static): 1.1.1.1
Netmask:  255.255.255.0

Router IP:  1.1.1.2
Netmask:    255.255.255.0
Gateway:    1.1.1.1
DNS:        8.8.8.8
Sec DNS:    1.1.1.1

Router LAN settings:  (DHCP)
IP:  2.1.1.1

DHCP settings:

Start with 2.1.1.2 with 5 clients allowed.

DHCP reservation 2.1.1.3 - Web Server

Web server DHCP with address of 2.1.1.3 connected via ethernet to router.

I have the modem set to IP passthrough giving the router outside access.

all the necessary ports are forwarded to 2.1.1.3 from the router.

My website is [www.bencookemusic.com](www.bencookemusic.com)  it gets forwarded to dyndns.com acquiring the name patriotsystems.thruhere.net.

the router's DDNS settings are correct, however, it thinks that the internet IP is 1.1.1.2.  Therefor, dyndns.com thinks that 1.1.1.2 is my internet address also.  When I try to go the dyndns.com and manually change it to the correct Internet address, it still doesn't work.

I don't have an outside Internet source to trace route so I don't know where the packets get stopped at.

For starters, stop using public address on your internal LAN. There isn't any reason to do so and it can cause problems.

---

### Post by pepsifx357 on 2011-04-23
> **kelt65 said:**
> For starters, stop using public address on your internal LAN. There isn't any reason to do so and it can cause problems.

I think I might know what you're talking about.  1.1.1.1 right?

I never understood this.  I use 1.1.1.1 merely for ease of remembrance and organization.

What is the correct way of doing this.  And is there a list of IP addresses that most people use when doing internal IPs.  192.168.1.1  just seems like a complicated number to use.

I really didn't think that had an effect on the outside.

EDIT: Ok, I found a website giving me a list of private IP addresses that I could use.

The Modem's LAN is now set to 10.1.1.1

Router is 10.1.1.2

Router's LAN is 10.10.1.1

And the web server is now 10.10.1.3

I turned the DDNS service OFF on the router and installed "ddclient" on Ubuntu instead. It looks like the DDNS is working, however, I still can't get my website to work outside.

I finally got port 80 and 22 forwarded, but ports 21 and 25565 are still unresponsive.  I really don't understand this.  It's been working fine in the past.

21 doesn't work when using the dynamic dns domain name of patriotsystems.thruhere.net but if I use the internet IP it works.  I've never had this much trouble forwarding ports.

---

### Post by pepsifx357 on 2011-04-23
Double Post, sorry.

---

### Post by restorator on 2011-04-23
You need to do a little more studying about networks. the reason people use 192.168.x.x and 10.x.x.x and 127.x.x.x is that they are basically designated to be for purposes of internal networks. You cant just arbitrarily choose numbers unless your network will never be connected to the outside world.

One of your problems is that your subnets (the different sets of numbers between the dots) are different. For all things on your network try keeping the first 3 sets of numbers the same and just changing the last set. ie., 10.1.1.1, 10.1.1.2, 10.1.1.3 etc.That gives you 254 addresses to use. It gets a lot more complicated if you use different numbers for more than the last set and you need to use different netmasks etc., and for your purposes there is no need to go into those details.

---

