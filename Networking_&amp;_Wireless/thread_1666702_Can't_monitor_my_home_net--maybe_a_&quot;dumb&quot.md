---
title: "Can't monitor my home net--maybe a &quot;dumb&quot; hub would help?"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by gringo guy on 2011-01-14
Hi all,
I'd like to start experimenting with collecting network stats, but have a router that will not support dd-wrt. Of course, tcpdump and snort only see traffic that gets to my PC. I do have a little hub, so thought that simply connecting everything to that would be equivalent to having a monitor port on the router, but still no go. Then I noticed that this is a "switching" hub which I now realize means it doesn't simply echo all packets to all ports. Never knew there was such a thing--it's been quite a while since doing any serious subnet admin!

So, if my router is too dumb, and my hub is too smart, are there any good alternatives (other than buying a managed switch)? Is it still possible to buy a dumb hub that simply dumps all traffic to all ports? 

Also, is there a way to tell if the NIC on my PC supports promisc mode? After boot, dmesg shows some messages where eth0 enters/leaves/enters promiscuous mode. Does that signify success or simply that attempts were made? (BTW, I did run ifconfig to add promisc to eth0, and it now shows this as running, but can't tell if that just means it's actually supported or merely available IFF the hardware supports it.)
Thanks!

---

### Post by gringo guy on 2011-01-14
If these questions are too stupid to answer, can someone at least tell me *why* they're too stupid? 
Thank you,

---

### Post by dandnsmith on 2011-01-15
I don't think the questions are too dumb - merely outside most peoples experience.
It's been a long time since I contemplated trying what you want to do.

I'm not sure a managed switch would help - might even make it more difficult(by just guaranteeing that traffic will only go one route). You don't say anything about the model of your modem/router, or about the number of ways the switch has to have.
I'd be looking for a 'hub', as this might well not have the problems that the switch has.

I'd say that you may well be able to switch to promiscuous mode, if there are no error messages when you try to do it, but when in that mode I'm not sure that you could both use it as a way of collecting traffic and also 'routing' for the PC.

---

### Post by SpaceTeddy on 2011-01-15
> **gringo guy said:**
> Hi all,
I'd like to start experimenting with collecting network stats, but have a router that will not support dd-wrt. Of course, tcpdump and snort only see traffic that gets to my PC. I do have a little hub, so thought that simply connecting everything to that would be equivalent to having a monitor port on the router, but still no go. Then I noticed that this is a "switching" hub which I now realize means it doesn't simply echo all packets to all ports. Never knew there was such a thing--it's been quite a while since doing any serious subnet admin!

If a hub is switching, it means it remembers where computers are and forward packets direct to them instead of mirroring them onto all ports. There is nothing you can do about this, except, as you said, buy a dumb (!) switch which is blasting packets on all ports. Although, i must admit, the concept of a switching hub seems a little alien to me.

> **gringo guy said:**
> 
So, if my router is too dumb, and my hub is too smart, are there any good alternatives (other than buying a managed switch)? Is it still possible to buy a dumb hub that simply dumps all traffic to all ports?

Well - i'd say you need to buy some hardware for that. When i ran into the problem a while back, i got myself this switch:
```
3COM 3CDSG8 Gigabit managed switch
```
It's 8 port, costs less than 100 bucks and has the capability of a monitoring port - however, it can only monitor ONE port, not all.
That was enough for me, but i do not know if that is enough for you...

The other alternative is to get an older computer, by as many network cards as you have used ports on your home switch and configure it to "act" as a hub bridging the network interfaces together. In this case, you can monitor anything on the computer itself. If course, the most simplistic of all setups in this case having two network cards that are bridged, basically acting as listening device on a cable. 

> **gringo guy said:**
> 
Also, is there a way to tell if the NIC on my PC supports promisc mode? After boot, dmesg shows some messages where eth0 enters/leaves/enters promiscuous mode. Does that signify success or simply that attempts were made? (BTW, I did run ifconfig to add promisc to eth0, and it now shows this as running, but can't tell if that just means it's actually supported or merely available IFF the hardware supports it.)
Thanks!
Let me clarify here - the network card does not care for anything above layer-1 (or should not unless you have fancy stuff like a TCP offload engine or other enhanced capabilities). In the basic scheme, a network card only cares about the physical link. This means, anything received by the network card is handed to the operating system driver. Now, if the driver does some filtering - i do not know. But my strong opinion on the matter is that all drivers should have a promisc mode. However, i am not entirely sure on the matter (yet, i have never had a network card that did not support promisc mode).
On another line of thought - don't you need promisc mode to receive dhcp configuration, leading to the conclusion that a network card (or driver) not supporting promisc mode would not be able to handle DHCP requests and acks ? Again, i am not entirely sure on the issue... 

