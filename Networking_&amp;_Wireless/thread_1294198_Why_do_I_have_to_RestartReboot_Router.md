---
title: "Why do I have to Restart/Reboot Router?"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by age99 on 2009-10-18
Hi All,
I am remotely accessing a Ubuntu machine that is wired to a router (D-Link 624).  I am using Xming, Putty (through vista) and ssh (Ubuntu) to access the machine and it works well however every couple of weeks the router needs to be reboot/restarted otherwise there is no access.  

There are other Vista/XP machines that access the the net using both wired and wireless connection on the same router and they are never experiencing any problems.

Is there some way to permanently (or semi-permanently) fix this issue?  What is causing it?

If not, is there any way to re-boot the router remotely?

Thanks

---

### Post by Johndo1 on 2009-10-18
If you know the Ip address of the router type it into the browser search-bar and hit enter. You should be able to log into the remote router with some sort of gui-interface were you can reboot it from there. 

If the Ip address doesnt work try the Gateway. To find the gateway address type in  "Route" in the terminal.
To find out other information about the internet on the ubuntu machine type in "ifconfig".

Hope this helps!

---

