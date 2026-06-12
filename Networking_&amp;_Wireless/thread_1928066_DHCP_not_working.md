---
title: "DHCP not working"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by igorium on 2012-02-19
Very same issue [here]("http://ubuntuforums.org/showthread.php?p=11700922#post11700922"), adding "MSFT 5.0" and removing rfc3442 didn't help.
Any other ways to fix it?

Windows recieves IP without problems, Ubuntu gets "No DHCPOFFERS"

---

### Post by Iowan on 2012-02-19
Moved to new thread.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

### Post by roelforg on 2012-02-20
Try switching routers/dhcp servers.
I have an old router laying around (somewhere...) that had the following problem:
Winslows: DHCP and internet
Ubuntu: No DHCP, no net
Got rid of it (replacing it with some thing better, needed extra ports anyway) and it worked!

I used that router because my pc-room only has 1 line to the central router,
Replaced it with a firewall (build from spare pc-parts) and a 3com superstack 4226T switch.
Speeds have now doubled-no tripled! No more port-shortages! Although the switch is complete overkill, it was cheap, got it used for 30 bucks (originally was a spare switch in for an local shop, they were renewing their net and sold their (still shrinkwrapped/3com sealed) switch to me! A 600 buck switch! This deal is the same as the beamer i bought from a local school (30 bucks, price in shops: 1000+ bucks (and this beamer has been in prod. for 10 years, top of the line);; Like they say: One man's junk is another's treasure)

---

