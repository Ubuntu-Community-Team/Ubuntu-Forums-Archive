---
title: "My  own little website"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2010-11-05
Ok here is my little project I have in mind. I have a pc with wireless I want to allow my other laptops to connect to it ( no internet involved) to access it as a web page, and other services later on, do I have to install some software i,e lamp, apache, etc. Or is there basic software in Ubuntu I can use to do this. I suppose my own little website. Also setting up wireless connection, would it be adhoc or infastructure. Also want makes it become an infastructure?

---

### Post by tgm4883 on 2010-11-05
> **spiky001 said:**
> Ok here is my little project I have in mind. I have a pc with wireless I want to allow my other laptops to connect to it ( no internet involved) to access it as a web page, and other services later on, do I have to install some software i,e lamp, apache, etc. Or is there basic software in Ubuntu I can use to do this. I suppose my own little website. Also setting up wireless connection, would it be adhoc or infastructure. Also want makes it become an infastructure?

You will need to install a webserver on teh PC (such as apache).

Adhoc is point to point wireless. Having and connecting to a router is what makes it infrastructure.

---

### Post by spiky001 on 2010-11-05
Ok so with a website running on pc I would still set connection as adhoc and it would stiil be seen by all wireless devices

---

### Post by dforthman on 2010-11-05
I've never messed with ADHOC, but just installing Apache, connecting to a wireless router you may having lying around the house, and then pointing to your webserver's IP address from your other computer(s) in a browser is simple enough to set up.

---

### Post by spiky001 on 2010-11-05
Ok I have set up adhoc wireless with adhoc, but the ip is set the same as eth0 10.42.43.1, the only way to get a wireless connection was set ipv4 to shared to other computers, if I set it to manuel so as to set ip of say 192.168.1.1 I cant connect. Is there a way to set wireless ip to 192.168,1,1 and still connect via wireless and leave eth0 as it is 10. etc this is to save confusion on ssh

---

### Post by tgm4883 on 2010-11-05
> **spiky001 said:**
> Ok I have set up adhoc wireless with adhoc, but the ip is set the same as eth0 10.42.43.1, the only way to get a wireless connection was set ipv4 to shared to other computers, if I set it to manuel so as to set ip of say 192.168.1.1 I cant connect. Is there a way to set wireless ip to 192.168,1,1 and still connect via wireless and leave eth0 as it is 10. etc this is to save confusion on ssh

Are you using a router in your network?

---

### Post by spiky001 on 2010-11-05
No router I have set pc with wireless no internet I want to connect with ip address 192.  I also have eth0 connection to another server which has internet connection, so I suppose I want 2 networks to connect to 1 via eth0 and 1 wireless only internal

---

### Post by cracker89 on 2010-11-05
let the settings for ipv4 remain auto for the connection. a router might be of some help tho..

---

### Post by lisati on 2010-11-05
I havn't having messed with Ad-hoc networks. My gut feeling is that using a router might be easier in the long run and take some of the workload off your computer.

---

### Post by cracker89 on 2010-11-06
> **lisati said:**
> I havn't having messed with Ad-hoc networks. My gut feeling is that using a router might be easier in the long run and take some of the workload off your computer.
  Ditto.

---

### Post by spiky001 on 2010-11-06
Ok I have it all set up at the moment no web page yet just ip addresses, If you select it via network manager is there away that it will open up on a web page so ( Network manager finds wireless spiky.com,) then connect will it open on my web page that is what i,m asking if not can it be done? or am I hoping for abit much "maybe"

---

### Post by tgm4883 on 2010-11-06
> **spiky001 said:**
> Ok I have it all set up at the moment no web page yet just ip addresses, If you select it via network manager is there away that it will open up on a web page so ( Network manager finds wireless spiky.com,) then connect will it open on my web page that is what i,m asking if not can it be done? or am I hoping for abit much "maybe"

That would require client side changes I think, which would need to be coded. Not saying it can't be done, but I don't know of a current way to do it.

---

### Post by spiky001 on 2010-11-06
LOL I knew I was expecting to much, I have a few more problems yet will get back with them still on this post

---

### Post by spiky001 on 2010-11-06
Ok I have just discovered a problem If I turn off all pc,s then I cant connect to wireless again, the main pc is setup shared ipv4 with ssid, the 1 I want to connect with has ip address manuel 192 etc then netmask 255 etc no gateway. To get it to work I have to delete main pc wireless connection redue it then it works any ideas plz

---

### Post by spiky001 on 2010-11-06
Ok an update to get it started from the no connection if I use Connect to hidden wireless it will all connect how to make it show when I switch on?

---

