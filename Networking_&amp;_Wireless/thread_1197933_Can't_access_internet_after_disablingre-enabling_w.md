---
title: "Can't access internet after disabling/re-enabling wireless"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by andreselsuave on 2009-06-26
Hi there. The topic explain itself. 

I have an HP 8710p laptop which has a deactivate/activate wireless button. When I push it, the wireless goes down accordingly, but when I want it back again, I push the button and wait, but the connection never comes back :(.

I also tried doing

```
sudo /etc/init.d/NetworkManager stop
sudo /etc/init.d/NetworkManager start
```

but doesn't work. Network manager shows no wireless points available. Anyone knows how to fix this? 

thank you

---

### Post by wojox on 2009-06-26
Did you just try rebooting your laptop?

---

### Post by andreselsuave on 2009-06-26
Well, yeah, rebooting is the only way to get it back. I meant a solution without the need of rebooting but thanks however :)

---

