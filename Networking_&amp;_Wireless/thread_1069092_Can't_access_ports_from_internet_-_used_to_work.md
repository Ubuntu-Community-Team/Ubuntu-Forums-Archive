---
title: "Can't access ports from internet - used to work"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by sav74sac on 2009-02-13
I used to be able to access my ports 80/apache & 22/ssh fine from outside computers. For some reason it stopped working... and rebooting my computer and router has not resolved the issue.

I have all my router port forwarding setup, as well as firewall access.
I haven't changed any of that since it stopped working.

I can access things fine from localhost, or even from another machine on my network (using 192.168.1.101).  It's just the ISP IP address that won't work from the outside.

Also, GRC ShieldsUp shows that my ports are open.
I enabled/disabled port forwarding & ShieldsUp respectively showed Open/Closed.
I also granted/restricted firewall access & ShieldsUp respectively showed Open/Closed.
So... it seems that my ports are being detected as open from the internet.

Can anyone suggest what I can check or try to see where the problem is?

---

### Post by sav74sac on 2009-02-13
I'm sorry - I figured it out...

Restarting my router did fix the problem actually.
I just used the old IP address & needed to re-run noip2 to get things updated.

Problem solved. If anyone has this problem, try rebooting your router (and computer just to be sure). That seemed to do the trick.

---

