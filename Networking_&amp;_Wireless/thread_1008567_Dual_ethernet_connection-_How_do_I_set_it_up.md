---
title: "Dual ethernet connection- How do I set it up?"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by moniker127 on 2008-12-11
Well, this is my first post outside the absolute beginner talk section, so i'm excited. :D

Heres my deal.
I have two comcast modems.
I have two ethernet cables.
I have two ethernet ports on my motherboard.
I have an asus p5q deluxe. 
I want to double my bandwidth.
U - Tell me if this is possible

I'd really like a link to a program or something, too, if you have one.

---

### Post by rhcm123 on 2008-12-11
> **moniker127 said:**
> Well, this is my first post outside the absolute beginner talk section, so i'm excited. :D

Heres my deal.
I have two comcast modems.
I have two ethernet cables.
I have two ethernet ports on my motherboard.
I have an asus p5q deluxe. 
I want to double my bandwidth.
U - Tell me if this is possible

I'd really like a link to a program or something, too, if you have one.

I know this is possible, but you have to team the network cards, which i am not aware of how to do... I would actually be interested in this too...

---

### Post by jonobr on 2008-12-11
hey welcome to the big time ):P  :p

I recall in the days of ISDN, we used to have two digital lines from the provider delivered to the home.
You could bond the two channels together to do dialup type connections, it was called Multilink PPP.
PPP was the dialup protocol used.
This would double your bandwidth by combining the two channels, so when you do downloads or speeds tests it would reflect accordingly.

You could also actually bond multiple channels together which companies do.
Ie if the have a T1 line with a few channels (say 8 ) your bandwidth would increase to roughly 8 * 64k.

However, heres the rub with the technology then, the ISP equipment end needs to be involved to understand that you are not only using multiple channels, but that you are bonding the bandwidth,
this required intelligence in the provider terminating device.

Im not  sure if that is true for the cable technology today but I would imagine its the same,
I think you would have to treat both "tunnels' as separate entities and treat them accordingly, i.e. not treating it as aggregated bandwidth, but two operate pipes and splitting the load accordingly.

I am however open to correction by all and curious and will look around to see if there is anything out there that may do this

---

### Post by jonobr on 2008-12-11
Hi, 

Just doing a quick squint aroung the internet,
I notice a few business trying aggregation using cable as opposed to buying expensive lines from their telco.,

The solutions seemded to resolve around expensive routers, and some suggested doing fancy load balancing.

Load balancing is different from aggregation in that you are splitting the traffic up depending on how busy one lan or connection is.

That may be a cheap mans way to resolving your issue,
if you type in ubuntu load balancing you should see some posts on this topic

---

### Post by moniker127 on 2008-12-11
> **jonobr said:**
> Hi, 

Just doing a quick squint aroung the internet,
I notice a few business trying aggregation using cable as opposed to buying expensive lines from their telco.,

The solutions seemded to resolve around expensive routers, and some suggested doing fancy load balancing.

Load balancing is different from aggregation in that you are splitting the traffic up depending on how busy one lan or connection is.

That may be a cheap mans way to resolving your issue,
if you type in ubuntu load balancing you should see some posts on this topic

Aggregation = 2 modems pulling full capacity at once?
I dont know what aggregation means in this sense.
Load balancing does not sound like its what im after, if its what I think your describing it as, because then it would be equivelent to one modem pulling full bandwidth, where as I want two or more. 

It would also be handy if the two connections could be connected to one remote server at once and interact with the same file downloading, but splitting the two up line cores would be cool too. 

It should be possible somehow. If i plug one modem into one computer I get 1 meg / sec. If i plug two modems into two computers I can get 2 megs / sec. So if I plug two modems into one computer, I really dont see why it shouldnt be 2 megs / sec, unless the cable i'm pulling off of simply cant carry that much data, but I dont think thats the case, because even if I use a splitter to make it into two, and hook it up to seperate computers, they still get 1 meg / sec each.

---

### Post by rhcm123 on 2008-12-12
> **moniker127 said:**
> Aggregation = 2 modems pulling full capacity at once?
I dont know what aggregation means in this sense.
Load balancing does not sound like its what im after, if its what I think your describing it as, because then it would be equivelent to one modem pulling full bandwidth, where as I want two or more. 

It would also be handy if the two connections could be connected to one remote server at once and interact with the same file downloading, but splitting the two up line cores would be cool too. 

It should be possible somehow. If i plug one modem into one computer I get 1 meg / sec. If i plug two modems into two computers I can get 2 megs / sec. So if I plug two modems into one computer, I really dont see why it shouldnt be 2 megs / sec, unless the cable i'm pulling off of simply cant carry that much data, but I dont think thats the case, because even if I use a splitter to make it into two, and hook it up to seperate computers, they still get 1 meg / sec each.

It's more a problem of the computers being able to see the fact that they can connect to a remote server at the same time through both network cards and download files. I don't think there is any program to do this.

---

### Post by inxygnuu on 2008-12-12
This would be neat to do... I think that in Ubuntu, where the network manager is located, and it asks you what connection you want to use, you have to find a way to choose both, and have it split the bandwidth. that is all I know. Some kind of software would help you do this.

---

### Post by telecomando on 2009-05-13
You can't do this with 2 cable modems.
You can do this with a T1 line and it is called BONDING.  1 IP shared across multiple T1 connections and is very expensive and has to come from your ISP. Verizon, ATT, Speakeasy anyone who provides T1's can do this.
With 2 cable modems you are going to have 2 IP addresses.  There is no way to bond that.
The only thing you could do is LOAD BALANCING.  Where you have a router in place that balances the traffic across the 2 connections.  So if you have 2 5Mb connections and you balance them you'd still have 2 5Mb connections, not 1 10Mb connection. This is helpful when you have a lot of users behind on one network, they all would get decent speed but no one would get anything faster than 5Mb and traffic would be spread across the 2 internet connections.  PFSense firewall can do this if you really want it but it will be of no benefit if it is only 1 computer behind the router.  But there are other problems that come with this that you would have to deal with.  HTTPS Sessions and other secure channels that might get confused seeing traffic come from a different IP then where it originated from.
But that's a whole other discussion.

---

### Post by nutrapi on 2011-01-12
Not only can you do it, but you can buy devices that do dual wan with loadbalancing and failover for you:
[Linksys RV042]("http://www.google.com/products/catalog?oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&q=RV042&um=1&ie=UTF-8&cid=7589159761057610975&ei=qB4uTe20D9DSgQen0PiyDA&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CDcQ8wIwAg#")

---

### Post by zsa on 2011-02-09
You can absolutely combine 2 cable modems.
You need a router-type of appliance where you plug in the internet sources and it actually aggregates them together to get the combined bandwidth.

I read about one in a press release called Mushroom Networks and I'm trying to learn more about it. I was at their site and saw that they have a bunch of technology awards so they definitely are doing something new... not just the same old load balancing.

If you've tried them out, let me know.

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---

