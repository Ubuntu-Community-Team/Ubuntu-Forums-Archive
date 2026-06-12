---
title: "Two Computers (XP and Ubuntu) In Same Router"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by MasterPoulos89 on 2009-02-04
Hello.

I've been using Ubuntu for months now and since I started till now I've always randomly gotten disconnected from the internet. I recently realized that it is because of the XP computer hooked up to the same router. If I restart my Ubuntu while XP is still on my ubuntu wont have internet until I restart the router. If my XP restarts while my Ubuntu is on, my Ubuntu looses internet untill I restart the router. If I restart Ubuntu While XP is off my Ubuntu starts up connected to the internet.

I'm tired of restarting my router all the time. Can anyone help me. is this a known problem. Is there a solution?

Thanks In Advance

---

### Post by MartyBuntu on 2009-02-04
> **MasterPoulos89 said:**
> Hello.

I've been using Ubuntu for months now and since I started till now I've always randomly gotten disconnected from the internet. I recently realized that it is because of the XP computer hooked up to the same router. If I restart my Ubuntu while XP is still on my ubuntu wont have internet until I restart the router. If my XP restarts while my Ubuntu is on, my Ubuntu looses internet untill I restart the router. If I restart Ubuntu While XP is off my Ubuntu starts up connected to the internet.

I'm tired of restarting my router all the time. Can anyone help me. is this a known problem. Is there a solution?

Thanks In Advance

Check the NAT settings of your router and have in set to DHCP.
Make sure your XP machine and Ubuntu machine are also set to DHCP.

---

### Post by MasterPoulos89 on 2009-02-04
Both machines are set to DHCP and the only NAT option I see in my router is enable or disable, and it is enabled.

I now left the XP machine off for quite a while and my Ubuntu still managed to loose internet connection. After rebooting the router several times I finally regained internet. So my XP is not the only reason I loose internet connection on my Ubuntu. I don't think its my router, my router works fine for XP.

Maybe I should mention that my XP is hooked up to the main router, then I connected another router to the original for distance. So my Ubuntu is actually connected to the second router. I dint think that should affect it. When I had windows on this same machine the internet was working perfectly. There has to be another reason.

PS: both my routers are linksys......and my network card is (Intel Corporation 82566DC-2 Gigabit Network Connection).

Thanks for your time. I appreciate any possible solution.

---

### Post by MasterPoulos89 on 2009-02-05
OK.....problem solved......I should of realised that if I want to use a router as a hub I should configure it to do so........I disabled DHCP on the router I'm using as a hub........sorry for wasting time and space. At least I learned something new though.

---

