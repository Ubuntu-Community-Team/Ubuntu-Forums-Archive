---
title: "Terrible wireless connection (network issue, not OS)"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by Exershio on 2012-09-08
This is a general issue with my network, not Ubuntu. But I run Ubuntu, so I figured it could go here.

I recently moved to a more congested area and since then my wireless connectivity really sucks. I have absolutely 0 issues with my wired connection. I have RR Lightning and get consistent 41mbps down / 5mbps up with wired.

However, my wireless connections, even when relatively close (one room away) drop constantly, and never get more than 10-15mbps download. I've tried moving the router to a higher position such as on top of my dresser, but it doesn't help. It's a small apartment so it shouldn't be giving me issues. The devices usually get 4-5 bars but it still drops often (sometimes every 5 minutes).

I live in a college neighborhood with like 15 networks that I can pick up on and off, so I was thinking it might be severe interference. Is there anything I can do about this? I have considered purchasing a bigger antenna/signal booster but I'm not sure what ones to look at.

I had a Ubee DOCSIS 3.0 router/modem with 2 antennas (i forgot the model), and replaced it with a motorola SBG6580 (which has no external antenna), but I'm going back to the ubee router in a couple days so I'll be able to hook up an alternative antenna 

Any help would be appreciated, thanks!

---

### Post by kurt18947 on 2012-09-09
You could try changing wifi channels which shouldn't be a huge undertaking.  It's done in the router, often in the wireless settings page.  Machines are different and I don't have any experience with your routers but some poking around might uncover the relevant settings page.  If there are a number of access points using the same channel along with other 2.4 ghz. devices that could cause problems I'd suspect.  If you're getting 4 or 5 bars I'm somewhat doubtful a new antenna will help.  You may have a situation sort of like an AM radio station in an area with lots of overhead electrical wires;  it's plenty 'loud'(good signal strength) but the main thing you can hear is static.  Just speculating though.

---

### Post by dandnsmith on 2012-09-09
It sounds like the obvious solutions have already been explored.
Are you (Exershio) using 2.5G, 5G or dual band? The 5G is reputed to be less able to cope with obstacles, but then a lot of kit is using 2.4G.
I've used Inssider to explore the channels in use and on which band (I'm afraid I don't know the Linux equivalent, despite having seen one mentioned) - and this helps to pick a less-occupied channel.

People have posted about using reflectors to create a more directional 'beam' - these can be for both transmitter and receiver.

I think that, by now, I'd be using a net cable - especial since you say 'one room away' and 'a small apartment'

I suppose that you should also explore the possibilities of very local interference: switching PSUs, digital phones ...

Good luck in your quest

---

### Post by troffasky on 2012-09-09
> **Exershio said:**
>  Is there anything I can do about this?

You haven't mentioned what band you're using so I'm going to assume it's 2.4GHz. There are only three non-overlapping on the 2.4GHz band:

[http://en.wikipedia.org/wiki/File:NonOverlappingChannels2.4GHzWLAN-en.svg](http://en.wikipedia.org/wiki/File:NonOverlappingChannels2.4GHzWLAN-en.svg)

compared with more that 20 on 5GHz, so your chances of finding some free spectrum to use are much better at 5GHz [not to mention that there are also many non-wifi users on 2.4GHz that won't even show up in a list of wireless networks]. My suggestion to you would be to get a 5GHz [or dual-band] access point and a compatible wireless adaptor for your client devices [where applicable]. If you have any devices that are 2.4GHz only, then you'll have to run both and live with the fact that 2.4GHz-only devices won't perform as well

> **Exershio said:**
> I have considered purchasing a bigger antenna/signal booster but I'm not sure what ones to look at

Your problem, from the limited information I have, is that you and your neighbours networks are talking over each other. Amplifying things is only ever going to make the problem worse.

Actually, one thing you could try before giving up on 2.4GHz is making things a bit more directional; that way, your AP hears more of your clients and less of the neighbours, and vice versa. To quote this page about corner reflectors:

[http://www.freeantennas.com/projects/Ez-10/](http://www.freeantennas.com/projects/Ez-10/)

"...this antenna is so easy to make, tune, and install, and it performs so well that it is foolish not to try one..."

---

### Post by Exershio on 2012-09-10
Thanks for the input everyone. I attached a screenshot of a wifi inspector running from my gf's laptop one/two rooms away. It shows about -40 dBm when I'm in the same room as the router, and between -68/-78dBm when I'm in another room (not very far away either). Every now and then a network pops up on the inspector with a -10dBm signal, but it's not frequently and disappears fast, and I didn't manage to get a screenshot of it. Either way I found that odd.

My network is at the top of the list, Skynet.

At this point I'm considering just wiring up everything. I just don't want 4 wires running around everywhere since I have a few devices. This is really an issue because everything is extremely unstable. I cannot play online games or watch netflix on my PS3 without it cutting out every other minute.

---

### Post by dandnsmith on 2012-09-11
That pic shows a lot of demand locally - worst thing is that a lot of is 11n, which means it'll spread over a wider bandwidth and occupy more channels.

How about doing ethernet over the mains wiring - costs a bit, but would save some of the trailing cables?

---

