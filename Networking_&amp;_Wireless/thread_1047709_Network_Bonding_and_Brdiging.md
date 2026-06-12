---
title: "Network Bonding and Brdiging"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by ilukester on 2009-01-22
Hi I have been reading alot about how to bond a network connection but I was wondering if there was a way to bond the connection and make it a "pass through" connection? I drew up a basic diagram of how my setup looks like. Dont worry the IP's are not real, but my ips do come off the same gateway. Can anyone put in me in the right direction. Has anyone else ever done this before?

---

### Post by chrisgibbs on 2009-01-23
Speaking to ilukestar on #ubunut, I suggested looking at vyatta as a potential solution.

Open source routing platform.

[http://www2.vyatta.com/s.nl/ctype.KB/it.I/id.17181/KB.424/.f](http://www2.vyatta.com/s.nl/ctype.KB/it.I/id.17181/KB.424/.f)

Cheers

Chris

---

### Post by Vesperatus on 2009-01-23
Once you connection is bonded, I don't see why you couldn't nat everything through it.  You will end up with an interface bond0 on one side and probably eth3 on the other. If you managed to bond it, I would suggest installing fwbuilder, a graphical interface to create firewalls. 

By the way, the internet looks awesome in your diagram.

---

### Post by ilukester on 2009-01-23
> By the way, the internet looks awesome in your diagram.
I'm 18. What more do you expect? ;)

I have used ifenslave to bond the connection. I will give that firewall a try and see if it will allow me to use the bond as a transparent connection.

---

### Post by Vesperatus on 2009-01-23
> **ilukester said:**
> I'm 18. What more do you expect? ;)

I have used ifenslave to bond the connection. I will give that firewall a try and see if it will allow me to use the bond as a transparent connection.

In firewall builder, you can use templates to create your firewall. You will want to try the one that allows you to share the connection, 1 host with 2 network cards, one facing the internet and another one facing the internal network. From there, it should be pretty straightforward. Just let us know if you have questions.

---

### Post by ilukester on 2009-02-06
Okay guys,

So.... I got the bridge to work just fine without assigning ips... basically i set the bridge to manual and told it to bridge bond0 eth0(my internal network).

Now my problem is that i can't have have the bond going and the bridge at the same time... anyone have any ideas... I can get the bond to work if i only have one connection into the bonded ports, but as soon as i add the second line the network fails and traffic goes down to a halt.

---

### Post by redmk2 on 2009-02-06
> Now my problem is that i can't have have the bond going and the bridge at the same time... anyone have any ideas... I can get the bond to work if i only have one connection into the bonded ports, but as soon as i add the second line the network fails and traffic goes down to a halt.

I believe this is due to your creation of a routing loop.  This causes the Spaning Tree Protocol to disable one of the legs to prevent looping.

I'm not sure what you are attempting to do.  My initial thought is that *[COLOR="RoyalBlue"]ifenslave[/COLOR]* does not do what you expect it to.  It is for load balancing and as such it is is 2 separate connections managed as one. If you had 2 web servers or needed 2 firewalls I could see the use of *[COLOR="RoyalBlue"]ifenslave[/COLOR]* inbound.

On the other hand why are you trying to bridge the interfaces in the Ubuntu box.  What is the Ubuntu box for?  Why is the firewall **[COLOR="Red"]after[/COLOR]** the Ubuntu box?

Bottom Line: The Spanning Tree Protocol (SPT) won't let you do harm to yourself and therefore won't allow you to do what you [think you] want to do.

---

### Post by ilukester on 2009-02-06
> **redmk2 said:**
> I believe this is due to your creation of a routing loop.  This causes the Spaning Tree Protocol to disable one of the legs to prevent looping.

I'm not sure what you are attempting to do.  My initial thought is that *[COLOR="RoyalBlue"]ifenslave[/COLOR]* does not do what you expect it to.  It is for load balancing and as such it is is 2 separate connections managed as one. If you had 2 web servers or needed 2 firewalls I could see the use of *[COLOR="RoyalBlue"]ifenslave[/COLOR]* inbound.

On the other hand why are you trying to bridge the interfaces in the Ubuntu box.  What is the Ubuntu box for?  Why is the firewall **[COLOR="Red"]after[/COLOR]** the Ubuntu box?

Bottom Line: The Spanning Tree Protocol (SPT) won't let you do harm to yourself and therefore won't allow you to do what you [think you] want to do.
Well i think i want to bond two Internet connections into one and then bridge that bond over to my cisco asa firewall/router. All the I want the Ubuntu box to do is to bond and pass all the traffic out the other end... I am trying to do a network load balancing.

---

### Post by redmk2 on 2009-02-06
I don't think you will be able to do that.  The bond creates a routing loop and SPT won't allow it.  You should not allow loops in your network design.

Edit:  See:
[http://en.wikipedia.org/wiki/Spanning_tree_protocol]("http://en.wikipedia.org/wiki/Spanning_tree_protocol")

and 
[http://www.cisco.com/univercd/cc/td/doc/product/rtrmgmt/sw_ntman/cwsimain/cwsi2/cwsiug2/vlan2/stpapp.htm]("http://www.cisco.com/univercd/cc/td/doc/product/rtrmgmt/sw_ntman/cwsimain/cwsi2/cwsiug2/vlan2/stpapp.htm")

Edit2: Understand that this is not an TCP/IP problem (layer 3/4).  It is a Layer 2 (Ethernet) Problem.  Bridges use MAC addresses for identification of the interface.

---

### Post by ilukester on 2009-02-09
So.... after some extensive testing. I have found that the bond does work, but not the way i am wanting it to. So i put my bonding mode into mode 4... and i put my ip as 74.251.55.20... and the internet worked fine but i was only getting as much speed as if i was on one circuit. so i pulled ifconfig and it showed that all the traffic was going threw eth1, i then changed my ip to 74.251.55.60 and all the traffic went threw the other port.... so does anyone know how to truely bond these two lines??? any help?

---

### Post by Vesperatus on 2009-02-09
When I bond my network cards, I use mode 2, wich seems to share the bandwidth.

Regarding modes, I think you are reffering to this :     

> IEEE 802.3ad Dynamic link aggregation.  Creates aggregation groups that share the same speed and duplex settings.  Utilizes all slaves in the active aggregator according to the 802.3ad specification.

While i'm refering to this : 

> 
XOR policy: Transmit based on the selected transmit hash policy.  The default policy is a simple [(source MAC address XOR'd with destination MAC address) modulo slave count].  Alternate transmit policies may be     selected via the xmit_hash_policy option, described below. This mode provides load balancing and fault tolerance.


Yours will only provide fault tolerance. Mine will provide fault and load balancing ( Well, I think :) ) Let me know how it goes.

---

### Post by ilukester on 2009-02-16
Hey guys I really need to finish up this project. I know it is possiable. I tested out some company's producted and it worked flawlessly but I am not going to pay no 3500 for a box that i know can be done in linux. Please guys. I need your help.

---

### Post by Vesperatus on 2009-02-16
You said you used mode 4. Did you tried using mode 2 has I suggested ?

---

### Post by ilukester on 2009-02-16
No i haven't tired mode 2 because you said that it would only provide fault tolerance... but i will try it as soon as i can.

---

### Post by Vesperatus on 2009-02-16
> **Vesperatus said:**
> 
While i'm refering to this : 

Yours will only provide fault tolerance. **Mine will provide fault and load balancing** ( Well, I think :) ) Let me know how it goes.

I quoted myself and put the important part in bold ;)

Let me know how it goes !

---

### Post by ilukester on 2009-02-28
Well sorry about the long delay. I have been studying for a few mid terms and finally got alittle break. Bond mode 2 only provides me with failover. :(

---

### Post by Vesperatus on 2009-03-01
Well, I'm out of options now. 

I used mode 2 for that purpose ?!

Did you restart network services, etc ?

---

### Post by ilukester on 2009-03-01
Yes. :(

---

### Post by Saghaulor on 2009-04-03
Have you tried this?

[http://ubuntuforums.org/showthread.php?t=1029811&highlight=bonding](http://ubuntuforums.org/showthread.php?t=1029811&highlight=bonding)

I'm not sure that it is what you're looking to do, but I figure I would try to help.

Please let us know how it goes or how it went, your feedback can help us all.

---

### Post by Replica2009 on 2011-05-03
Are you trying to do simple load balancing, or true bonding? If the latter, you may need a router that has broadband bonding features. We have one in our office and works great.

---

