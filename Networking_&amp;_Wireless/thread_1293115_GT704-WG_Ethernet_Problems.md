---
title: "GT704-WG Ethernet Problems"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by Patriot1776 on 2009-10-16
I recently got a donated GT704-WG DSL modem/router with Ethernet and wireless, and the wireless is working, but pppoeconf cannot apparently see the modem when I've got it hooked up to my Hardy system via Ethernet.

Both the ethernet and wireless work in Windoze XP, but of course I ain't switching to it to get online when using this router.  Any ideas of what I need to look at and change?  System log monitoring confirms the system is not seeing the router on eth0, my primary ethernet port.  I'm using my old Westell modem to post this.

---

### Post by Patriot1776 on 2009-10-17
[SOLVED]

Somebody please delete this thread.  Got it working by going to System->Administration->Network and setting Wired Connection to DHCP.  Yes, I still am a newbie to a huge degree when it comes to admining my system and it makes me feel horrible. I'm not on here often enough to even remember how to mark this thread as SOLVED.

---

