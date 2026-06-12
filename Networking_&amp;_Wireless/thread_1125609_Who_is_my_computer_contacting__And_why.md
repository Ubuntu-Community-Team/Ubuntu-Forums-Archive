---
title: "Who is my computer contacting?  And why?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by t0p on 2009-04-14
I use a 3G cellphone to connect my computers to the internet.  I've noticed that, when I'm surfing the internet, my computer periodically trades data with hosts with ip addresses like 1.2.3.8, 1.2.3.10 and 1.2.3.12.  These are obviously computers on my cellphone provider's network - these ip addresses are reserved so I assume belong to my cellphone provider (or whoever runs their network).  What I want to know is: why is my computer talking to these machines?  And what kind of info is passing between them?  I don't like the idea of these conversations taking place when I don't know what's being said.

I used wireshark to capture some of these packets.  Unfortunately, I don't know how to analyze them and get meaningful data. Can anyone help?

---

### Post by pytheas22 on 2009-04-14
What IP address do you have when you're on the provider's network?  Is it in the same subnet as the machines being contacted?  If so, it's possible this is just normal ARP traffic.  They could also be your DNS server or something like that; look in your /etc/resolv.conf file to see which DNS you use.

Otherwise, if you want to upload a packet dump somewhere, I'll take a look and see if anything stands out as suspicious, but be advised of course that a packet dump could possibly contain private information.

I suppose you could also run a port scanner like Zenmap/nmap to try to get a better idea of what the computers in question are doing (which ports they have open, which operating systems they run, etc.).  That would be kind of rude, but it's also rude if your ISP is sending traffic to these machines without your knowledge.

---

### Post by kerry_s on 2009-04-14
several things do that.
examples:
update-manager
ntpdate
firefox and it's plugins
mail
etc...

if you want to stop it, try disabling those kind of things.

---

### Post by t0p on 2009-04-14
> **pytheas22 said:**
> What IP address do you have when you're on the provider's network?  Is it in the same subnet as the machines being contacted?  If so, it's possible this is just normal ARP traffic.  They could also be your DNS server or something like that; look in your /etc/resolv.conf file to see which DNS you use.

My ip address will be something like 10.157.40.254.  The machines being contacted have ip addresses 1.2.3.8-13.  My /etc/resolv.conf has my DNS servers as 149.254.192.126 and 149.254.201.126

> **pytheas22 said:**
> 
Otherwise, if you want to upload a packet dump somewhere, I'll take a look and see if anything stands out as suspicious, but be advised of course that a packet dump could possibly contain private information.

I suppose you could also run a port scanner like Zenmap/nmap to try to get a better idea of what the computers in question are doing (which ports they have open, which operating systems they run, etc.).  That would be kind of rude, but it's also rude if your ISP is sending traffic to these machines without your knowledge.

I think I may run nmap on them.  I'm very curious as to what's going on here.  As for showing you a packet dump - I may take you up on the offer.  Anyway, thanks for the feedback, it's given me something to chew on anyway.

---

### Post by t0p on 2009-04-14
> **kerry_s said:**
> several things do that.
examples:
update-manager
ntpdate
firefox and it's plugins
mail
etc...

if you want to stop it, try disabling those kind of things.

A process of elimination may reveal what's going on here.  Thanks for the advice.

---

### Post by Stupendoussteve on 2009-04-14
Those IP addresses are reserved (IANA says they are unallocated). There shouldn't be any systems on them.

I am interested to see some of the traffic.

---

