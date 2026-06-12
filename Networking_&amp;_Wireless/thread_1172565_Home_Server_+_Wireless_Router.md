---
title: "Home Server + Wireless Router"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by nakedfanatic on 2009-05-28
Hi,

I'm setting up a server for my home network, following the instructions here: [http://linuxgazette.net/141/lazar.html]("http://linuxgazette.net/141/lazar.html")

It is going quite well. I've completed steps 1-10, and the computers on my network can now access the internet via the my headless Ubuntu server.

The issue I have is that for each of these machines, I need to specify the Gateway and DNS for the server before they can access the internet. It would be preferable if new computers connected to the LAN could access the internet without special configuration. This was possible when I was only using a router for internet sharing. What do I need to do to have the same functionality from my server?

I am using a Linksys wireless router as my network hub with the server connected to a 'LAN' port at the back, rather than the 'Internet' port (I don't want the router to mask the IP addresses of computers accessing the server) Is there perhaps a setting on the router that needs changing?

Thanks for reading -- networking is not my strong suit and any help is appreciated!

Ian

---

### Post by Iowan on 2009-05-28
I only briefly scanned the article.  I presume you used a more current version that Feisty? The article didn't mention that you can set up your server to be a DHCP server - which *should* make setting up clients pretty easy.  I installed DHCP3 on my server - but in hindsight, wish I'd tried DNSMASQ - which (reportedly) ties DHCP to DNS, thereby making it possible to ping/connect/etc by hostname rather than (dynamic) IP address.

---

### Post by nakedfanatic on 2009-05-28
I'm using Jaunty Server 32bit. Most of the article seems to be still relevant.

Thanks for the advice. I'll do a bit of homework on DHCP and try it out.

---

### Post by Iowan on 2009-05-28
[Here]("https://help.ubuntu.com/7.04/server/C/dhcp.html") is a help page to get you started with DHCP, and [another]("https://help.ubuntu.com/community/Dnsmasq") for DNSMasq.

---

### Post by dmizer on 2009-05-28
The howto you are following is quite old, and out of date. Many of the suggestions it makes are dubious as a result (webmin and shorewall for example).

Also, you're better off relying on a hardware firewall instead of having a computer dedicated to this task. While I appreciate the learning experince involved, routers are really good at doing DNS/NAT/Firewall, are much easier to configure, maintenance free, and eliminate the risk of exposure due to misconfiguration (ex: a mal-formed iptables rule).

---

### Post by nakedfanatic on 2009-05-28
Interesting!

I would still like to use the server box for various tasks, such as a setting up a Squidproxy and various bandwidth shaping and monitoring tasks as I work out how. Bandwidth is very expensive in my country and I my family loves to download!

Would you suggest that the server resides inside the hardware firewall or in a DMZ?

Also, if Webmin is a dubious choice, is there a better option available or should I be configuring everything manually through SSH?

Thanks.

---

### Post by dmizer on 2009-05-28
> **nakedfanatic said:**
> Interesting!

I would still like to use the server box for various tasks, such as a setting up a Squidproxy and various bandwidth shaping and monitoring tasks as I work out how. Bandwidth is very expensive in my country and I my family loves to download!
Bandwidth monitoring is a good reason to have a server functioning as a gateway. If this is what you really need, I HIGHLY suggest:&#12288;[Ebox (as a stand alone gateway)](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Febox-platform.com%2F&ei=bkQfSoDgHIKYtAO95PmVBA&rct=j&q=ebox&usg=AFQjCNEuFr_CUummhE4VWFQj_6NWhYkgfw), [http://www.untangle.com/](http://www.untangle.com/), or [http://www.clarkconnect.com/](http://www.clarkconnect.com/) rather than hand configuring an Ubuntu server. These are specialized distributions specifically built to do serve as gateways. They have built in web interfaces and make configuration a breeze, and greatly reduce the risk of mis-configuration. Again, not that I'm trying to discourage using Ubuntu, but why go through all the trouble to build this when it's already built for you?

> **nakedfanatic said:**
> Would you suggest that the server resides inside the hardware firewall or in a DMZ?
It is far preferable to correctly configure port forwarding as needed. This way, you don't accidentally expose your server with a service you may have installed by mistake. Are you going to have this server exposed to the internet?

> **nakedfanatic said:**
> Also, if Webmin is a dubious choice, is there a better option available or should I be configuring everything manually through SSH?

Thanks.

If you are still motivated to go with Ubuntu for your gateway solution, then the suggestion has been to use [ebox](http://ebox-platform.com/) instead of Webmin. I haven't used it though and I'm unsure as to how close it is to Webmin but it looks pretty complete. What can't be configured through ebox should be configured via CLI. This will give you much better control over your server functions and greatly reduce the risk of mis-configuration.

---

### Post by Iowan on 2009-05-29
Shorewall is also dubious? You prefer Clarkconnect to Smoothwall - or just more familar w/ former?

---

### Post by dmizer on 2009-05-29
> **Iowan said:**
> Shorewall is also dubious? You prefer Clarkconnect to Smoothwall - or just more familar w/ former?

No, smoothwall express is good as well. But the smoothwall that comes with Webmin is not much more than a frontend for IPtables (unless there've been updates to Webmin since I last checked ... I'm willing to be corrected).

I actually have very little experience with smoothwall express and haven't seen many reviews on it, but clarckconnect is a complete gateway server, not just a firewall and gets mostly positive reviews. I've also used it personally and found it to be quite satisfactory.

---

