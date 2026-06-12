---
title: "Get me online PLEASE!!!!!!!!"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by tad214 on 2009-08-31
Hi, :P
I need help with getting on the internet. I can hook up to a wireless connection with no problem. However, i plugged the cat5 cable from my daughters cable modem into my laptop, and i do not have a connection. I am used to windows, just plug it in, and take off. So, could someone please tell me what i need to do to get online? Thank you so much for the help. Dale :(

---

### Post by tad214 on 2009-08-31
Hi, :P
I need help with getting on the internet. I can hook up to a wireless connection with no problem. However, i plugged the cat5 cable from my daughters cable modem into my laptop, and i do not have a connection. I am used to windows, just plug it in, and take off. So, could someone please tell me what i need to do to get online? Thank you so much for the help. Dale :(

---

### Post by tad214 on 2009-08-31
**Anyone? Please?**

---

### Post by philcamlin on 2009-08-31
please post output of ```
lspci
```

---

### Post by philcamlin on 2009-08-31
could you post output of ```
lspci
```

and why do you have 2 threads open?

---

### Post by tad214 on 2009-08-31
second post was an accident. I cannot get online to post the results of lspci. Is there anything i can tell you within the post?

---

### Post by tad214 on 2009-08-31
**up**

---

### Post by jwrede on 2009-08-31
I would start with entering "sudo ifconfig" in a terminal window and look for an adapter called "eth0" in the list and make sure that it has an IP address.

Also, have you tried resetting your cable modem?

---

### Post by overdrank on 2009-08-31
Threads merged and easy on the bumps it is not polite. :)

---

### Post by MrWES on 2009-08-31
> **jwrede said:**
> I would start with entering "sudo ifconfig" in a terminal window and look for an adapter called "eth0" in the list and make sure that it has an IP address.

Also, have you tried resetting your cable modem?

If you're connected directly from the cable modem to the computer you'll need to reset the modem. There should be a small reset button on the rear panel. When your daughter had her computer connected to the cable modem, the modem stores the MAC address of her card in memory. When you connected the cable modem to your computer, which has a different MAC address; you won't be able to connect.

Generally, just powering it off and back on will not clear the MAC address from memory, you can try though. I've always found it necessary to do a hard reset.

Bill

---

### Post by tad214 on 2009-08-31
Thanks Mr.Wes. That is all it needed. I am on it now. Thanks again guys. Your the best. Have a great day. Dale p.s. Again, i apologize for the second post and the bumps.

---

### Post by Iowan on 2009-08-31
BTW, [SOLVED] appears to be back (under Thread Tools).

---

### Post by MrWES on 2009-08-31
Your welcome. Went through the same thing with my son and his computer and PS3; cable modem -- no router. Heck, even Comcastic didn't know that one. Took me several days and many forums to track that fix down. Now remember, when you reconnect her computer you'll need to do the same thing -- or get a router and you won't have to.

Bill

---

