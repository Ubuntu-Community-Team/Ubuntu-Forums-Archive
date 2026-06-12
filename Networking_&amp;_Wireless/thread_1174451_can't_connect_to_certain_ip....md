---
title: "can't connect to certain ip..."
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by nestorpistor on 2009-05-30
Edit title should say ***[COLOR="DarkRed"]Can't PING certain ip...[/COLOR]***

Im having a puzzler.

Installed xubuntu, fresh install went well.  wireless config went well.

I'm trying to used the Citric ICA Client to connect to my work computer but it says can't connect.  Turns out I can't ping that IP/domain name and I know it's available 24/7 as we have use use it when on-call and because i've connected to it using several linux distros.

Turns out I can't ping the domain name or the ip but I can ping other domain names/ip but I;ve noticed that it is quite slow returning time.

I didn't install a firewall but it appears that UFW was installed but I turned it of,  there are no iptables rule.  I need to get this running if I'm going to use this distro.  

To tell you the truth I actually like this ubuntu distro better then any other Ubuntu and want to keep using it if I can get this fixed.

Any advise or help is greatly appreciated.

Nestor Pistor

---

### Post by Brandon Williams on 2009-05-30
Are you certain that your citrix server and/or corporate firewall are configured to respond to ping? Many corporate networks will drop ICMP pings. For this reason, ICMP pings are an unreliable test of network connectivity. They are only useful if you know that the other machine is susposed to respond.

---

### Post by anarchyinc on 2009-05-31
The first things I do whenever I'm setting up ANY network are;

1) block ping requests
2) enable MAC filtering

Now, depending on what the network actually is used for I'll proceed from there, It's just good security.

---

### Post by superprash2003 on 2009-05-31
yes ,there is a possibility of the server blocking your requests..

---

### Post by nestorpistor on 2009-05-31
Yes I admit it may be blocking my pings BUT I was able to connect with Citrix using Ubuntu Studio, Mepis, Debian, and Kubuntu.  with just some security certificate issues that were solved effortlessly.  

So I guess I want to  know why I can't connect to my corporate server in order to tke over my PC at work from home using Xubuntu?

Thanks
Nestor

---

### Post by nestorpistor on 2009-05-31
[SIZE="5"]SOLVED...[/SIZE]

It would really help if I addressed the right web site.  Some time I really amaze myself...

Thanks to all that replied.

Nestor Pistor

---

