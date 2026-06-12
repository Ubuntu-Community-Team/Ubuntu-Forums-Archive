---
title: "get default networking configuration"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by freakinjonathan on 2009-07-01
ok so I had to redo my networking configuration and now to redo it I need to run 
sudo apt-get install network-manager net-tools
without internet.

I am running off the live cd right now. 
I did
sudo apt-cdrom add
sudo apt-get update
       all the couldnt connect to repo errors
sudo apt-get install network-manager net-tools

but that did not work.
How do you install packages offline?

---

### Post by t0mppa on 2009-07-01
I believe you have to tick off the online repo's from the sources list, so that it doesn't try to look them up for updates and of course add the cd in there as well.

---

