---
title: "Port Forwarding (Ubuntu, Airport Extreme, Port 25565 and 25560)"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by Christop406 on 2011-06-26
I've been searching everywhere for an answer to this question, How do I port forward, if that's what needs to happen on Ubuntu, and get it online through my Airport Extreme router? I'm trying to get a minecraft server back online since it's been down for days now, so a quick response would be nice!

---

### Post by Christop406 on 2011-06-26
Plz not to be pushy but i have a community of about 700 people waiting for me to get this server back up!

---

### Post by lanmangler on 2011-08-13
This may primarily be just a problem with the Airport config. Any of the web how to articles for your router should take you through the advance settings to open your router up to allowing those ports.  IF your router settings got reset, by default these ports are not open.
 
I just did the same with a different router and was able to get it running smoothly. I do not think there is anything necessary with Ubuntu by default.
 
To get further assistance, you will need to post more info on your version of Ubuntu, and for starters info on any firewall you may be running on Unbuntu.

---

### Post by lanmangler on 2011-08-13
If you are reconfiguring the router, you'll want to use a port checking tool such as
 
[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)
 
This will tell you when your router and linux config looks right on those ports.  You'll also want to make sure you are using the right external IP address for everyone to connect to... which may depend on your ISP is giving you a dynamic or static IP. Most cheap ISP connections are dynamic, so your external IP(that will have your configured ports forwarded to it from the Airport) are dynamic and change on every reset or reboot of the router.

---

