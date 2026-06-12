---
title: "How to get through the HUB?"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by ArtemNY on 2010-04-01
I'm a bit confused.
When my pc is connected directly to the LAN modem, my server can go online, ip connects to the domain and everything is cool.
When my pc connected to the router which is connected to the modem, I can't make my server go online. It asks for some linksys authorisation.

How can I teach my server to ignore my router and go directly to the modem. Unfortunately I can't just connect my server to the modem couse 3 more PCs are connected with the hub.

---

### Post by ArtemNY on 2010-04-01
Anyone? ;)

---

### Post by ArtemNY on 2010-04-01
Please? :)

---

### Post by ArtemNY on 2010-04-01
I don't need help to fix the problem, I need help to know where to look for some info. I don't know where and what to look for.

---

### Post by Schitso on 2010-04-01
Is it a router or a hub? The difference is important.

---

### Post by ArtemNY on 2010-04-01
> **Schitso said:**
> Is it a router or a hub? The difference is important.
It's a linksys cable router

---

### Post by ArtemNY on 2010-04-01
> **ArtemNY said:**
> It's a linksys cable router
Linksys BEFSR41
and the message is:

> A username and password are being requested by "here's my ip" The site says: "Linksys BEFSR41"

---

### Post by Iowan on 2010-04-01
What are the IP's involved - kinda sounds like you're accessing the router's configuration page. Is the router or modem (both?) a DHCP server?

---

### Post by ArtemNY on 2010-04-01
> **Iowan said:**
> What are the IP's involved - kinda sounds like you're accessing the router's configuration page. 
Yeah that's what happening when I log in on this page.
I checked with the linkys support what are the default login and pass for the linksys router conf. page so when this authorisation page opened, I just loged in to the router's config page. But I don't want this page to apper. I want my modem to go through the router dirrectly to the Internet so that my domain could be connected dirrectly to my IP.
 
When my computer connected dirrectly to the modem it has different IP from the one that appears when it's connected to the router. I guess that's how it should be because when it's connected to the modem, my IP is asighned by my ISP (I guess) but when it's connected to the router it's asighned by the router (I guess).
 
When my computer connected directly to the modem, everything works just fine. When it's connected to the modem _through_ the router, I get an authorisation page when I put my IP in the browser. 
 
 
> **Iowan said:**
> Is the router or modem (both?) a DHCP server?
Honestly, I don't know I'm not good with networking (yet).
 
If it'll help, my cable provider is Cablevision (Optimum Online) in New York.
 
I just checked the config. page of the router, it says "Local DHCP Server: Enabled"

---

### Post by Schitso on 2010-04-01
You need to make sure that your router is configured as a router and not as a gateway. I'm not sure if your router will enable DHCP forwarding when you set it as such, but if it doesn't you have to make sure that the DHCP router on the modem and the DHCP server on the router don't interfere. Could you post the DHCP settings of both the modem and the router?

---

### Post by ArtemNY on 2010-04-01
> **Schitso said:**
> You need to make sure that your router is configured as a router and not as a gateway. I'm not sure if your router will enable DHCP forwarding when you set it as such, but if it doesn't you have to make sure that the DHCP router on the modem and the DHCP server on the router don't interfere. 
So many senseless words for me :p
But I'll try hard to learn it all.
 
> **Schitso said:**
> Could you post the DHCP settings of both the modem and the router?
Can I check it in a terminal?
 
I've lerned how to open a config. page of the router but I don't know what exactly you need. And the modem I don't even know where to look...
So if it possible to check it in the terminal, I'd like to know what commands should I use. (I actually write down all useful commands)

---

### Post by ArtemNY on 2010-04-02
In Windows the same problem.

---

### Post by Iowan on 2010-04-02
What IP address do you get when connected to router and what address do you get when connected to modem? (Check with **ifconfig**)

You probably need to configure your router to work with modem. (Not really an Ubuntu problem, but we might still be able to help...)

---

