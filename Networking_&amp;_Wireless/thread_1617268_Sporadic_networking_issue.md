---
title: "Sporadic networking issue"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by pumbani on 2010-11-09
Hi there,

I've been a linux user for years, but my network admin prowess are very much lacking. I've just got a lovely new server onto which I've install 10.04 server x64. It all seems to be working except for the network which seems to be somewhat unstable. If I ssh into the machine it will work, but then it'll stop responding for like 30 seconds. Then it will start working again. Then it will stop. etc. I haven't noticed an exact pattern and the duration isn't always the same...If I sit at the machine while the ssh is not responding and try to ping out, then it doesn't respond either. So it's not ssh that's being weird -- it's like the whole eth0 just doesn't work for a period and then starts working again. Note -- it doesn't drop the ssh connection.

I don't even know where to start looking. Anyone have any ideas? What more information can I give you to help you help me?

Thanks.

---

### Post by Zill on 2010-11-09
pumbani:  Could be a "simple" hardware failure.  I would try another ethernet card.

---

### Post by iponeverything on 2010-11-09
see if anything shows up in /var/log/message, /var/log/syslog, /var/log/debug and dmesg over the periods of the outages.

---

