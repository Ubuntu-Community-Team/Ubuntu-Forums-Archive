---
title: "Multiple web servers share ONE physical IP address"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by oliveryang on 2009-04-04
I'm quite new to to this area. I know we can have multiple websites with different domains hosting in the same server. But my situation is a little bit different. Not sure if this is possible. 

I have two server machines. Server A and B. Each machine runs its own web server. I also have two domain names for each website but I have only one IP address and one port, which is 80, to allow incoming traffic.

I'm thinking two methods:
1. Using a router which holds a physical IP address and set DMZ to Server A. When connecting to serverA.com, it just shows the website of server A. When connecting to serverB.com, server A directs the incoming traffic to server B. Server B then send the webpage to the users.

2. Using a hub but installing two ethernet cards in server A. One holds physical IP and the other owns private IP and connects to the hub. Server B only has a private IP. The rest is like what I describe in 1.

Is either way possible? If the answer is positive, then how to set up server A?

Thank you very much.

---

### Post by Iowan on 2009-04-04
Dunno if it's what you're looking for, but [here](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/) is a How-To for name based virtual hosting.

---

### Post by kreggz on 2009-04-04
I think you will need to use a content switch or load balancer.

If the router has 1 public IP you would need a device with a Virtual IP which points to the right internal IP address - in theory.

---

### Post by oliveryang on 2009-04-05
> **Iowan said:**
> Dunno if it's what you're looking for, but [here](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/) is a How-To for name based virtual hosting.
Thanks for your reply. This is a very informative article. But virtual hosting seems not what I need here. It hosts multiple websites in a single server. I'm looking for a way to have multiple servers sharing one public IP.

---

### Post by oliveryang on 2009-04-05
> **kreggz said:**
> I think you will need to use a content switch or load balancer.

If the router has 1 public IP you would need a device with a Virtual IP which points to the right internal IP address - in theory.
Thank you very much. I'll look into this. Since I'm not intend to buy a new equipment except ethernet card (if needed), load balancing might work in my case.

---

### Post by tgalati4 on 2009-04-05
Change your port on machine B to 8080. Poke a hole in your router firewall at 8080.

---

### Post by oobe-feisty on 2009-04-05
sure both are possible what you need is to setup iptables to have firewall rules to route certain requests to server b from server a easiest way i can think of is to have apache on server b listen on a different port then forward all external traffic on that port to server b using iptables

woops i didnt read tgalati4 comment he said roughly the same thing except you will need to forward the port either using your router or iptables

---

### Post by oliveryang on 2009-04-06
Thanks for everyone's help.

I've checked iptables and didn't see how to differentiate the incoming traffic by its "domain names". Since there is only one port (80) available to public, using different ports to differentiate incoming traffic to server A or B becomes impossible. I can't just forward incoming traffic on port 80 to server B because I also have another website on server A.

Let me describe the scenario again.
serverA.com on server A
serverB.com on server B
one IP and one port (80) to public, all the other ports are blocked.
The public IP is on server A.

---

### Post by oobe-feisty on 2009-04-06
you need to configure apache to listen on port 8080 on server B and use your router to forward ports to its lan ip or use iptables iptables cannot tell a service or daemon to listen on a certain port it will be set in /etc/apache2/ports.conf


> **oliveryang said:**
> Thanks for everyone's help.

I've checked iptables and didn't see how to differentiate the incoming traffic by its "domain names". Since there is only one port (80) available to public, using different ports to differentiate incoming traffic to server A or B becomes impossible. I can't just forward incoming traffic on port 80 to server B because I also have another website on server A.

Let me describe the scenario again.
serverA.com on server A
serverB.com on server B
one IP and one port (80) to public, all the other ports are blocked.
The public IP is on server A.

---

### Post by oliveryang on 2009-04-08
I'm not sure if I misunderstood what tgalati4 and oobe-fesity's posts. Did you mean using router to forward port 80 to server A and 8080 to server B? If this is what you mean, then it won't work in my case.

