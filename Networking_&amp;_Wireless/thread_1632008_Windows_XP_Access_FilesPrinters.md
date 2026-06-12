---
title: "Windows XP Access Files/Printers"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by Thinkin on 2010-11-27
Have 10.10, but for some reason cannot access an XP workgroup or machine.  I can ping in both directions from Ubuntu to XP and vice versa.

When I try to open the Windows Workgroup I get the following error:


Unable to mount location.
Failed to retrieve share list from server.

---

### Post by gordintoronto on 2010-11-27
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Thinkin on 2010-11-27
Solved:

I finally got this working, yet I did not have Dlink advanced DNS turned on. In my situation, the:

Use Unicasting : (compatibility for some DHCP Servers)

was turned on the router, when unchecked I am back to normal!

---

