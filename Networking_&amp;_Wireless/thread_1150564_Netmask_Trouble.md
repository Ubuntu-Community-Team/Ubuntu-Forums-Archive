---
title: "Netmask Trouble"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Sum Guy on 2009-05-06
I am currently using a DSL-G604T router to connect to the net. Through trial and error, and other info here on the forums I have discovered the difficulty in connecting through Ubuntu is a flaw in the router's DHCP server. I have tried setting a static IP address but for some reason when I input the netmask (255.0.0.0) it changes into an 8, and won't connect. Any help will be appreciated greatly.

---

### Post by tricolorpoa on 2009-05-06
Man,

The network address:10.1.1.0 with a netmask 255.0.0.0 is the same of 10.1.1.1/8

What's the problem with your connection?

---

### Post by Sum Guy on 2009-05-06
The router doesn't connect to Ubuntu through wireless without first connecting through a wire, with static or DHCP addressing. The connection goes through fine if I use a wire and then get a wireless connection. The 2 connections must overlap to connect. Note the router is a G604T, which has had a bad reputation in the past, although one person successfully connected through an unsecured network on one. I am now using no security with hardware address exclusion, which allowed the previously mentioned connection, but didn't correct the entire problem. Anyone have a solution?

---

### Post by tricolorpoa on 2009-05-06
Sorry..

I can't understand what do you really want!

---

### Post by Sum Guy on 2009-05-07
i need to find a way of getting an address without plugging the laptop into the router first.

thanks for the input so far btw.

---