Both server A and server B are behind firewall. Port 80 is the only port that opens to public. That is, if a user type [http://serverB.com:8080/](http://serverB.com:8080/), this url will go nowhere. It will be blocked by firewall. Besides, I don't want to use any port other than 80. It would just make users confused.

I really appreciate your help. I'm quite new to setting up web server. That's why I keeps circling at the same point. I didn't quite understand what you mean. Load balancing sounds a good idea so far but it also looks a bit complicated. I'm just looking to see if there is a easier way to do it. Thanks:)

---

### Post by tgalati4 on 2009-04-09
There are 64k ports available.  What's the issue with opening port 8080?  That's the only way to route IP traffic to two different servers sharing the same external address.

As far as users:  bookmark the page.  All of my bookmarks have long URL's with tokens.  Once the page is bookmarked, no reason to forget using 8080.  You can use any port above 10k.  8080 is a common, reserved port for web traffic.  Choose a port with a meaningful number.

---

### Post by jalmod on 2010-04-22
I have exactly the same requirement.
 
Can not use other port for the other server or serverB.
 
Some copmanies do not open all ports for thier staff, so those staff can not access my second server.
 
Appreciate your help.

---

### Post by jalmod on 2010-09-13
No more hints!!!!!!

---

### Post by annoyingrob on 2010-09-13
Apache2 has the ability to host multiple virtual websites on the same machine on the same port. Take a look at the first reply to your thread with the link to the howto.

For example, on my home network, I have a webserver running. If people try to connect to it from my external domain, it routes to one page, and if I try to connect to it from my home's internal domain, it directs to another page.

All of the connections to the webserver come from the same port on the same interface. Apache simply looks at the URL that the client was trying to connect to, and points it to the appropriate site on my server.

---

### Post by jalmod on 2010-09-24
Your suggestion does not show how to handle multiple internal servers with single external IP and single port.

---

### Post by Zanthir on 2010-10-04
I also have the same problem. I'm using GoDaddy DNS, and you can't assign a domain name to a port. I probably just need some more advanced DNS settings, but I haven't figured it out on that end. I'm trying to use a SVC rule (to put requests to a certain sub-domain to port 8080 instead of 80) but haven't had any luck.
 
I'm wondering, can you use Apache virtual host to point one website to another computer/local IP? This would solve the problem. Alternately, I was thinking, "if I use ESX, I can combine the two machines into one virtual machine, then I could just do typical virtual hosting with Apache."
 
So, I guess one solution (although, not a convenient or easy one, might require an additional network card or two, research, time, etc.) would be to use ESX. Any better ideas?

---

### Post by SeijiSensei on 2010-10-04
> **jalmod said:**
> [LEFT][FONT=Calibri][SIZE=3]Your suggestion does not show how to handle multiple internal servers with single external IP and single port.[/SIZE][/FONT][/LEFT]

Do some research on load balancing and round-robin DNS.

---

### Post by Zanthir on 2010-10-04
> **SeijiSensei said:**
> Do some research on load balancing and round-robin DNS.
 
Found this on Wikipedia: In addition to using dedicated hardware load balancers, software-only solutions are available, including open source options. Examples of the latter include the [[COLOR=#0645ad]Apache[/COLOR]]("http://ubuntuforums.org/wiki/Apache_HTTP_Server") web server's mod_proxy_balancer extension and the [[COLOR=#0645ad]Pound[/COLOR]]("http://ubuntuforums.org/wiki/Pound_(networking)") reverse proxy and load balancer.
 
I'm not sure mod_proxy_balancer does what we need either.
 
[Edit: I think that we're getting close though. I think running a Reverse Proxy as described [here]("http://www.apachetutor.org/admin/reverseproxies") might do the trick. I'll have to try it out tonight and see if it does the trick for me.]

---