### Post by ArtemNY on 2010-04-02
> **Iowan said:**
> What IP address do you get when connected to router and what address do you get when connected to modem? (Check with **ifconfig**)
24.185.147.*
24.185.147.**
Difference in one last figure only.
> **Iowan said:**
> You probably need to configure your router to work with modem. (Not really an Ubuntu problem, but we might still be able to help...)
Well I know it's not a Ubuntu problem, but can I solve it using Ubuntu somehow?

---

### Post by Iowan on 2010-04-02
Interesting addresses - I was expecting something more like 192.168.X.X... I suspected the router and modem might both be DHCP servers issuing addresses in the same range - the router would then have trouble with LAN and WAN ports on same subnet. 
Your router will probably configure via a web page - so pointing a browser at that address should work. I've no idea what username and password might be, but there are defaults - depending on router.

---

### Post by ArtemNY on 2010-04-02
> **Iowan said:**
> 
Your router will probably configure via a web page - so pointing a browser at that address should work. I've no idea what username and password might be, but there are defaults - depending on router.
That is correct. As I said before I know what the login and password are. And I CAN login to the router config. page via the browser, but I don't want it to appear, I want my IP to go directly to my computer, not to a router.

---

### Post by Iowan on 2010-04-02
> **ArtemNY said:**
>  As I said before I know what the login and password are. And I CAN login to the router config. page via the browser, but I don't want it to appear, I want my IP to go directly to my computer, not to a router.You did mention that (sorry...) Do the other machines connected to router have similar addresses? (I'm still a bit confused by local subnet). 

[Here]("http://www.hansenonline.net/Networking/Linksys101.html") is one tutorial I found for Linksys routers. Unless there's a reason to keep the 24.185.147.X subnet, enable DHCP on the router and use default range. Initially, you may want to get the WAN address via DHCP as well (that'd probably come from the modem). > ...but I don't want it to appear, I want my IP to go directly to my computer, not to a router. I'm not sure what you're asking. :confused:

---

### Post by ArtemNY on 2010-04-02
> **Iowan said:**
> I'm not sure what you're asking. :confused:
When I type my current IP in the browser, I get a router config. page login menu (now I know that it's a router's menu). I don't want it to be that way. When I type my current IP in the browser, I want it to be connected directly to my server, not to the router, so that outside world when typing my ip gets the server (my website on my server) not the router authorisation page.


PS I wrote to the linksys support. Let's see what they can get for me. ;)


PS2 I can't tell you how much I appreciate your help. THANKS A LOT!

---

### Post by lisati on 2010-04-02
> **ArtemNY said:**
> When I type my current IP in the browser, I get a router config. page login menu (now I know that it's a router's menu). 

I had the exact same thing happen on my system. The solution that worked for me was to set up forwarding of port 80 from the router to the machine I use as a web server.

Rough translation: the router needs to know where to send requests from the outside.

---

### Post by ArtemNY on 2010-04-02
> **lisati said:**
> 
Rough translation: the router needs to know where to send requests from the outside.
That's what my logic thinking was telling me, but I didn't know where to start and what to do or even what to google.

> **lisati said:**
> The solution that worked for me was to set up forwarding of port 80 from the router to the machine I use as a web server.

And how exactly did you do that in Ubuntu?

---

### Post by Iowan on 2010-04-02
OK, the fog lifts a little. For some reason, I thought you were working from the server - and I couldn't understand why you'd enter your own address in the browser. 
I'm still a bit confused about the subnet - you got the 24.185.147.X addresses via **ifconfig** (on the server) - not from whatismyipaddress.com?

---

### Post by ArtemNY on 2010-04-02
> **Iowan said:**
> 
I'm still a bit confused about the subnet - you got the 24.185.147.X addresses via **ifconfig** (on the server) - not from whatismyipaddress.com?
Oh shooot. :D
Hold on a sec I'll check it with **ipconfig** this time. :D LOL

---

### Post by ArtemNY on 2010-04-04
To hell this crap! No more Internet for other computers. I'm tired of that.
 
Thanks a lot everyone who tried to help me. Guys, I really really appreciate it!!!
 
**[THREAD CLOSED]**

---

