---
title: "Network Monitoring"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by mmulqueen on 2009-08-05
I maintain a network for a small software development company.  In about 3 weeks, some of our clients will start using an application from our servers.  All of the sudden, bandwidth usage has become an issue to the guys upstairs.  The developers who work here are constantly using the internet to find coding help and sometimes even streaming video tutorials.  However, the bosses have also seen people streaming video from youtube or facebook or streaming their favorite radio stations.  It wasn't a problem before because work was still getting done but now it is a problem because the extra streaming could cause our clients to experience latency.  I've received a requirement for a network monitoring solution for which they, of course, are not willing to pay.  Does anyone know of an open source or free network monitoring solution that would allow me to easily see which sites are being visited and how much bandwidth a node is using?  It would also be nice if logged data could be dumped to a database to allow reporting.

Any suggestions are very much appreciated :)

---

### Post by frup on 2009-08-06
So your production servers are on the same connection as your workstations? :S

vnstat allows you to see each connections network usage etc. per computer

It doesn't differentiate between local and internet transfer etc.

---

### Post by gletob on 2009-08-06
I don't really see how your downloading could affect your users download that much?  Of course I'm not certified in anything but that's just my 2 cent

---

### Post by thisllub on 2009-08-06
Install squid and make everyone connect via proxy.
THen you can view the logs with something like sarc and ban sites like youtube.

---

### Post by mmulqueen on 2009-08-10
thanks for the suggestions.

---

### Post by running_rabbit07 on 2009-08-10
> **gletob said:**
> I don't really see how your downloading could affect your users download that much?  Of course I'm not certified in anything but that's just my 2 cent

You'd be surprised how quick a 10 gigabit connection can bog to a crawl when multiple users are streaming. Even with a good switch setup the collisions rise and therefore bog down the connection even more when all those packets are being moved. Kinda like the post office 3 days before Christmas. All it takes is one good collision for multiple systems to start requesting packets be resent.

May be a good Idea to set up a DNS server to block youtube.

---

### Post by callan79 on 2009-08-10
> **running_rabbit07 said:**
> You'd be surprised how quick a 10 gigabit connection can bog to a crawl when multiple users are streaming.

Hi,

thisllub recommended installing squid, I thought I'd just say yes, I agree!

You might want to have a look at [www.ebox-platform.com](http://www.ebox-platform.com). This needs a dedicated machine, but can be set up as a proxy/cache, web/email filter, traffic shaping and more.

I've got it set up at two sites right now. I'm not using the proxy but I did have a bit of a play and it seems to work well. You can even block certain TYPES of file ... for example block MP3.

Well worth a look.

And, eBox just runs Ubuntu Server under the hood :)

Cheers
Callan

---

### Post by OooBuntuRox on 2009-08-15
I'm not sure if this is the same question, but I would like to monitor my wireless network activity from a workstation. I only have a wireless workstation to do this from. But I would like to configure some software  (free please) that will warn me if anyone is attempting to access/ piggyback/ poke around my network.

Can that be done from a workstation?

Thanks, OooBuntuRox :guitar:

---

### Post by SolarOnline on 2009-08-17
[ipMonitor]("http://tinyurl.com/q9crts") has a free 1 month trial that should suit your needs for the short term. Unfortunatly it's usually the case that most network usage suites are not free.

---

### Post by karthick87 on 2009-09-04
Hi [thisllub]("http://ubuntuforums.org/member.php?u=184176") what is sarc?and how to view the logs using sarc?

---

### Post by nmsolutions on 2009-10-15
I would recommend that you try the solution from OpExpert, which is free and is well supported. The link is [http://www.opexpert.com](http://www.opexpert.com)

---

### Post by u2c4 on 2009-11-05
Another worth mention; IPcop + Bot + Advproxy + Urlfilter + Sarg

---

