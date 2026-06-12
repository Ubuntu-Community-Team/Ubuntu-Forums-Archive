---
title: "lan speed under 3mb/s"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-12-12
It is a network 100mb/s
The network has 2 wireless routers and 2 PC's, one ubuntu, one windows 7. Both PC have gigabyte type lan cards, however routers are standard 100 ethernet.

Transfer speed seems slow, what do you get?

Is this normal?

---

### Post by Grenage on 2012-12-12
If there is a great deal of tiny files, it can seriously hamper transfer speed.  I'll bet you get much better speeds with a single archive (if only as a test).

---

### Post by irv on 2012-12-12
> **Grenage said:**
> If there is a great deal of tiny files, it can seriously hamper transfer speed.  I'll bet you get much better speeds with a single archive (if only as a test).

Yes, it looks like he has over 9,000 file left and he was halfway so he must be transferring over 18,000 files. It would be much faster with one archive file. From the looks of it I think they are photos so the size would be more then a text file.

EDIT: I forgot to mention, back when I used Windows I noticed that Windows transfers files slower then Linux. There was a big difference in speed as I remember.

---

### Post by irv on 2012-12-12
If you are going to compress your files, this looked interesting. That is if they are .jpg files.
[http://www.webupd8.org/2012/12/batch-lossy-jpg-and-png-compression.html]("http://www.webupd8.org/2012/12/batch-lossy-jpg-and-png-compression.html")

---

### Post by sdowney717 on 2012-12-12
Lots of picture files

Compressing into a single archive speeds up a transfer?

---

### Post by Grenage on 2012-12-12
Well it's usually a toss-up between the time required to archive, send, and extract - and just sending all of the files.

---

### Post by Cheesemill on 2012-12-12
That looks about right for a transfer of thousands of small files.

You must also recognise the difference between bits (b) and bytes (B). Network transfer speeds are usually quoted in bits whereas file sizes are usually quoted in bytes. As there are 8 bits in a byte the absolute maximum theoretical speed on a 100Mb/s network is 100 / 8 = 12.5MB/s. If you take into account the error checking and protocol overhead then you are looking at a maximum speed of around 10MB/s.

As others have mentioned to get the best performance you would need to put all of your files in a single archive, doing this would get you closer to the 10MB/s mark.

---

### Post by irv on 2012-12-12
Maybe one more thing to mention. Router speeds. I have a linksys router and am replacing it today with a Asus router. My new router will be a 1 x Gigabit WAN port router. This will really improve my lan speed.

---

### Post by Cheesemill on 2012-12-12
> **irv said:**
> Maybe one more thing to mention. Router speeds. I have a linksys router and am replacing it today with a Asus router. My new router will be a 1 x Gigabit WAN port router. This will really improve my lan speed.

Not really.

The only situation where this will improve your LAN speed is if you have a file server connected to the single 1000Mb/s port and you are doing simultaneous transfers from several hosts that are plugged into the 100Mb/s ports. You will get no increase in your WAN speed or your transfer speed from single host to single host. Transfer speeds are always limited to the transfer rate of the slowest host.

---

### Post by irv on 2012-12-12
> **Cheesemill said:**
> Not really.

The only situation where this will improve your LAN speed is if you have a file server connected to the single 1000Mb/s port and you are doing simultaneous transfers from several hosts that are plugged into the 100Mb/s ports. You will get no increase in your WAN speed or your transfer speed from single host to single host. Transfer speeds are always limited to the transfer rate of the slowest host.

Yes you are right. Speeds are are as fast as the slowest port. My new router supports Ethernet and 802.3 with max. bit rate 10/100/1000 Mbps. So if I am coming off a 1000 Mbps port and going to a 10 or 100 Mbps port it will only run at 10 or 100 Mbps.

---

### Post by sdowney717 on 2012-12-12
I use cat5e cable.
If I got 2 gigabyte routers, would the lan speed up?

Are the Lan ports on gigabyte routers all gigabyte or do they cheat you?

---

### Post by Cheesemill on 2012-12-12
> **sdowney717 said:**
> Are the Lan ports on gigabyte routers all gigabyte or do they cheat you?

You would have to look at the specs of your router to be sure.

There is a current trend for routers to have 4 x LAN ports, with only one of them being a 1Gb/s port (my current BT Home Hub included). For most users this makes no sense whatsoever, you will see no increase in speeds compared to a router with 4 x 100Mb/s ports. I'm not sure what the reasoning behind this is but it's probably purely marketing (they can now put Gigabit on the packaging somewhere).

Personally I have a cheap Netgear 8 x 1000Mb/s unmanaged switch in my home network so that all of my machines can connect to each other at Gigabit speeds.

PS - I think you meant Gigabit not Gigabyte, there is no such thing as a Gigabyte router.

---

### Post by Grenage on 2012-12-12
Indeed, it's generally better performance to have a separate switch connected to the router - although that does require another power socket.  Most home routers are bloody awful at handling large data loads, especially when they are simultaneous and between multiple hosts.

Oddly enough, I have seen some routers marketed as 'gigabyte', most likely just to hedge their marketing bets.

---

### Post by Cheesemill on 2012-12-12
> **Grenage said:**
> Oddly enough, I have seen some routers marketed as 'gigabyte', most likely just to hedge their marketing bets.

Unless they were actually manufactured by Gigabyte (TM) :)

I agree about most home routers being shoddy though, every time I try and run Nessus against one of my remote servers from home my BT Home Hub simply falls over and goes into a reboot loop until I unplug it from the mains.

---

### Post by irv on 2012-12-12
I read a lot of reviews on routers and finally got this one. Like I said, it is due to arrive today.
[http://www.amazon.com/gp/product/B008ABOJKS/ref=oh_details_o02_s00_i00]("http://www.amazon.com/gp/product/B008ABOJKS/ref=oh_details_o02_s00_i00")

EDIT: I think I am going to like the AiCloud and the two USB ports on this router for Network HD and printing.

---

### Post by Cheesemill on 2012-12-12
That looks like a good home router.

The Gigabit WAN port is pretty irrelevant unless you have a fibre connection directly to your home, but it does have a built in 4 x 1000Mb/s switch so you should see a transfer rate between your machines of up to around 100MB/s.

---

### Post by irv on 2012-12-12
> **Cheesemill said:**
> That looks like a good home router.

The Gigabit WAN port is pretty irrelevant unless you have a fibre connection directly to your home, but it does have a built in 4 x 1000Mb/s switch so you should see a transfer rate between your machines of up to around 100MB/s.

I do have fiber coming into my house. The whole town is wired with fiber. I do have a fast Internet on the wire
[ATTACH]228596[/ATTACH]

---

### Post by sdowney717 on 2012-12-12
I downloaded and ran lanspeedtest. This writes and reads a 20mb file onto a LAN pc.

I have 2 lans joined with static route, so it is going from win7 pc to router to router to ubuntu pc.

How do the results look to you?

---

