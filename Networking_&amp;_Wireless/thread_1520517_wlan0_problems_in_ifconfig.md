---
title: "wlan0 problems in ifconfig"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Light_Yagami on 2010-06-29
Alright, I know this place is for Ubuntu, this is for my new Debian system and I've heard that similar problems can be fixed in Debian and Ubuntu. So anyway;

I need to find my IP address. When I type in "ifconfig", I get this:

lo          Link encap:Local Loopback
             inet addr:* address here*    Mask: *another address*
             UP LOOPBACK RUNNING   MTU: 16436   Metric:1
             RX packets: 4 (and so on and so forth.)

But in my Ubuntu system, when I type in *ifconfig*, I get the catagories: 

eth0
lo
wlan0
wmaster0

So just like above, I have the "lo" section, but I really need the wlan0 section &/or eth0.
Do you know how to either write one up, or find a website that shows you how to get *eth0* onto your *ifconfig* page?

---

### Post by Iowan on 2010-06-29
You can try **ifconfig -a** - which should show all available interfaces (even if down). By the way... loopback device (lo) is ordinarily 127.0.0.1 with mask 255.0.0.0. If eth0 doesn't show up, you might check **sudo lshw -C network** to see if interface has an alias, driver, etc...

---

