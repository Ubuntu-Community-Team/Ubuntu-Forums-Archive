---
title: "Connecting to a remote computer with dial-up"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by GenBattle on 2009-11-24
Hi there.

I'm trying to switch my grandparents over to Ubuntu, but i don't think they'll be able to maintain it fully by themselves, and i don't know of any local Ubuntu experts where they live who can help them with any problems they have. 

My solution is to try and set up some ability to SSH or remote desktop into their machine. This would be reasonably simple for a DSL connection with a static IP, but unfortunately they are still on dial-up.

Therefore i have two ideas of how i can connect to their computer remotely. First, just go in over IP; they connect on their 56K connection, and i connect to their PC through my ADSL connection. The problem is i don't know how to set this up with a dial-up modem (which usually have dynamic IP addresses that change with each dial). The second idea i had was to simply set up the computers so one computer can dial into the other directly (my computer has a 56K modem as well, although it is currently unused).

Any other ideas as to how i could achieve this sort of connection (i'm a complete SSH/RDP newbie...) would be much appreciated, as well as any help with setting up one of the two ideas i've come up with so far.

Thanks.

---

### Post by dmizer on 2009-11-24
The dial up connection will always be 56K no matter how you or they connect. Because of this, the connection will probably be way too slow to be useful even for SSH. RDP would most certainly be impossible.

I suggest looking for some more input on SSH over dial up, but don't expect much.

Sorry.

---

### Post by GenBattle on 2009-11-24
Ah ok, i had a fair inkling RDP would be nearly impossible but i didn't think ssh would be too intensive. Guess it's back to the support drawing board. Thanks for the info.

---

