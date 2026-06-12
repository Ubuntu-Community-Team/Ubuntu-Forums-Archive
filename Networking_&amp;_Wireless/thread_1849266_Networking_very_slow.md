---
title: "Networking very slow"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by geraintedwards on 2011-09-24
After my system (11.04) was updated on Thurdsay 22 Sep 2011 my wired networking completely seized up - locally and internet.

Speeds down to 20-50 bytes per second (sic NOT Kilobytes)  - I guessed it could have been a recent update so went back through the history.

I removed Apport (which was updated to version 1.20.1) which improved things a lot but the network was still painfully slow.

I then tried rebooting using the previous kernel (not the new 2.6.38-11) but not much joy there.  

Other machines on the network are accessing the network normally and I've tried changing cables, rebooting the router etc.

Any suggestions for how I can diagnose the issue further would be very welcome.

Thanks

---

### Post by geraintedwards on 2011-09-24
I have found a wireless networking USB stick and instantly connected at full speed.

So there is something amiss with the wired connection - any suggestions for hardware tests or driver checks would be great

the card is :

RTL8111/81688 PCI Exptress Gigabit 

thanks

---

### Post by bkratz on 2011-09-24
> **geraintedwards said:**
> I have found a wireless networking USB stick and instantly connected at full speed.

So there is something amiss with the wired connection - any suggestions for hardware tests or driver checks would be great

the card is :

RTL8111/81688 PCI Exptress Gigabit 

thanks


Look at your 

lsmod

and see if r8169 is an active module or is it r8168.  When it uses r8169 there sometimes are a lot of network problems with the wired connection.  I will find the thread that tells about it in a few minutes.

---

### Post by bkratz on 2011-09-24
Here is the thread I was looking for (If you see r8169 in lsmod).

[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

---

### Post by geraintedwards on 2011-09-24
thanks for the suggestion - it was indeed a r8168 card using the r8169 driver but the changes suggested had no effect.

I'll do some more looking around on this topic.

---

