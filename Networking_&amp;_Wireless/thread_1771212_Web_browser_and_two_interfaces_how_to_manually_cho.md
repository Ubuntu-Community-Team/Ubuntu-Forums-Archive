---
title: "Web browser and two interfaces how to manually choose?"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by saidbakr on 2011-05-30
Hi,
I have wired connection Ethernet (eth0) and 3G connection GSM (ttyUSB0). Firefox uses eth0, but sometimes, I want Firefox to use ttyUSB0. How could I do that?

---

### Post by dandnsmith on 2011-05-30
In principal, you ensure that the ttyUSB0 has an IP address associated with it, and then change the routing so that the internet default is via that interface.

Details? I don't know, not ever having tangled with one of these.

BTW, You won't get both interfaces handling internet traffic in the same session, unless you do some fancy handling in IPtables or whatever.

---

### Post by saidbakr on 2011-05-30
Thank you!
I have done your suggestion as follows:
1- I got the properties of ttyUSB0, look at the attached image -[Screenshot-3.png]("http://ubuntuforums.org/attachment.php?attachmentid=193640&stc=1&d=1306763712")- and I found that its IP is 10.98.79.112 - Of course in the ISP Network -.
2- In the Firefox preference -> Advanced -> Network -> Connection settings - [Screenshot-2.png]("http://ubuntuforums.org/attachment.php?attachmentid=193640&stc=1&d=1306763712") I chose Manual Proxy and then I set the IP 10.98.79.112 and port 80 as shown in the image.

I have local Apache server, and also, I have dyndns.org account that I use it and updated its Ip using the ADSL wired connection. The ADSL router has NAT settings to forward port 80 requests to port 80 of machine IP 192.168.1.31 - My current computer on the wired network -

Without changing setting when I try to access my dyndns URL - myaccont.dyndns.org - it popup the request for ADSL router user name and password. After applying settings, It opens my local server home page.

That's fine. However, any other website such as facebook.com, is going to open my local server too. and this is the problem. Also downloading speed of pages component, inducate that connection is done locally, not through the Internet, where my 3G connection speed is 64 Kbs only!

Is there any further suggestions?

---

### Post by dandnsmith on 2011-05-31
> I found that its IP is 10.98.79.112 - Of course in the ISP Network

That isn't *of course* at all.
If you look at the 'recommendations' for local IP ranges you'll find top of the list is 10.0.0.0-10.255.255.255
I've noticed that the connections for mobile operations seem to use the 'local' ranges to make the end user part of their local network - the caveat being that these addresses have to be translated by the ISP before the traffic gets passed outside the mobile network.

As to the rest of it, I warned you that there were other problems - I cannot find a fix without a lot more information and, I suspect, a chance to play with a parallel setup (which I don't have).
Someone else in these fora may have a solution (but you may need to give more info about what you want to achieve).

Good luck

---

### Post by saidbakr on 2011-05-31
I remember that Internet Explorer in Windows has more simple connection option. I don't know why it isn't found in Firefox?!

---

### Post by dandnsmith on 2011-05-31
My FF just says 'use system proxy settings' and nothing more is needed.
You only need the others if you're trying to get really fancy.

I've never seen IExp as having simpler connection options - in my experience you can screw up the whole of Windows by picking the wrong choice.

---

### Post by saidbakr on 2011-05-31
The requirement of trying do that, is I'd like to test my local server application from another network on the Internet. I'd like to make one of web browsers on the system such as Firefox or Chrome to use the 3G network interface to get my local server from my dyndns URL. which is updated by the ADSL router IP, where My ADSL service provider give me an external IP, while the 3G service give me local IP in their network. is there any way to know the proxy server that 3G service using other than calling there silly support?!

---

