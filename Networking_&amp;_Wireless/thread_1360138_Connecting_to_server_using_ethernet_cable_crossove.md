---
title: "Connecting to server using ethernet cable crossover"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by CatsRninja on 2009-12-20
I have my laptop connected via wireless to the ubuntu server, and it works fine, i can ssh into it and sutch.

but it takes too mutch time to transfer big files, like backups, the top speed i get is arround 500kb/s.

So I figured i would jointhem in sweet comuunion via a ethernet cable.
I had 2 unused ethernet cables liying arround, so i made them into a crossover t568B.

but now im stuck, my laptop, running ubuntu, does find the connection and says its connected, without me doing a thing.
I mean, in the connections options i just put the Ipv4 options to shared with other computers, and in the connection options it gives me a ip and a broadcast address, without me doing nothing.

ok, in the server, i can put the eth0 up using ifconfig and while changing the interface file (/etc/network/interfaces) i dont know how i should configure it to work, shall i give it a static ip?

i did, i added:
auto eth0
iface eth0 inet static
      address XXX.XXX.XXX.XXX

restart the networking
```
/etc/init.d/networking restart
```

it complains i dont have the wireless working( i unplugued the pen from the server)
and it complais eth0 lacks configuraion options.

Thinking i did no mistakes with the cables, how should i configure the thing?(both desktop server and laptop.

im running the newest server edition and the newst desktop edition.

Awaiting for a reply,
have a nice day,
CRN

---

### Post by Iowan on 2009-12-20
> **CatsRninja said:**
> 
and it complais eth0 lacks configuraion options.Sounds kinda odd - what does the complaint look like? (Almost sounds like DHCP server complaining). 
Check **ifconfig -a** on both machines - are they in the same subnet?

---

### Post by CatsRninja on 2009-12-22
I dont know mutch about networking,so i guessing stuff.
Probably guessing wrong.

I want to connect 2 pcs via ethernet with a crossover cable.


I added this lines in the server /etc/network/interfaces

auto eth0
iface eth0 inet dhcp

This activates the dhcp right?
Then gone to ubuntu desktop networkconnections, in the tab of auto eth0, cliked edit,
put it to connect automaticly and activated dhcp.

then it start connecting, but comes out as "wired network disconected" after a while.

and doing network restart  on the server, it starts looking for dhcp a guess i get something like this:
Listening to LPF/eth0/XX:XX:XX:XX:XX:XX 
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port XX interval X
no DHCPDISCOVER received.
no woeking leases in persistent datavase - sleeping

oh, and ifconfig -a doesnt show nothing wrong.

I just want to connect the 2 things with a cable directly.cant find that on google search.
If all this is ok, i guess the cable must be wrong.

---

### Post by Iowan on 2009-12-22
Unless you have a DHCP server configured on one of the machines, you will get the message you got.  

Hold the ends of the cable beside each other. A "standard" cable will be the same on both ends - probably white (with orange stripe), then orange (with white stripe). A crossover cable will be that way on one end, the other will start with white (with green stripe, then green (with white stripe).

There may be a way to enable the "zero-conf" (avahi) networking - I haven't used it.

---

### Post by ant2ne on 2009-12-22
I'd suspect a bad cable. If this is the first that you made, then you probably failed. Making these things is a pita and it is easy to make a faulty one. 

if you know the cable is good, both joining NICs should have an 169.x.x.x addy in ifconfig.

---

