---
title: "home networking headache"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by infoburner on 2005-12-22
I dont know if this is the right place to ask this question but here goes. 
Please forgive my stupid questions:

I have a friend who had an esoft ex2 firewall connected to his broadband modem and a cisco switch. well, the ex2 is now fried. he has a back-up linksys router, I dont know what model but its one of the cheaper ones. 

the problem is that he doesnt want to connect all of his computers to the linksys because he says it cant handle the load. He says that it is 100BaseT, but if he is transfering files between many computers, they have to share the total 100BaseT. As in if there were two pairs of boxes transfering files, each pair would get 50 Mbits/sec of the available bandwidth. 

Question #1 : is he right about that?

if so, I was thinking that maybe I could put the linksys between the modem and the cisco switch, so that all of the computers could be dhclients of the router (or have static IPs for that matter),  but still use the speedy cisco switch amongst themselves. 

Question #2: Would this work like I hope it would?

Thanks very much for any help you can offer!

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=infoburner]I dont know if this is the right place to ask this question but here goes. 
Please forgive my stupid questions:

I have a friend who had an esoft ex2 firewall connected to his broadband modem and a cisco switch. well, the ex2 is now fried. he has a back-up linksys router, I dont know what model but its one of the cheaper ones. 

the problem is that he doesnt want to connect all of his computers to the linksys because he says it cant handle the load. He says that it is 100BaseT, but if he is transfering files between many computers, they have to share the total 100BaseT. As in if there were two pairs of boxes transfering files, each pair would get 50 Mbits/sec of the available bandwidth. 

Question #1 : is he right about that?

if so, I was thinking that maybe I could put the linksys between the modem and the cisco switch, so that all of the computers could be dhclients of the router (or have static IPs for that matter),  but still use the speedy cisco switch amongst themselves. 

Question #2: Would this work like I hope it would?

Thanks very much for any help you can offer![/QUOTE]

Experimentation will probably give you the best answer.

In regards to question #1, the question posed does not entirely make sense to me.  10BaseT, 100BaseT, etc. are measures of data transfer rates for an Ethernet (layer 2).  A router deals with packets at layer 3 (TCP/IP protocol).  That said, let us suppose that the router has 4 PCs hooked up to it as well as the Internet connection.  If each of the PCs is downloading/uploading data to the Internet, the router must inspect each of those packets and track the connections for network address translation (NAT) purposes.  The more data that needs to be inspected, the more work the router has to do.  Eventually, a saturation point will be reached and the router will start discarding packets.

With regards to #2, I don't see any reason this shouldn't work.  The switch works at layer 2, and it lets the Ethernet act as a switched Ethernet.  [http://www.howstuffworks.com]("http://www.howstuffworks.com") has a good explanation or Ethernets, routers, and switches.

---

### Post by djgenesis on 2005-12-23
I think **cwaldbieser** is talking about the differences in a Hub and a Switch. But i don't suppose that linksys is using a hub. The main difference is that the Hub "broadcasts" but the switch "switches" to the appropriate channels. 
Your friend has a point theoretically but in your system this will not make any difference. [This webpage]("http://www.duxcw.com/faq/network/hubsw.htm") explains the basic difference between the two network components clearly. Have a read it'll do you good. 

Regarding the configuration it will work but there is no need to add complexity and more points of failure to your network. The load of 4 to 8 pcs connot be considered heavy enough to be handled by the router. You would implement the architecture you proposed if you had 15-24. 

Genxx

---

### Post by infoburner on 2005-12-23
thanks for the help!

---

