---
title: "Can't connect to DIR-615 router"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by Icy Defiance on 2010-10-06
Hey, I'm dual-booting Win7 and Ubuntu 10.04, I can connect to my router wirelessly just fine in Win7, but not in Ubuntu.

The first time I booted into Ubuntu, the router worked, and I left it overnight to install updates (only took about 30 minutes, but it was already quite late). The next morning I tried to get my second monitor working, and the changes I made required me to restart my computer. When I got back into Ubuntu, it wouldn't connect to the router. After a while I figured out how to make the thing forget my router, I re-entered the password for the router and it connected. However, after the second restart, even that won't work.

I've been on Google for the past 5 hours, and I can't find anything at all on this issue since 2008. None of the fixes from back then seem to work...if I'm even doing them right.

I'm on an Acer Aspire 5534, my wireless adapter is an Atheros AR5B93, and I'm trying to connect to a DIR-615 router using WPA2 with AES only. I can connect to the internet through Ubuntu if I'm hardwired to it.

I've made so many funky changes to Ubuntu to try to fix this thing that half of them may be interfering with each other by now, I'll be reinstalling the OS before obeying any of the answers on this thread.

So yeah, what am I supposed to do?

---

### Post by vibris on 2010-10-10
Hi,

just figured out this problem.

in setup -> network settings -> uncheck Always broadcast

Zotac ION ITX D-E with ubuntu 10.04 and d-link dir-615 works fine.

---

### Post by Mistbubble on 2011-10-14
Hi!

I seem to have the same problem, my Dir-615 Router works only if wired. I tried to change the " always broadcast" thingie but I can't find it anywhere... no network settings, only properties, and nowhere anything about "always broadcast".I am using Ubuntu 10.10.  Could you, please, help me? Thanks!

---

### Post by Mistbubble on 2011-10-16
Problem SOLVED!! :-D

System->Administration->Additional Drivers-> select the other driver, if available and IT WORKS! :)

---

