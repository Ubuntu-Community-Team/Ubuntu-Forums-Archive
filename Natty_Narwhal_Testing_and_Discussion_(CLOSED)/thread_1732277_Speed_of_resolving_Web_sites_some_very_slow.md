---
title: "Speed of resolving Web sites: some very slow"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2011-04-18
Hello All

I'm using 11.04 beta 2 with current updates on an EeePC 1000 with solid state drives (8Gb for root and the 32 Gb for home). Most features seem to be working, some issues coming back from suspend, mainly with wifi. Unity seems to be working as intended and its growing on my for use on this small 1024 by 600 screen. Just wish the icon bar thingy could be positioned at the bottom.

Some web sites resolve and display quickly (bbc.co.uk, google.co.uk, other 'local' sites). Others take ages or time out (pinboard.in, dropbox.com and some blog type sites like tumblr.com based in the US). This is the same for Firefox or w3m, but different to other computers on the same wifi connection.

Any ideas? I've checked the network connections and its all the usual DHCP automatic type settings with ipv6 set to 'ignore'.

Cheers

---

### Post by dino99 on 2011-04-18
my only hard time is with planet.ubuntu.com, wonder why

---

### Post by keithpeter on 2011-04-18
> **dino99 said:**
> my only hard time is with planet.ubuntu.com, wonder why

Hello dino99, is that just with your Natty test installation or with all your computers?

What I'm trying to work out is why this only seems to occur on the laptop with Natty on! I'll boot that laptop from a USB live with 10.04 on and see what happens.

---

### Post by lucazade on 2011-04-18
Is an issue related to wifi only? Does wired connection work well?

Have you checked if it is related to you DNS resolving slow?
```
ping ubuntu.com
```
you should ping "time=50 ms" or 100 ms to have a responsive network.
(ctrl+c to break)

if ping time is higher try to change dns server with opendns:
208.67.222.222
208.67.220.220

or google dns:
8.8.8.8
8.8.4.4

give also a look at speedtest to see if network speed is in range
[http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by coffeecat on 2011-04-18
> **keithpeter said:**
> Some web sites resolve and display quickly (bbc.co.uk, google.co.uk, other 'local' sites). Others take ages or time out

That could be your ISP caching some popular sites, or just poor DNS servers. In which case lucazade's suggestion is worth trying:

> **lucazade said:**
> 
if ping time is higher try to change dns server with opendns:
208.67.222.222
208.67.220.220

With my previous ISP, I changed to openDNS on occasion whenever my own ISP's DNS servers were on a go-slow. Since changing ISP I've not needed to. Out of interest, which ISP do you use?

---

### Post by dino99 on 2011-04-18
its with natty (i386) only & only with planet.ubuntu.com
when i ping it into a terminal i get 22ms so its ok
but when i try to open with firefox it take more than 20 seconds and some times get a timeout

So dns is ok, ping is ok, other urls opened with firefox are ok, very strange as the problem is always true, not time related.

---

### Post by lucazade on 2011-04-18
> **dino99 said:**
> its with natty (i386) only & only with planet.ubuntu.com
when i ping it into a terminal i get 22ms so its ok
but when i try to open with firefox it take more than 20 seconds and some times get a timeout

So dns is ok, ping is ok, other urls opened with firefox are ok, very strange as the problem is always true, not time related.

if it happens only with a site it is probably that server!
if you are sure ping, dns are ok check with traceroute where packages are drop and look in dmesg if network driver drop some packages with a crc error.

---

### Post by dino99 on 2011-04-18
> **lucazade said:**
> if it happens only with a site it is probably that server!
if you are sure ping, dns are ok check with traceroute where packages are drop and look in dmesg if network driver drop some packages with a crc error.

i've already checked that cases but nothing logged; the problem is only to open this url, then using it is normal not slow

note: i've some protections like:
- adblocks, javascript off, flash off, ipblock, noscript
but as planet.ubuntu is not a commercial url it should not be a too complicated connecting process issue.

---

### Post by coffeecat on 2011-04-18
> **dino99 said:**
> its with natty (i386) only & only with planet.ubuntu.com
when i ping it into a terminal i get 22ms so its ok
but when i try to open with firefox it take more than 20 seconds and some times get a timeout

Pings to [http://planet.ubuntu.com/](http://planet.ubuntu.com/) are taking about 60 ms for me, but resolving and opening that page in firefox takes a second or so. About 1 second for the page to appear and a further 3-4 seconds to receive and display all the images further down the page.

---

### Post by Grenage on 2011-04-18
It's probably also worth mentioning that only the first ping will be indicative of a poor DNS server; the record would be cached after such time.

---

### Post by keithpeter on 2011-04-18
> **lucazade said:**
> Is an issue related to wifi only? Does wired connection work well?

thanks Lucazade

Auth0 works fine with all web domains coming up fast in Firefox. 

Ubuntu.com pings in about 25 mS on wifi or wired (they are, I suppose, just up the road on the Isle of Man)

dropbox.com pings around 150 mS, oddly enough also on wifi, but web page refuses to display at all. On wired connection to the same router and the same ISP, its up in a second or two.

Everyone;

Wifi behaviour is the same on a local convention centre connection, very slow on some sites, fast on others. Any ideas what is causing this big difference?

---

