---
title: "Router appears down but can ping it"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by Kurtosis on 2010-05-20
Every three or four weeks my router and cable modem will appear to go down.  Not only can I not access the internet or web, but I can't even access the router and modem's admin pages (192.168.2.1 and 192.168.100.1 respectively).  However, I can successfully ping 192.168.2.1 (forgot to try pinging the modem ip).

Hard resetting both by unplugging them for about a minute or so and replugging them fixes the problem.  This is what Roadrunner says to do any time connectivity is lost.

This problem also used to occur on Windows as well, except that on Windows I could still browse to both the router and modem's admin websites and restart them remotely.  On Ubuntu (both 9.10 and 10.04) I have to manually unplug them since I can't bring up the admin sites in a browser.

I'm not sure how to go about troubleshooting this issue, and why Linux seems to require a manual hard reset whereas it could be solved on Windows with a remote restart.  I wouldn't have thought the OS would even have anything to do with that.  Any suggestions or ideas on how to figure out what is going on here?

Thanks!

---

### Post by Iowan on 2010-05-21
I'm sure you've already tried, but what effect does resetting the router alone have? Is there more than one (client) machine attached to the router? (I'm curious if they show different symptoms/results). Also out of curiosity, what brand/model are the router and modem?

---

