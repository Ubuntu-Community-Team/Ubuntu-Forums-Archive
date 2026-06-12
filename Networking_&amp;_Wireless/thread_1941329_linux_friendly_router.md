---
title: "linux friendly router"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by jdh77 on 2012-03-15
What is the most Linux friendly router amongst Dlink/LinkSys/or ??? 

Wired/wireless?

thanx for all suggestions.

jdh77

---

### Post by dandnsmith on 2012-03-15
What nature friendliness are you looking for?
I've never had trouble with my netgear routers, and generally a router is a router and is fairly transparent to your network connections - with the possible exception of firewall software being incorporated.
The only other thing I can think of is that some come with setup software which only works under (some) Windows - but this isn't a necessary thing (unless you connect via usb to it).

---

### Post by haqking on 2012-03-15
most if not all residential routers are running linux as their OS, and most commercial ones are too or a bespoke IOS which is often *nix based.

There should be no compatability issues at all.

Connection via wifi or ethernet and potential issues will not be OS specific but more of a an issue with your wifi hardware, encryption methods and the like and nothing to with your brand of router.

Chers

---

### Post by Grenage on 2012-03-15
> **haqking said:**
> Connection via wifi or ethernet and potential issues will not be OS specific but more of a an issue with your wifi hardware, encryption methods and the like and nothing to with your brand of router.

Quite so; home routers/gateways should really be dealing with ubiquitous network protocols and standards, which will work fine on just about any system.

---

### Post by Cerin on 2013-01-30
> **Grenage said:**
> Quite so; home routers/gateways should really be dealing with ubiquitous network protocols and standards, which will work fine on just about any system.

I wish this were the case. Linksys used to be the gold standard. Ever since they were bought by Cisco, their routers have become garbage. Unfortunately, I didn't realize this until recently.

I bought a Cisco Linksys EA2700 wireless router. Connected to its web admin interface, it now has a prompt that strongly encourages you to run the Windows-only install CD, and says using the admin interface may damage the router.

Even though it claims to simeltaneously support A, B, N, and G wireless protocols, half my wifi devices couldn't even see the wireless network, even after I tried enabling each protocol individually.

It's also incredibly slow to retrieve DHCP data from upstream. I have a Comcast connection, and with an earlier Linksys WRT54G router, it "just worked", but I had to call Comcast and have them "reprovision" the IP for my connection to get it to work with the EA2700.

There are also no status lights on it (except for ethernet plugs on the back), so it's not easy to tell if wifi is enabled or any ports are in use.

I ended up returning the router, and using my older Linksys WRT54G until I can find something faster (the WRT54G tops out at 13Mbps).

I'm still looking for a Linux-friendly wireless router, but I'd recommend everyone avoid Cisco/Linksys like the plague.

---

### Post by Bucky Ball on 2013-01-30
> **grenage said:**
> quite so; home routers/gateways should really be dealing with ubiquitous network protocols and standards, which will work fine on just about any system.

+1.

---

### Post by Mark Phelps on 2013-01-30
> **Cerin said:**
> I bought a Cisco Linksys EA2700 wireless router. Connected to its web admin interface, it now has a prompt that strongly encourages you to run the Windows-only install CD, and says using the admin interface may damage the router.
All that does is install CISCO Connect -- an app that allows you to administer the router without using a Browser. I have an E2000 and have had no problems using different Ubuntu versions with it.

> Even though it claims to simeltaneously support A, B, N, and G wireless protocols, half my wifi devices couldn't even see the wireless network, even after I tried enabling each protocol individually.I used "mixed mode" with G/N and, apart from the low performance (which is to be expected in Mixed mode), it worked fine.

> It's also incredibly slow to retrieve DHCP data from upstream. I have a Comcast connection, and with an earlier Linksys WRT54G router, it "just worked", but I had to call Comcast and have them "reprovision" the IP for my connection to get it to work with the EA2700.You should have EXPECTED that to be the case.  Even though they DENY it, Comcast used the MacAddress of the router to grant authorization.  I confirmed that when I upgraded a relative's router and they were denied access.  Used the Mac Address spoofing capability of the new router to set it to the "old" MacAddress -- and it worked just fine.

> There are also no status lights on it (except for ethernet plugs on the back), so it's not easy to tell if wifi is enabled or any ports are in use.Mine is "old enough" to still have status lights.  Don't know why the router suppliers are "dumbing these down".

> I ended up returning the router, and using my older Linksys WRT54G until I can find something faster (the WRT54G tops out at 13Mbps).

I'm still looking for a Linux-friendly wireless router, but I'd recommend everyone avoid Cisco/Linksys like the plague.
You might look at the TrendNet routers.  I recently go a wireless bridge model and it works great -- took about 5 minutes to set it up using WPS.

---

### Post by Lemuriano on 2013-01-30
I use a  Netgear WNDR3700 that I use with DD-WRT and usb/connect a hard drive using ext3. I believed ext4 was not supported on that router but I just format the hard drive using ext3.

---

### Post by Cerin on 2013-01-30
> **Mark Phelps said:**
> 
You should have EXPECTED that to be the case.  Even though they DENY it, Comcast used the MacAddress of the router to grant authorization.  I confirmed that when I upgraded a relative's router and they were denied access.  Used the Mac Address spoofing capability of the new router to set it to the "old" MacAddress -- and it worked just fine.


I did expect that and I've successfully done that in the past. I tried it in this instance, and even though the MAC reported from the non-functioning EA2700 matched that in the functioning WRT54G, it didn't work until I had to manually call Comcast.

---