I hope my rambling are helpful...

---

### Post by CharlesA on 2011-01-15
Good luck finding a "dumb" hub these days, most stuff are switches as they are more efficient then hubs.

You'd be better off either getting a router that works with dd-wrt or finding a switch that does port mirroring.

---

### Post by gringo guy on 2011-01-21
@dandnsmith: Thank you for your suggestions.

@SpaceTeddy: I checked out the switch you recommend. I notice that it's not on the list of dd-wrt supported devices but, for a managed switch, the price is sure good. Also, thanks for your note that only ONE port can be monitored as that's not clear from the description--perhaps if the one port is a hub, switched or otherwise, it might work. Yes, big help. Thank you for your ramblings!

@CharlesA: Okay, thanks. Looks like the decision is which type of router to get: either managed, or supported by dd-wrt. Maybe there's one that fits both categories that isn't hugely expensive. 

This helps a lot. If I get something working, I'll follow up here.
Thanks again!

---

### Post by jroa on 2011-01-21
Can you access the configuration settings of the switching hub?  If so, you may be able to set it up so that everything that passes through it would be echoed to your port.

You might also be able to use another network card, if you can set things up right.  One network card would be connected directly to the internet, the other would be bridged to share the internet access of the first.  Then, you connect your router to the second card.  All data would then be passing through your computer.  I have never done this, but I have heard of others who have.

---

### Post by CharlesA on 2011-01-21
Getting a router you can put on dd-wrt on would probably be the cheaper option.

---

### Post by gringo guy on 2011-01-22
@jroa: The hub is a Linksys EZXS55W and has no config options--you just plug it in and it works. That's a good idea about a 2nd NIC. That occurred to me also, and may be what I will need to do.

I did find an [archived thread]("http://homecommunity.cisco.com/t5/Hubs/Available-Hubs/td-p/321934") where someone asked Cisco about this, but the reply was misleading as the listed hubs are [apparently switching hubs]("http://www.amazon.com/review/R1XBZ2JGQ5POOM/ref=cm_cr_pr_viewpnt#R1XBZ2JGQ5POOM") also.

@CharlesA: Probably quickest as well; however, after reading a little about snort (and reading bodhi.zazzen's [quick start guide]("http://ubuntuforums.org/showthread.php?t=1477696")), my curiosity is now piqued. I'd like to learn more about using NIDS tools.

---

### Post by coding_monkey on 2011-04-16
Gringo did you ever figure out a good solution to this? Since most wired ports are switched and wireless traffic is often encrypted it seems very difficult to monitor network traffic effectively. My router would work with DD-WRT but it was not clear to me how DD-WRT supports monitoring.

---

### Post by CharlesA on 2011-04-16
> **coding_monkey said:**
> Gringo did you ever figure out a good solution to this? Since most wired ports are switched and wireless traffic is often encrypted it seems very difficult to monitor network traffic effectively. My router would work with DD-WRT but it was not clear to me how DD-WRT supports monitoring.
DD-WRT is able to keep a record of how much bandwidth has been used.

If you wanted to read the contents of packets, you'd have to place a machine between the gateway and the internet network.

---

### Post by gringo guy on 2011-04-26
coding_monkey, Good timing with your question: I just bought a [WZR-HP-G300NH]("http://wiki.openwrt.org/toh/buffalo/wzr-hp-g300h") router and am considering using the graphing tools from [Gargoyle]("http://www.gargoyle-router.com/"). Not quite as low-level as I'd hoped, but it will be fine for now--while I spend some time getting familiar with the [many packages]("http://downloads.openwrt.org/backfire/10.03.1-rc4/x86/packages/") available from OpenWRT, and figuring out what I might add or update using OpenWRT's nice cross compiling build environment. 

At some point I may put a PC out in front of the router but, either way, this will be a good first step in that direction and may end up being sufficient.

---

