---
title: "IP Change"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by zeroTOLERANCE on 2009-06-09
Hey, i was wondering if something was possible in Ubuntu...
Can i get my computer to change its outward IP address at a set interval?
10.0.0.26 is what i have right now, but can i get it to change?
if this is possible can you please let me know.
Thanks in advance ;)

---

### Post by Iowan on 2009-06-09
If it's a static configuration, you could probably set a cron job to change it for you - if it's DHCP, you *might* be able to refuse an offer for the current address.

---

### Post by lensman3 on 2009-06-09
The 10.0.0.0/8 IP range is not routable address on the Internet backbone. The backbone routers drop that address. So in all likelihood, you are behind a NAT router that your provider is maintaining.  If the IP number is being assigned by the unique NIC number on your Ethernet card, then it is unlikely that your provider will allow you to change the IP number.

It might be possible to spoof the provider using the "arp" command.  Also take a look at using nmap and just filtering on the arp-packets.  The "who-has" and "who-is" packets might allow you to spoof.  Unfortunately, if you do spoof, then packets returning from the Internet may go to another computer and not to your computer.

---

### Post by Iowan on 2009-06-09
Are you behind a router - or is that your ISP-assigned address? The next (somewhat obvious) question is: Why is it necessary to periodically change your IP address? You may wish to plead the Fifth Amendment if it's to circumvent someone's security.

---

### Post by lisati on 2009-06-09
> **Iowan said:**
> The next (somewhat obvious) question is: Why is it necessary to periodically change your IP address?

Good question. I'm wondering too.....

The IP address 10.0.0.26 looks to me like one on a local network. On my own home network I prefer to assign a specific IP addresses to each of my own machines, so that in the unlikely event of someone complaining about me sending out unwanted email, it will be easier to track it down to a specific machine or to say "Sorry, that did not originate from my home network, next question please!" or even alert me to the possibility that someone has somehow managed to leech a connection.

---

### Post by zeroTOLERANCE on 2009-06-10
well when I made the post I was on a public router, but not right now. as for the use of this, I think I will stick with pleading the fifth :-p
just kiddin lol, its just a project that I have wanted to try for a while. its a curiosity of mine

---

