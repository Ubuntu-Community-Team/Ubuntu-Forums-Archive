---
title: "Good ubuntu routing guide?"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2009-10-14
Ohai!

I want to see if I can route my connection directly to my netbook directly via an Ethernet cable. I have absolutely no need for it, but, my Ethernet cable was just lying around, all sad, and needed a job. Pretend the router end's connection is through wlan0 and the connection that the netbook is recieving is through eth0. So:

Router recieves signal through wlan0
|
Sends out through eth0 - netbook receives through eth0

Okay, is there a nice package for this, or is the best way for me to get down and dirty with the terminal :3.

---

### Post by yknivag on 2009-10-15
Your diagram suggests you're trying to do something like this:

--Incoming WiFi-->[Router]--cable-->[Netbook]

As your Netbook only has one connection then all routes point down the cable to the router. Any config would need to happen in the router.

How you did this would depend on what you were trying to achieve, where the "incoming WiFi" was coming from and what type of router you have.

---

### Post by dragos240 on 2009-10-15
> **yknivag said:**
> Your diagram suggests you're trying to do something like this:

--Incoming WiFi-->[Router]--cable-->[Netbook]

As your Netbook only has one connection then all routes point down the cable to the router. Any config would need to happen in the router.

How you did this would depend on what you were trying to achieve, where the "incoming WiFi" was coming from and what type of router you have.


Well, My "router" is my computer, and my netbook has more than 1 connecton. I want to direct the signal I'm getting to my netbook, as if I was plugging it into my router.

---

