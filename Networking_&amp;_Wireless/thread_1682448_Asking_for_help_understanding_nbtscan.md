---
title: "Asking for help understanding nbtscan"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by frotzed on 2011-02-05
So I'm trying to use nbtscan.  Ideally what I'd like to do it use it to find all the devices (wired and wireless) on a given network which my laptop is connected to.  But I'm running into some confusing results.

When my laptop - running 10.10 - is connected to a network only via wireless I run nbtscan like this:

```
nbtscan 192.168.1.1-254
```

and it gives me all, but ONLY, the wireless devices on the network.  I can see everyone else's laptop and the wireless printer (which has a static IP).  But I can't see my desktop, which is wired to the same router and also has a static IP.

So I plug a network cable into my laptop and run nbtscan exactly the same way as I did before.  When I do this, the laptop is connected wirelessly as well as wired so it effectively has two IP addresses (one for each NIC).  But this time, while I can see the other laptops, I _still_ can't see my wired desktop but now I can't see the wireless printer.

Then, when I disconnect wirelessly and only have a wired connection I get the same results as when I had both wireless and wired connectivity.

Running nbtscan with the exact same parameters from my wired desktop results in showing me all the wireless devices _except_ for that wireless printer.

My wired desktop is at 192.168.1.100 and the printer is at 192.168.1.101.  The router's DHCP range is .2 through .99 so as to not cause any avoidable conflicts.

I'm not a network engineer but have a fairly sound base in simple networking.  I'm hoping I can get a little education as to why this would be happening with nbtscan.  I'd also like to know how to return a complete list of all networked devices on any given subnet.

EDIT: I suppose it is pertinent to point out that the wired desktop is running Ubuntu 10.10 as well as my laptop, but all the other devices (except for the printer) are running Windows Vista and 7.  Not sure if perhaps my desktop is making itself "invisible" on the network?

---

### Post by registered2-5-2011 on 2011-02-06
try doing...

```
sudo nbtscan -r x.x.x.1-254
```

the -r may help you see windows boxes(you have to use sudo with the -r)

as far as the wired/wireless differences go I believe that it has to do with the fct that the wired pc's are technically in a switched environment. nbtscan does not work bery well on my cisco 2960 switch. Note that if you fire up wireshark on a wifi pc you can see all the traffic going to the other wifi pcs as well as the broadcast traffic, but you would not see any of the traffic occurring between the wired pc's and the router. nmap may be a better solution as far as seeing all the boxes on your net, try the -sP for a ping sweep it is less offensive.
```

sudo nmap -T4 -sP x.x.x.1-254
```

here's a few links
[http://www.inetcat.net/software/nbtscan.html](http://www.inetcat.net/software/nbtscan.html)
[http://wiki.wireshark.org/CaptureSetup/Ethernet](http://wiki.wireshark.org/CaptureSetup/Ethernet)

---

### Post by frotzed on 2011-02-06
I really appreciate that answer.  Not only am I able to accomplish what I want now (scanning a network for devices) but you've also pointed me toward material for self-study.  You're awesome dude :KS:KS

---

