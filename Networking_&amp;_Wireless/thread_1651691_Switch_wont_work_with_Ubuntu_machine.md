---
title: "Switch wont work with Ubuntu machine"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by CrazeDIzzleD on 2010-12-23
I got a Ubuntu machine running a local web server. It is connected to an archaic 10mbit hub, and I'd like a little bit faster network. I got a new 100/1000mbit switch connected to my router. I have 3 other PC's running off it, no problems at all. No configuration was necessary, and all existing cables worked fine.

Since the router and hub are located at the opposite end of the house, and the switch is in my PC room, I made up a new cable to connect it to my Ubuntu machine. It's just a straight-through cable, just like the other cables connecting the switch to other PC's. Okay so, when I plug the cable in to the machine I get no ethernet lights on either the machine nor the switch. But here's the kicker: I plug the cable into my laptop (running Windows 7), and it works perfectly. I restart the machine with the cable in, and get a green light. As soon as Ubuntu loads up, no lights, no connectivity.

It shouldn't matter, but I'm running a static IP on the machine. I also have static IP's on the other PC's connected to the switch and nothing had to be changed.

So what gives?

---

### Post by dandnsmith on 2010-12-23
Were you saying you plugged the new cable switch to laptop, or server to laptop when it worked?

Have you checked that there is nothing special about the switch port you are using - sometimes they have one designed for switch sequencing which has to have the correct setting  (or a x-over cable).

---

### Post by CrazeDIzzleD on 2010-12-23
I connected my laptop to the switch with the same cable, to verify the cable worked - which it did, with no issues.

The switch uses that fancy auto sense stuff so it doesn't matter which way the cable is. It's not the switch, because the other 3 PC's I have connected work totally fine and I had no issues with them, and they all use straight cables just like the one I made. And, the cable works fine because I tested it with my laptop.

Not sure if it's worth noting, but one of the other 3 PC's I have connected also runs Ubuntu and it connected with no problems.

---

### Post by CharlesA on 2010-12-23
Hi,

Try a different cable.

I've been running Ubuntu off of a Dlink gigabit switch with no problems.

Is the network card seen in Ubuntu?

```
ifconfig
```

---

### Post by CrazeDIzzleD on 2010-12-23
I don't have a different cable. Not that it would make a difference, the cable is functioning perfectly fine. And so is the network card, because it connects with no issues to my old hub.

---

### Post by CharlesA on 2010-12-23
Just a note: A 10Mbps and 100Mbps switch uses 2 pairs, a 1000MBps uses 4 pairs on CAT5.

If one of those wires are shorted or open, it won't work.

---

### Post by oldsoundguy on 2010-12-23
have you checked your network card? Just a thought.  I have had several WIRELESS NIC's and one hard wired on board NIC go south over the last couple of months.
(NOT a clue as to why! ... when newer cards were installed, everything worked again.)

---

### Post by CrazeDIzzleD on 2010-12-23
> **CharlesA said:**
> Just a note: A 10Mbps and 100Mbps switch uses 2 pairs, a 1000MBps uses 4 pairs on CAT5.

If one of those wires are shorted or open, it won't work.

My laptop has a gigabit LAN, and using that cable, it connects at 1Gbps and is fully functional.

@oldsoundguy: Again, my machine works with no issues at all when connecting to my hub, as it has been connected with for over a year now. 

Out of curiosity, is there a way in Ubuntu to force the NIC to run at 10mbps?

---

### Post by bkratz on 2010-12-23
In the terminal type

man iwconfig 

and look at the section about bit rates

---

### Post by CrazeDIzzleD on 2010-12-24
> **bkratz said:**
> In the terminal type

man iwconfig 

and look at the section about bit rates

Not sure what this is supposed to be doing, but I don't see anything about bitrates. And is this for wireless? I don't have wireless.

---

### Post by lisati on 2010-12-24
How have you assigned the static IP addresses? I'm wondering if there's a conflict somewhere that you haven't yet picked up. My personal preference is to let my router(s) handle the allocation of IP addresses, including static addresses when needed.

---

### Post by CrazeDIzzleD on 2010-12-26
What do you mean how? I'm only aware of one way.

I changed manually set my IP in the IPv4 settings, and used my router as the gateway. The switch doesn't change anything with static IP's so I don't know why there would be any difference. All of my other PC's that use the switch also have static IP's.

---

### Post by dandnsmith on 2010-12-27
That looks like how I set mine up.

One more point about cables - I've had a mystifying occurrence of a cable not working with a particular PC, which was particularly awkward as the cable was routed through a tricky loft space.
Reluctantly I got another long cable tested it with the PC, and then threaded it (and removed the other). The new cable continued to work.
Now comes the crunch: the 'presumed faulty' cable has since always worked at a different site with several different PCs.
Moral - don't rule out the possibility that it may be the combination of cable and PC which is the problem (connector mismatch?).

---

