---
title: "How to get Reverse DNS to work?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by krasenpaskaa on 2009-11-21
I am very new to this, so my question might be way off here.

I installed Bind on my system and set it up according to a guide I followed.

It works great in one way, if I ping my domain (let's call it example.com) I get a response, and if I do a dnslookup on example.com, I get the IP of my machine.

The other way around does not work however. If I do a lookup on the IP, it gives me my ISPs host, not example.com

Is there any way I can fix this?

---

### Post by back2arie on 2009-11-21
Hi

Could you post your Bind config, so we can take a look...:)

---

### Post by Bachstelze on 2009-11-21
You cannot use a local DNS server to customize the reverse DNS record of your ISP-assigned address. This must be done on your ISP's nameservers. Contact them and ask if that's possible.

---

