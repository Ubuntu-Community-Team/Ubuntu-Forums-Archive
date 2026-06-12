---
title: "Network Drive Activity"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by asearle on 2013-04-25
Hi everyone,

This might be a little bit off-topic but I'm sure that someone out there will have an idea ...

I have a Lacie Networkspace network drive which works fine with Ubuntu:  Simply plug it in and it is visible.

The drive has a private (password protected) area and a public area (no password) and plugs into my router (standard LAN cable).  When I have a connection with the drive it flickers and is obviously active (even when I am not transfering or accessing files).  But when I shut down my PC the drive often still flickers and whirrs indicating activity.  My worry here is that somehow the drive is being accessed from the internet.

Does anyone have any thoughts on this?  Should I maybe stop being paranoid and simply trust the firewall?  Are there other tests that I can do?  Are there ports that I should block?

Many thanks for any tips that you can give me.

Yours,
Alan Searle

---

### Post by TheFu on 2013-04-25
You are probably being paranoid since most ISPs block CIFS access over the internet, however, if you are not in a "western country", then you should be completely paranoid. I've seen crazy ISP network setups in some less developed countries that place huge groups of ISP customers on the same subnet - allowing access to anything each client didn't specifically block.

Many home routers have back doors or just huge bugs.  If you are still running the stock firmware, it is very possible that someone on the internet has changed your settings and **is** accessing your internal network.  There are automatic tools that do this these days.  It is very likely if you didn't change the default password on the router too.

Another likely thing is that the device is "phoning home" to the manufacturer. More and more devices are doing this, including home Cisco/Linksys routers, media players, etc.

Now that I've scared you, what solutions can I offer?
* Only buy network equipment that you trust, from vendors that you trust.
* For homes, look for routers that support dd-wrt, openWRT and/or tomato replacement firmware.  After you get the device home, REPLACE the vendor firmware with one of those. Choose F/LOSS over commercial if that is an option.
* For businesses, look for commercial-grade routers. If it is designed for your house, it is not designed for a corporate environment. You can still deploy F/LOSS router solutions - I just put a pfSense box in at a monastery in Kathmandu. These are more complex than home routers, but provide much more capability.
* Block all inbound ports by default on the internet.
* Block all non-TCP/UDP protocols by default on the internet.
* Block IPv6 in all forms, unless you understand it AND you need it. We really need to block IPv6 tunnels over IPv4 by default.
* Only allow outbound ports to specific target ports/protocols.  This is where home routers fail and networking becomes more complex. Basically, DNS, HTTP, IMAPS and SMTPS should be allowed - the last 2 only to specific servers that you know and use. Do not allow outbound SMTP to any random address on the internet. 
* If you don't know that you need it, block the outbound port and protocol by default.

Most of this stuff you can accomplish with any home router firmware. Some of it, you cannot. That doesn't necessarily mean you are or will be cracked.

---

