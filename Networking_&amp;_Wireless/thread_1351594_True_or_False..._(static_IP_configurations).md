---
title: "True or False... (static IP configurations)"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-10
If I set a static IP in the network interface file, do I need a connection to an actual switch/network device to actually utilize that static IP?

Reason I ask is, previously when setting up Ubuntu based imaging servers with FOG to image Windows machines I would just edit the network interface file to give it a static IP accordingly. In the past, this worked great, so then I can access the web based GUI without even needing a connection to a switch.

I recently switched to Kubuntu and this was not the case, however it's easy enough to have a static IP set in network manager and just plug in to a switch to therefore utilize that IP for the web based GUI.

Well, I didn't have a Kubuntu CD and I had to set up two more imaging laptops for temporary usage, so I went to Ubuntu. I set both up identically. Both were the exact same hardware, brand new E6500 Latitude's from Dell. One had the IP with Ubuntu, even when not connected to the switch, while the other did not respond like that. The other one responded like Kubuntu did when I tried the same thing.

So, more or less, when I set a static IP in the network interface file, MUST I be connected to a switch or network device to "use" that IP address?

---

### Post by gordintoronto on 2009-12-11
Is this right? You have a stand-alone PC running Ubuntu, and you want to refer to an IP address in your browser?

Have you explored the word "localhost"?  I think it means you don't need an IP address.

---

### Post by Roasted on 2009-12-11
Yeah. About that... after I posted this, my buddy suggested it to me. And uh, it worked. Duur. Thanks!

---

### Post by Roasted on 2009-12-11
Okay, so you know how I said that worked? It worked in Kubuntu differently than Ubuntu.

3 laptops - all E5500s - all identical hardware - two on Ubuntu 9.04 - one on Kubuntu 9.10.

I assigned a static IP to the wired network interface and assigned their home page to the loopback IP so I could access the web interface of the software I was using.

With Kubuntu, I did NOT need to be plugged into my LAN switch to access the loopback IP web gui.
With Ubuntu (both laptops), I DID have to be plugged into my LAN switch to access the loopback IP web gui.

Is this a problem? No - not at all. But being a Linux fanatic I always like to understand how things work. What's happening differently between these systems? Which one is correct? Is Kubuntu incorrect because it can access the loopback at any given time even without a connection? Is Ubuntu incorrect because they should be able to?

---

