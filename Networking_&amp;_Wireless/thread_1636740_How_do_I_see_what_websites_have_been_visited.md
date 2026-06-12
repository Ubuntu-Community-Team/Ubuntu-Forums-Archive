---
title: "How do I see what websites have been visited"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by squishjt on 2010-12-03
Hi guys.

I would like to know if it's possible  and how to see what websites my neighbours visit using my BB connection. I leave it open out of courtesy really, Nice peeps around here. And i have been in the situation myself when my connection went down and was piggy backing on my neighbours for a while. It's a sky BB router btw.  Thanks in advance :).

---

### Post by pricetech on 2010-12-03
Does your router do logging ??  Does it have a feature that allows you to have the logs mailed to you when full ??

Be prepared to spend a lot of time looking at them.

---

### Post by CharlesA on 2010-12-03
If you are looking for a way to tell what sites have been visited from your connection, good luck with trying to log everything and filter the resulting data.

I don't know an easy way to do what you want as there will be multiple machines connected as your wireless is "open" and you can't exactly see the history of the browser on those machines.

---

### Post by SeijiSensei on 2010-12-04
If you **really** want to do this, I'd suggest the following:

1)  On your wireless router, assign specific IP addresses to your visitors based on their MAC addresses.  That way, you'll know that Ken is always 192.168.1.23 and Barbie is 192.168.1.34.

2)  Put a Linux box between the router and the Internet. Configure it with iptables to do firewalling and run the Squid proxy in transparent mode.  You'll get (long) logs of every object downloaded from the Internet.

3)  You can dispense with (1) if you use authentication in Squid instead.  Then your neighbors would have to log in with a username and password to browse the Internet.

---

### Post by squishjt on 2010-12-04
> **SeijiSensei said:**
> If you **really** want to do this, I'd suggest the following:

1)  On your wireless router, assign specific IP addresses to your visitors based on their MAC addresses.  That way, you'll know that Ken is always 192.168.1.23 and Barbie is 192.168.1.34.

2)  Put a Linux box between the router and the Internet. Configure it with iptables to do firewalling and run the Squid proxy in transparent mode.  You'll get (long) logs of every object downloaded from the Internet.

3)  You can dispense with (1) if you use authentication in Squid instead.  Then your neighbors would have to log in with a username and password to browse the Internet.



Perfect. Thanks Sensei. Happy holidays.

---

