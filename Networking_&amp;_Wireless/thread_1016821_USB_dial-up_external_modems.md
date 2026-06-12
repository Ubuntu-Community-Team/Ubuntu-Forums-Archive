---
title: "USB dial-up external modems"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2008-12-20
I have read the posts about such modems (i.e., USRobotics, USR5637 fax modem).  Some say that they won't work.  Is there a known procedure to get such a modem to work with 8.10 and ALSO get it working with FIREFOX

John

---

### Post by ModelM on 2008-12-20
I have two USB modems, a USR5637 & also a Rosewill RNX-56USB. Both modems are recognized by the operating system (Ubuntu Intrepid) by simply plugging them in.

After that, it's just a matter of configuring your dialer program of choice to use whichever device the modem is, usually /dev/ttyACM0.

There are some USB modems which will not work with Linux because some USB modems are not hardware modems. The two I mentioned above, however, are hardware modems & each work perfectly without the need to install drivers - just plug them in.

---

### Post by ModelM on 2008-12-22
For folks tuning in late who may be modem shopping I wanted to add that the USR5637 modem has an Agere chip & the Rosewill has a Conexant chip. In case power consumption is a concern, the Rosewill uses 100ma & the USR uses a little more than 300ma.

---

### Post by Bartender on 2008-12-26
Firefox works with dial-up, you just have to remember to click the "Work Online" box.  Annoying.  I remember someone saying they had a workaround but didn't save the link.

---

### Post by ieee488 on 2008-12-26
> **Bartender said:**
> Firefox works with dial-up, you just have to remember to click the "Work Online" box.  Annoying.  I remember someone saying they had a workaround but didn't save the link.

Only a problem with 8.04, not 8.10.

---

### Post by Westmeath on 2008-12-26
> **ieee488 said:**
> Only a problem with 8.04, not 8.10.

Was happening in 8.10 for me.

---

