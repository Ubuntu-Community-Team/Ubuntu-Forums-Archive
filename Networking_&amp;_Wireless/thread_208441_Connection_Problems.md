---
title: "Connection Problems"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by Pimpbot5000 on 2006-07-03
Ok, mad props goes out to anyone who can solve this.  I have a 5.10 machine which was working fine up until friday afternoon.  It was around then that I started having problems with the browsing.  I can browse to google.com, and firefox.com, but it just sits there if I try and go to yahoo.com and msn.com.  I can get a good ping response back from yahoo.com, I just can't browse.  I have disabled IPV6 and that didn't fix anything.  This is an error that only became apparent when I was trying to do "sudo apt-get update" and it couldn't complete it.  I'm all out of ideas.  Any help would be appreciated.

---

### Post by Zelut on 2006-07-03
I wonder if its related to a DNS issue.  I've seen that happen after an ISP makes some changes.  If your machine can't seem to find its DNS server it wont' know how to get to the domains you're looking for.

I'd suggest re-checking your listed DNS (usually found in your router admin page) and manually enter that in your network setup.  See if that helps..

---

### Post by Pimpbot5000 on 2006-07-03
I went into the network setup and removed the DNS stuff.  Then I rebooted.  I confirmed that it did indeed re-load the DNS settings.  

About the network: The 5.10 computer is on an office lan with about 15 other computers none of them has any problems with connection.  All the computers are set to use DHCP with information from our router, which the ISP configures.

Any one else have any ideas?

---

### Post by Pimpbot5000 on 2006-07-06
Ok, so for anyone that cares, I fixed the problem.  It turns out my NIC was fubar.  I got fed up and re-installed Ubuntu.  When that didn't work, I switched network cables and jacks.  When that still didn't work, I did a lot of cursing, and then replaced my NIC card.  That worked.

---

### Post by Iowan on 2006-07-06
I care... It's always nice to see a problem solved, and know what fixed it.

---

