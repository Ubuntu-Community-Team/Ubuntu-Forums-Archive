---
title: "laptop cart and Likewise-open random failing logons"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by defunkt on 2011-08-20
im not new to ubuntu, been working with ubuntu for about 5 years.  i was recently given the chance to get ubuntu into the classrooms.  

we are a windows AD environment, in a high school.  we have deployed linux in desktop computer labs previously without a hitch (using likewise-open) and have had great success.  this summer we have installed likewise on about 100 netbooks and all seemed well...

we have run into a problem which i havn't been able to narrow down just yet.  in each laptop cart, only about 90% of the netbooks will login successfully. the 10% that fail dont seem to fail the next period that students use them.  so its not always the same laptops, not the same user accounts.  my first reaction was it must be a wireless issue, but if i hop on a problematic netbook on another tty...  im connected to the wifi and can ping both DC's.  so at first glance i dont see this being a network issue.  rebooting the netbook doesnt seem to solve the problem either; and that confuses me more because next period (after the laptop has been shut down) the netbook may work perfectly fine...

i have a hunch that likewise-open is starting prior to clients being connected to the network, thus causing problems.  but i cant find anything to back that up.  honestly i cant find a whole lot of people using likewise on any larger wireless networks.

our wireless infrastructure is plenty robust enough, we have redundant cisco controllers with load balancing, multiple AP's covering rooms, etc.

i firmly believe that this is some sort of software related issue, but im at a loss because its not the same devices that have the problem repeatedly.  

any insight or ideas from the ubuntu gods would be greatly appreciated.

---

