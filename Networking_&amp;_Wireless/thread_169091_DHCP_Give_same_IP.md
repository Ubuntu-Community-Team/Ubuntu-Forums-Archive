---
title: "DHCP Give same IP"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by Ignite_nz on 2006-05-01
Okay so I have my DHCP server running okay, all my computers on my network can get on the internet and get their IP addresses off it, however I have one question, how do I make it so that each computer has an IP it gets from the DHCP server thats the same each time it renews without setting their IP's to static? I changed the lease time on the IP's, this is all very well and good untill the computers get rebooted and they recieve a new IP from the DHCP server, can anyone help me with this, maybe I need to add the MAC addresses of the PC's to a list somewhere or something?

Any help would be greatly appreciated, thanks :).

---

### Post by jchau on 2006-05-01
Sounds like you probably want to use the dynamic allocation (or maybe manual allocation) mode for your dhcp server [http://en.wikipedia.org/wiki/DHCP#IP_address_allocation](http://en.wikipedia.org/wiki/DHCP#IP_address_allocation) .  I don't have dhcp server running, so I can't give you step by step instructions, but you should be able to find a config file to set this.  

Hope this helps!

---

### Post by Keith_Beef on 2006-05-01
[QUOTE=Ignite_nz]Okay so I have my DHCP server running okay, all my computers on my network can get on the internet and get their IP addresses off it, however I have one question, how do I make it so that each computer has an IP it gets from the DHCP server thats the same each time it renews without setting their IP's to static? I changed the lease time on the IP's, this is all very well and good untill the computers get rebooted and they recieve a new IP from the DHCP server, can anyone help me with this, maybe I need to [COLOR="Red"]add the MAC addresses of the PC's to a list somewhere[/COLOR] or something?

Any help would be greatly appreciated, thanks :).[/QUOTE]

I suppose you must have a good reason for wanting each host to get thesame IP address, and I would have done that by giving each a static address.

My NetGear router has a built-in DHCP server, that can reserve an IP address for a known MAC address (as you guessed); maybe you can do that with your DHCP server...


Beef.

---

### Post by mips on 2006-05-02
You might as well stick with static IP's.

What you want to do can be done but you have to manually assign them in dhcp with MAC address which kinda defeats the object of dhcp i would say ?

---

### Post by jchau on 2006-05-02
Well, I suppose automatic allocation will be useful if you're starting a large network.  You wouldn't have to assign everyone an ip manually and everyone gets to keep a static IP.  

Using the manual allocation might also be useful to prevent another computer from snatching up an IP address from a computer that is off.  

I guess DHCP just help prevent IP address confilicts.

---

### Post by Iowan on 2006-05-02
There's a thread around here  - somewhere - that discusses static allocation via DHCP (even for servers) based on MAC address.  This lets you manage assignments via the DHCP server instead of setting them individually at each machine.  
[http://ubuntuforums.org/showthread.php?t=122108]("http://ubuntuforums.org/showthread.php?t=122108")

---

### Post by Ignite_nz on 2006-05-03
Cheers for your help everyone, I will consdier my options and do what I want to do from there.

As us kiwi's say, have a good one :)

---

### Post by Slim Odds on 2006-05-03
[QUOTE=mips]You might as well stick with static IP's.

What you want to do can be done but you have to manually assign them in dhcp with MAC address which kinda defeats the object of dhcp i would say ?[/QUOTE]

That's not really true. DHCP does a lot more than just assign IP addresses. One of the most important roles for DHCP is to assign the gateway address and the DNS address(es). 

It's not unreasonable to want each machine to keep the same IP address each time it comes up, but still have the flexability of assigning the gateway and DNS dynamically.

---

