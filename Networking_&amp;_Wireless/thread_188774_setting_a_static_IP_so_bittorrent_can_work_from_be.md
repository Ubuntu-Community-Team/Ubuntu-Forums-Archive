---
title: "setting a static IP so bittorrent can work from behind router"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by mental_drummer on 2006-06-04
Hi,
My computer uses a Inexq ISW054t router to connect to the internet which, if i understand correctly, means I need to set a static IP to use bittorrent. I did this with Breezy and it worked fine. However, when I set a static IP in Dapper the internet stops working...
Not really sure what the problem is. I *think *I'm doing everything right cos it worked on Breezy (althought the was a certain amount of guesswork envolved!).

Thanks for any help you can give me

---

### Post by nikolokolus on 2006-06-04
Well, I have no specific knowledge of your router, but I can give you a general sort of way to configure static IP.

your router should have its own private IP (LAN not WAN IP) eg. 192.168.1.1 a subnet mask of 255.255.255.0 (typically).

In order to communicate through your router properly you will need to set your computer's static IP to fall within the same subnet as the router for instance 192.168.1.2 (or whatever IP range is allowed by your router).  This assumes you are talking about a wired ethernet connection and not a wireless connection; those usually require some sort of DHCP or static DHCP address assignment.

FYI:  If your router supports UPnP correctly and you enable UPnP inside of Azureus, then your router can dynamically assign the appropriate port ranges and forward traffic to the correct computer on the fly rather than having to setup forwarding rules inside the router.

Good luck


ps. I found this link which may or not be any help at all.[click here]("http://www.bmannconsulting.com/node/1149").  My other suggestion would be to get a decent router (like a linksys wrt 54gl) and ditch what looks to be a pos router :/

---

### Post by mental_drummer on 2006-06-04
Lol I see what u mean about getting a descent router - I guess this is what u get for buying the cheapest one in Argos...
Thats kinda how I thought the IP thing worked - it's just so gaulling that it worked under Breezy but not Dapper. (no slight on Dapper - it quality)
:-k hmm scratchy chiny

---

### Post by stimpack on 2006-06-04
Try not to use UPnP if possible!, its not as big a deal under Linux as Windows, but letting programs alter your routers routing is very bad unless you trust that program or are even aware that a malicous program in the background is doing this.

---

### Post by nikolokolus on 2006-06-05
[QUOTE=stimpack]Try not to use UPnP if possible!, its not as big a deal under Linux as Windows, but letting programs alter your routers routing is very bad unless you trust that program or are even aware that a malicous program in the background is doing this.[/QUOTE]

I mentioned UPnP mostly as a last resort (if the user was unable to setup static DHCP).  But you are right that UPnP can be nasty if not monitored carefully.

---

### Post by toolisima on 2008-06-12
Hey there!
I've been searching and searching for how to correct a NAT problem with Azureus...and while trying out ports and trying to figure out how to set a static IP (see that I really dont know what I am doing!) something went really bad and now Azureus disappears as soon as I try to open it....dont know how to fix this (tryed to uninstall it and install it again, but still disappears).

So I try now to use BitTornado client to see if this is easier to go around, then I find out I have very very low download speed.
I have a Hughes HN7000S router and want to use as much as I can my download capabilities. Can anyone help? I am an absolute beginner in networking and dont want to mess around anymore!

---

