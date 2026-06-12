---
title: "two wifi adapters"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by corncob on 2011-11-26
My friend's HP laptop, running 11.10, has 2 wifi adapters both connecting to her router-- an internal Broadcom (3 bars) and an external linksys (about 2 bars).  She had thought the internal one wasn't working but it seems to be now.  Is there any advantage or disadvantage to using them both?  Just curious -- I don't notice any difference but then I haven't timed any downloads or anything.

---

### Post by dandnsmith on 2011-11-27
Unless you come up with a scheme to organise the traffic (by destination, traffic type ...) you can only confuse things by trying to use both - you're trying to send packets to the internet and receive them, how would you expect the 'conversations' to be sorted out?

---

### Post by corncob on 2011-11-28
Thanks for the reply; I figured there must be something to be said about that.  The USB adapter is gone but a problem still persists.  If the laptop is running on battery it won't go on the internet if the desktop is already on the web.  If it is on the web first it prevents the desktop (wired connection) from connecting.  It might connect to the router but won't open a website.  When the laptop is plugged into its power supply everything works fine.  Also, her other laptop does not have this problem.  Also, if I take the laptop home to my network it doesn't have this problem?  Any idea what's going on?

---

### Post by dandnsmith on 2011-11-29
Sounds as though the same IP address may be in use - so first one to establish traffic wins the connection.
You need to have a look at what is going on -
*ifconfig*          will show details of IP address etc
*route*             will show what routes are set to guide traffic
You need to run these as route, possibly.

---

### Post by corncob on 2011-11-29
> **dandnsmith said:**
> Sounds as though the same IP address may be in use - so first one to establish traffic wins the connection.
You need to have a look at what is going on -
*ifconfig*          will show details of IP address etc
*route*             will show what routes are set to guide traffic
You need to run these as route, possibly.

Thanks again.  I'll try it next time I'm over at her place.  Does the fact that it works with the power cord plugged in fit the picture?  The battery seems to last as expected when I bring it over here.

---

