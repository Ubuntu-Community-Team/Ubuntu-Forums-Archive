---
title: "bonded cards, clients won't load"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by theller on 2011-09-02
I have a lucid, fat client server with 6 network cards. When I used these instructions [http://www.ubuntugeek.com/how-to-setup-bond-or-team-network-cards-in-ubuntu-10-1010-04.html](http://www.ubuntugeek.com/how-to-setup-bond-or-team-network-cards-in-ubuntu-10-1010-04.html)
the cards bonded (ifconfig showed slaves), but now my fat clients will not load. I get pxe-32 timeout.

It did work when I had configured each card to one static address separately through networkmanager.

I think I need to add a line in the  /etc/network/interfaces file or, should I go back to giving each card the same static address?

Anyone have ideas?

---

### Post by theller on 2011-09-03
Another piece of the puzzle is there is a separate machine handing out addresses. When I realized I didn't put that in the first post I also realized I didn't put that anywhere in the config file. I guess that's important.

Would I just add:

dns 192.222.2.2

---

### Post by theller on 2011-09-05
That dns line worked. 6 cards work as 1 (sounds like a superhero team). Fat clients log in and play video with no buffering. I tested with three clients; the real test will be when I have a class of 24.

I guess I don't need replies for the forum to help.

---

