---
title: "[SOLVED] OpenDNS servers  problem.... Ubuntu 8.10"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by paparozoumis on 2009-01-09
I want to use OpenDNS servers on my Ubuntu 8.10 laptop. 

I change them via System>Administration>Network>DNS>Add

In there, I can  find the address  that  points to my router. If I delete this address and add OpenDNS (208.67.222.222 and 208.67.220.220) I can    use the  latter but I lose my shared folders from my other computers. 

If I put first  my router's  address,   the  second and third DNS won't work, so I have my shared   computers but not the OpenDNS. 

Is there any way to have both, shared computer/files AND OpenDNS?

---

### Post by TransitMan on 2009-01-10
> **paparozoumis said:**
> I want to use OpenDNS servers on my Ubuntu 8.10 laptop. 

I change them via System>Administration>Network>DNS>Add

In there, I can  find the address  that  points to my router. If I delete this address and add OpenDNS (208.67.222.222 and 208.67.220.220) I can    use the  latter but I lose my shared folders from my other computers. 

If I put first  my router's  address,   the  second and third DNS won't work, so I have my shared   computers but not the OpenDNS. 

Is there any way to have both, shared computer/files AND OpenDNS?

Yep, put the OpenDNS IP's in your router, and have the computer use the router's IP for DNS lookup.

---

### Post by paparozoumis on 2009-01-10
> **TransitMan said:**
> Yep, put the OpenDNS IP's in your router, and have the computer use the router's IP for DNS lookup.

You're  right... 
Actually I  didn't want to mess with telnet'ing the router but at the end this is the most correct solution... 
I finally did it and everything works as it should... 

Thanks for the advice :P

---

