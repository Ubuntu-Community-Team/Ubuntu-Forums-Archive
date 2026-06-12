---
title: "wireless problems"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by theflanman on 2010-02-07
I have a TX2120us, and recently replaced 32-bit ubuntu with 64-bit AMD ubuntu, and now my wireless card, a broadcom bcm4328, doesn't work, any ideas what could be causing the problems?

---

### Post by lz1dsb on 2010-02-07
Did you try to compile and than install the Broadcom Linux driver? Here's where you can download it:  [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
In your case you'll need the 64-bit version. In the Readme file you'll find info how to compile it and than add it as a module.

Cheers,
Boyan

---

### Post by theflanman on 2010-02-07
yes, i did, didn't do anything though.

---

### Post by lz1dsb on 2010-02-08
Could you show what output you're getting when you try to insert the module with insmod?
Also did you have problems during the driver module compilation? Any errors, warnings? Did you save same outputs...

Regards,
Boyan

---

### Post by theflanman on 2010-02-08
I found something that fixed it, but thanks. :p

---

### Post by lz1dsb on 2010-02-09
I'm just curious... Did you use the native Linux driver? You could also mark this thread as solved.

Cheers, 
Boyan

---

