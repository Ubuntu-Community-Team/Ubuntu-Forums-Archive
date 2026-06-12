---
title: "Multiple Wireless Cards"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by lukus on 2009-07-01
Hi There,

I have a desktop computer, with 2 wireless cards and one wired network port in it.

I am using Ubuntu - with GNOME.

NetworkManager takes care of there being a wired and wireless card in there - no probs, however, using 2 wireless cards is a bit of bother... I cannot seem to get ubuntu to realise there are 2 cards. It seems to just select a card and go with it. I have tried to remove one card and use the other, and this works fine. but for some reason, when there are 2 cards in the computer, only one will work at one time...

why?
is there a solution?

Cheers,

Lukus

---

### Post by t0mppa on 2009-07-01
Network Manager cannot handle more than one wired or wireless interface at a time. You'll have to configure the rest manually through /etc/network/interfaces and /etc/resolv.conf

---

### Post by lukus on 2009-07-02
I see...

---

### Post by superprash2003 on 2009-07-02
network manager can handle more than one wired interface though.. not sure about wifi

---

### Post by t0mppa on 2009-07-02
I stand corrected, was added to 0.7. Unless someone has experience with multiple wireless interfaces and network manager, manual configuration is still the best bet though.

---

