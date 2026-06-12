---
title: "DNS Translation to Internal Servers?"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by computer13137 on 2009-06-26
Hi,

I've got an interesting question.  I've never seen this discussed anywhere, and I'm wondering if it's possible.  I'm fairly sure it is- because I think I've seen it done in the past.

I have a server\router for my network running Ubuntu 9.04.  Currently, I run Apache on it, and create virtual hosts for my domains.  This is working fine, but I'm considering setting up a RAID and running a VMWare Server for my own local use for testing\containment of websites, etc.

Anyway, reasons aside, what I'd like to do is setup some kind of... "DNS NAT" is the best term I can come up with.  I want multiple domains, on different internal servers on my LAN, to be able to share port 80 on a single external IP address.

For a simple text-diagram...

Router (1.2.3.4 Internet) (10.1.1.1 LAN)
       -- Foo.com (1.2.3.4:80) on 10.1.1.5:80
       -- Foo1.com (1.2.3.4:80) on 10.1.1.6:80
       -- Foo2.com (1.2.3.4:80) on 10.1.1.7:80

I also created a Visio diagram with a lot of useless notes about how\why I want to set this up this way. ;)

[[IMG]http://www.imghost.oabw.net/img02/1246120240.png[/IMG]]("http://www.imghost.oabw.net/img02/1246120240.png")

So, where should I start?  Am I going to have to specially configure Apache on my router, or can this be done with IPTables (which I doubt).  

I have no problem with running custom configurations on my router... nor do I have a problem with doing complicated\custom DNS.  I currently run BIND on the server for my DNS anyway.

Thanks for your time and consideration in taking a shot at my question. :)

Cheers,
Kirk

---

### Post by jhannah on 2009-06-28
In the strictest sense, there isn't a way to accomplish exactly what you describe. Keep in mind that, from the routers perspective, the domain that was resolved to get the end user's packets to it is transparent. That is, the end user resolves the domain and then sends the traffic to the address it got back. In this case, all of your domain names are going to be going to the same IP address so the router has no criteria on which to differentiate traffic going to foo1.com from foo2.com - at least on a DNS level. That being said, I think there is a way to accomplish the goal, at least as I see it from yoru post.

If you were setup Apache with VirtualHosts on the router, you could setup a reverse proxy for each VirtualHost which pulls content directly from the internal IP that corrosponds to the site. This effectively relates the HTTP host header to a particular internal IP which the reverse proxy server will then serve as though the content were it's own. You could likely accomplish the same goal with something like squid or nginx which, depending on which you are more comfortable with, might be easier in the long run.

Does that speak to your question?

---

### Post by Boondoklife on 2009-06-28
This might help you out [http://www.yolinux.com/TUTORIALS/ApacheRedirect.html,]("http://www.yolinux.com/TUTORIALS/ApacheRedirect.html")

---

### Post by jonobr on 2009-06-28
computer13137, I cant really help you , but I was hoping someone was going to answer.

I was thinking about reverse dns, or (this probably does not suit based on your post)
Having one main homepage with links to the four internals.

Given your requirement for segmentation , i dont think it will help.

However, my only reason for responding, is to compliment you on an excellent well, presented and detailed post,
Its rare to get such detail and effort put into a thread, and I it think should be commended when done.

---

### Post by computer13137 on 2009-06-29
jhannah: Yeah, I was actually thinking of giving mod_proxy a try, but I wasn't going to suggest it to the community - I was thinking maybe there was a better solution that you guys would come up with. 

maletek: Looks like a useful link for some experimentation.  :)

jonobr: Heh, yeah.  I thought it was an interesting question - since I've never seen anyone else ask it.  Plus, I could see it having a lot of cool uses.  I recall having an Internet friend who had a TLD pointed at his house, and a subdomain for each computer.  I never asked him how he did it and he kind of disappeared... I'm guessing he likely used mod_proxy since I'm fairly sure he was on home cable and didn't have multiple IPs.

Yeah, I'm not sure if I'm going to do anything with the setup, but I'm thinking about setting up a virtualization server with like a 2.83Ghz Core2Quad and a 2TB RAID5 for keeping my data safer and giving my various services, like my game servers and several websites, somewhat separate.  My thought was that since VMs have different IPs, I could try a setup like what I'd seen my friend do. :P

So yeah, I'll look into mod_proxy, and I'd welcome any other suggestions anyone has. :)

Cheers,
Kirk

---

