---
title: "Wireless stopped connecting to networks... sometimes"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by sdlyr8 on 2011-04-06
I've had ubuntu 10.10 installed on my Dell XPS m1530 for 6 months or so. Starting just this week, it stopped connecting to some wireless networks. Mainly, the wireless on my campus. Yet I can go home and connect to my wireless just fine. It also wouldn't connect to the wireless network at my work. It seemed hit or miss at work and would sometimes work, but on campus it doesn't work at all anymore. I don't believe I updated anything before it started giving me this problem. 

Anyone have any suggestions to fixing this pain in the a** problem or anything to try?

---

### Post by sdlyr8 on 2011-04-06
Also, what I mean by "it doesn't work" is that it displays all the wireless networks like normal, but when I try to connect, the wifi bars count up like it's normally trying to connect to a network, but then just fails after a minute

---

### Post by jnorthr on 2011-04-06
wireless networks are prone to problems when they are placed at points of interference with other electrical/electronic devices in their vicinity. Some structural barriers like metal or steel in the walls can block/reflect these signals. Try to reposition your devices to be more in 'line-of-site' with your router. just a thought ... 8-[

---

### Post by sdlyr8 on 2011-04-07
I doubt it's that. I sit in the same spot every day, and I've tried multiple different areas on campus trying different positions. nothing helps. thanks for the suggestion though!

---

### Post by sdlyr8 on 2011-04-07
UPDATE: I talked to the IT desk at my school, and they said that they can see the laptop logging into the network but I just can't establish an IP. 

Also, something else I though of... I have been playing around with some network hacking (arpspoofing & WEP cracking) in my free time just because I like playing around with things like that (not doing anything illegal, I promise). Would any of those setup steps have messed anything up with my wireless? Just a thought.

---

### Post by paccc on 2011-04-07
Sounds like my problem with my router,
the pc conneting and stalled after 1 minute, but logs on router showed:

Authenticating...
Authentication success
DHCP lease ip 192.168.0.101 to pc
DHCP lease ip 192.168.0.101 to pc
DHCP lease ip 192.168.0.101 to pc

only one thing after looking  - all the dates were in 2002, my router hadn't updated the time
so I guess the DHCP leases went old before they reached my pc :) (worked in windows though)

I managed to set the time approximately and get it running,
maybe you should check summertime settings? But I guess it only shows there can be many problems...

---

