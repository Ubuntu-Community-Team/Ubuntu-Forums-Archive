---
title: "2Wire Router and Ubuntu."
date: 2005-01-22
forum: Networking &amp; Wireless
---

### Post by izzydahedgehog on 2005-01-22
OK, here's the deal.  I have broadband at my house, and the broadband provider (SBC) gave us this 2Wire wireless router for the network.  You're supposed to just set up the network with a wizard that comes with the broadband stuff, but there is no Linux support.

Anyone else have a 2Wire router that they've gotten to work with Linux?

---

### Post by lockenkeyster on 2005-01-22
If you plug into the network jack on the router, can you see it's web interface? (try 192.168.1.1 in firefox; the IP might be wrong, check the documentation that came with your router)

I've setup a 2Wire and a Linksys this way, I just had to manually set the pppoe settings on the router using the server IP, default gateway and other info provided by SBC through the web interface.

---

### Post by kram on 2005-02-02
For the 2wire SBC connection. The default config page is located at gateway.2wire.net.
-Ram

---

### Post by alastair on 2005-02-02
We have a 2wire DSL modem/router at work - and it was a learning experience.

I had to plug a cable into it directly - by default, it sits on a 172.16.0.0/16 network.

You can set your system to be on this e.g. 172.16.0.2 - and use the web interface at 172.16.0.1.

---

### Post by paf on 2005-02-06
To configure it, I just connect by wifi, the dhcp give me an address and the gateway.

For me the 2Wire was by default on 192.168.1.254

I go to [http://192.168.1.254](http://192.168.1.254), and in broadband link>advanced>broadband network

I select pppoe (for me) and i put my login and password...

And it works.

---

### Post by geekgod on 2005-04-12
Manual Setup
use mozilla firefox or opera if possible for compatibility.

open browser

type homeportal/setup  or 192.168.1.254/setup

enter key 522P-22P4-6262-22AT-F2NV
CREATE A PASSWORD
select a timezone
ppp conection setup info

user [email]sbcyahooreg@sbcglobal.net[/email]
pass sbcyahooreg

you will get a configuration server error, 
you should have 3 green lights

now to register go to [http://help.sbcglobal.net/register](http://help.sbcglobal.net/register)

register

then type homeportal/setup  or 192.168.1.254/setup

enter your password skip the key and the time zone

ppp conection setup info: uid:yourname@sbcglobal.net pw:yourpass

poof may get a configuration server error  but your online.....

now does anyone know the registration servers for att.worldnet ??

---

### Post by izzydahedgehog on 2005-07-01
It all works now, spent some time with ndiswrapper and the drivers and it's fine.  All my difficulties up until this point were caused mostly by me not really paying attention to what I had to do to get wireless to work.

P.S. If anyone wants a wireless card that's dirt cheap and works well with minimal trouble (unless you're stupid like me), check out Encore.  The card I have cost $15.

---

