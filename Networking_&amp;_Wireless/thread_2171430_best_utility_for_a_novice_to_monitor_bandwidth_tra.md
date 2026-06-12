---
title: "best utility for a novice to monitor bandwidth traffic on my network?"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by nick34 on 2013-08-30
Hi,   The situation is that I let my neighbors across the street (~125 yds) use my wifi because he mows my grass for me :p. He has some sort of netgear range booster that picks up my wifi signal in the corner of his house and then rebroadcasts it through his house. It appears to show up as another network named something like MyNetworkName_Ext2 and that is what he connects to, but with the same password used to get on my router's wifi. There is currently only one computer connected to my router and is connected by wire, so they are the only ones actually using the wifi.   What I am wanting is a utility to track the bandwidth usage of everyone individually so that I can make sure they aren't putting too much of a strain on my little 4mb connection. A GUI utility to begin with would be nice, but I am willing, and eventually want, to learn a CLI tool if necessary as the ultimate goal here is to increase my knowledge of network administration and the tools for it.   If there is any other information/documentation or tools that would be relevant or helpful to someone who wants to begin learning more about linux network administration that would be very much appreciated as well. I'm comfortable with the CLI and enthusiastic about learning to use more CLI tools.   Thanks very much.

---

### Post by houstonbofh on 2013-08-30
Cacti is a very nice tool for this, and is in the repositories.  It is kind of the industry standard for bandwidth monitoring and historical trending.

---

### Post by SeijiSensei on 2013-08-30
It sounds to me like your neighbor's connection goes straight into your router.  If so, the only place you can monitor it is on the router itself.  To do what you want to do, you would need to have two routers, one between you and the Internet, and one between you and your neighbor.  Then you could put a Linux box between the routers and using something like **ntop** to monitor traffic.  

I'd also consider identifying your neighbor's MAC address and telling your router to assign it a predesignated IP.

If your router supports some Linux-based software like dd-wrt or Tomato, you might want to see whether one of those provides the kinds of monitoring tools you need without any extra configuration required.  If so, you could reflash your router with the alternative firmware.  I use dd-wrt on my ASUS router; installation was pretty much a no-brainer.

---

### Post by nick34 on 2013-08-31
Thanks for the replies! 

> **SeijiSensei said:**
> It sounds to me like your neighbor's connection goes straight into your router.  If so, the only place you can monitor it is on the router itself.  To do what you want to do, you would need to have two routers, one between you and the Internet, and one between you and your neighbor.  Then you could put a Linux box between the routers and using something like **ntop** to monitor traffic.  

I'd also consider identifying your neighbor's MAC address and telling your router to assign it a predesignated IP.

If your router supports some Linux-based software like dd-wrt or Tomato, you might want to see whether one of those provides the kinds of monitoring tools you need without any extra configuration required.  If so, you could reflash your router with the alternative firmware.  I use dd-wrt on my ASUS router; installation was pretty much a no-brainer.

So if I understood correctly: If I want to monitor individual connections to a router, it can only be done *at* the router and not from my computer?

All of the neighbors devices (laptops, ipads, etc) connect first to this range booster and then the range booster connects to my router wirelessly. To monitor all the traffic combined passing through this range booster, I can assign it a predesignated IP that I can then monitor *from my router* (assuming the software is supported), is that correct? 

I'm a little confused at how the range booster works exactly and the network it creates (MyNetwork_Ext2), but I'm pretty positive it's connection to my router is what I want to monitor. (I think this would be even more difficult if all of their devices were connected to my router without the range booster in-between.)

ps. i have a Linksys E3200, I will check to see if it supports that software. 

Thanks for your time, I hope I was able to be clear enough.

---

### Post by SeijiSensei on 2013-08-31
> **nick34 said:**
> So if I understood correctly: If I want to monitor individual connections to a router, it can only be done *at* the router and not from my computer?

Yes, because your computer will never see any of that traffic.  It comes from the neighbor, goes into the router, and on to the Internet.

---

### Post by houstonbofh on 2013-08-31
Every access point I have ever seen supports SNMP.  I am betting that his range booster does as well.  Monitor that with cacti, and you have all his bandwidth.

Otherwise, you have to get some hardware to put in place so that you can monitor that leg.

---

### Post by nick34 on 2013-08-31
Great, thanks for the help guys!

---

