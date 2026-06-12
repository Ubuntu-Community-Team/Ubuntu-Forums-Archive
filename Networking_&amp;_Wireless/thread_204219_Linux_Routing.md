---
title: "Linux Routing"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by Thund3rstruck on 2006-06-26
Hi all,

 I have a quick question for you guys. Right now I'm running a stock Linksys WRT54G v5 wireless router and its fine but I'd really like to implement packet filtering, logging, and possibly smtp/pop from the "router" device and the Wireless router doesn't meet all these needs. 

How hard would it be to setup something like this?

Internet | -->cable modem |-->Linux Router? |-->WRT54G WiFi |-->LAN PCs

I've been looking at Devil Linux to do this but I'm sure about it. Would it be better to get rid of the LinkSys wifi router and replace it with a Wireless Access Point?

---

### Post by jstueve on 2006-06-26
have you looked at replacing the firmware on the Linksys, and installing something like DD-WRT or OpenWRT that gets you a customizable linux on the router?

Also smtp/pop might be filtered on the standard ports with some ISPs.

---

### Post by kozimodo on 2006-06-26
[QUOTE=jstueve]have you looked at replacing the firmware on the Linksys, and installing something like DD-WRT or OpenWRT that gets you a customizable linux on the router?

Also smtp/pop might be filtered on the standard ports with some ISPs.[/QUOTE]
I believe that requires a different version of the WRT (either pre-5.0 or the WRT54GL).

---

### Post by schrombot on 2006-06-26
[QUOTE=kozimodo]I believe that requires a different version of the WRT (either pre-5.0 or the WRT54GL).[/QUOTE]

You are right, in order to flash the router with a third-party firmware on a wrt54g you need a version 1-4 router. Version 5 does not come with a linux based firmware and therefore does not need to be open and Linksys can keep it proprietory.

I would recommend you check out ebay and pick up a pre-v5 wrt54g, and flash it with the DD-WRT firmware. It will make your life a hell of a lot easier. Not to mention your 30 dollar router will act more like a 1500 dollar router.

---

### Post by Thund3rstruck on 2006-06-26
Yea.. to hack the WRT54G v5+ you need a JTAG and you have to do a hardware  hack. I did find a software only one (the micro) but unfortunatly I have the latest linksys bios (v1.00.9) and it cancels out the ability to use even that. 

I think I'm going to give M0n0wall a try. It seems kind of silly to run 2 routers (the Linksys and the M0n0wall router) so I'm thinking about replacing the Linksys with a WAP instead for the wireless laptops. 

The other concern I have is if I use an old PC to do this, it's going to have the older ethernet cards so isn't that going to slow down my internet connections?

---

### Post by mips on 2006-06-27
[QUOTE=Thund3rstruck]Hi all,

 I have a quick question for you guys. Right now I'm running a stock Linksys WRT54G v5 wireless router and its fine but I'd really like to implement packet filtering, logging, and possibly smtp/pop from the "router" device and the Wireless router doesn't meet all these needs. 

How hard would it be to setup something like this?

Internet | -->cable modem |-->Linux Router? |-->WRT54G WiFi |-->LAN PCs

I've been looking at Devil Linux to do this but I'm sure about it. Would it be better to get rid of the LinkSys wifi router and replace it with a Wireless Access Point?[/QUOTE]

If you can disable routing on the linksys and just bridge the connection. Alternatively leave the routing on and simply disbale all security. OpenBSD would make a really secure router/server.

---

### Post by Thund3rstruck on 2006-06-28
Yea.. I was looking at the configuration on the Linksys and it has a "gateway" mode that I can set which will allow me to direct it's traffic to another router. 

Thanks.. I think I'm going to go ahead and try pfsense, which I am hearing is the best solution out there

---

