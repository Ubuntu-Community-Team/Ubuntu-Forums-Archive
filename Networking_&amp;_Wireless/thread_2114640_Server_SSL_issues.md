---
title: "Server SSL issues"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by Izzzy9999 on 2013-02-10
I have a couple of network issues I can’t resolve so hopefully a guru here can point me in the correct direction.

I’m running a server with Ubuntu 12.10, connected to a DD-WRT router connected to my ISP’s cable modem. I’m hosting 2 web servers each with domain names purchased from cheapname.com. The @ and www are both set to URL Frame to the IP address of my cable modem. Up to this point everything works fine. Enter the [www.xxxxxxxx.com](www.xxxxxxxx.com) for each site and there you are with the domain name framed in the browser address bar.

Here’s the first problem. I can’t get SSL to work. I purchased an SSL cert and set it up in Apache2 for one of the sites. When you browse to that site you get an error:

xx.xx.xx.xx  uses an invalid security certificate.

The certificate is only valid for the following names:
xxxxxxxx.com , [www.xxxxxxxx.com](www.xxxxxxxx.com)  

The xxxxxxxx.com is the proper website domain. I’m guessing that it’s complaining about the IP address. CS at cheapname told me that using URL Frame should solve the problem but it doesn’t.  Their other suggestion use to get a Unified (UCC) certificate which allows you to use IP as common name. The problem is that I’m hosting these sites for a couple of community groups for free. I don’t want to pay hundreds of $$ per year for a UCC. Is there any way around it? 

The second problem is this. Both sites are running Simple Machine Forums. The users that join them show in the log with the IP address of the router and not their public IP addresses. Every user in the logs of both sites is 192.168.1.1. Any way to solve this?


Thanks for any input.

---

