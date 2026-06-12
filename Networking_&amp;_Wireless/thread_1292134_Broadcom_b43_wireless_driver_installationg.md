---
title: "Broadcom b43 wireless driver installationg"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by yoshiki2 on 2009-10-15
ubuntu 9.04 acer aspire 5100
When i try the live cd i can see this driver in the driver restrict options..
but once I install ubuntu and i click on hardware drivers i cannot find it anymore... any ideas?

---

### Post by Ayuthia on 2009-10-15
I am not for sure why that happens.  However, if you have a working internet connection, you should be able to accomplish the same thing by installing b43-fwcutter from Synaptic or from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

Hope that helps.

---

### Post by yoshiki2 on 2009-10-15
I can drop by my gf's house.. to check it,  but do i need to add something? or just open terminal and enter those comandas, 1 by 1?

---

### Post by Ayuthia on 2009-10-15
> **yoshiki2 said:**
> I can drop by my gf's house.. to check it,  but do i need to add something? or just open terminal and enter those comandas, 1 by 1?

That should be all that you have to do.  Once it is complete, it will tell you to restart your computer (because it needs to reload the driver).  It should be ready after that.

---

### Post by swoody on 2009-10-15
That should work just fine, but you're going to need an internet connection to download the packages as well as fetch and cut the driver. As long as you can connect via ethernet cable, you should be good to go :)

---

