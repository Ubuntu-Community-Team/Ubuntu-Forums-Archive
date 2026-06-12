---
title: "Bsnl broadband:unable to connect via Network Maneger but able via pppoeconf command"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by tadhya on 2013-08-21
Hi,
I am using ubuntu 12.04LTS 32bit with BSNL broadband 500c plan.
My modem is D-LINK DSL-2520U ASDL 2+ Router

I have set my broadband following way via Network Maneger(NM) wizard;
Network connections>DSL>Add
In IPv4 settings tab set method as Automatic(PPPoE) and 
in DSL tab i have entered username and password

[B]Its working for me fine. I click DSL Connection 1 option on NM munu to
connect to the internet.

But for few days I am not able to do this and DSL Connection 1 option
also disappeared from NM.[/B]

I then just follow another way (via pppoeconf in command line) to connect.
I was successful.

**So my question is why I am not able to connect via NM, while via pon dsl-provider command I can connect easily?**

An interesting observation eth0 interface uses IPv6 address instead of IPv4.

**So Why does eth0 interface uses IPv6 address?**

Give me some suggestion to fix these problems?

---

