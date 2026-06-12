---
title: "WPA key wrong with Network Manager"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by mklcst on 2010-09-09
Hi guys, I have a problem to insert the WPA password on ubuntu.
I recovered an old pentium year 2003 by installing ubuntu 10,04, I have a USB stick for wifi and ubuntu recognized it immediately seeing all wifi networks available (great!).
The problem is that it recognizes as wrong the WPA and remain in constant connection attempt then giving me the error, how can I resolve it?

The wifi key is "Emtec USB 2.0 Wireless Wan",  with windows xp works.

Thank you very much for your support.

---

### Post by bkratz on 2010-09-09
> **mklcst said:**
> Hi guys, I have a problem to insert the WPA password on ubuntu.
I recovered an old pentium year 2003 by installing ubuntu 10,04, I have a USB stick for wifi and ubuntu recognized it immediately seeing all wifi networks available (great!).
The problem is that it recognizes as wrong the WPA and remain in constant connection attempt then giving me the error, how can I resolve it?

The wifi key is "Emtec USB 2.0 Wireless Wan",  with windows xp works.

Thank you very much for your support.

There are sometime problems if the A/P is setup to use both WPA and  WPA2 You might want to try changing the (wireless router?) to either WPA or WPA2 but not both.

see this posting

[http://ubuntuforums.org/showpost.php?p=9825038&postcount=35](http://ubuntuforums.org/showpost.php?p=9825038&postcount=35)

---

### Post by mklcst on 2010-09-09
Ok now I try to see the router

---

### Post by mklcst on 2010-09-09
Ok, my router's settings are:

Security Mod: WPA2 Personal

Encryption: TKIP or AES

---

### Post by bkratz on 2010-09-09
Can you set it to AES only? Again, mine required separate WPA and WPA2 and also separate TKIP and AES to finally get it to work correctly.

---

### Post by mklcst on 2010-09-09
it works!!! Thank you very much, I asked to italian support but none can able to answer me.
):P

---

### Post by bkratz on 2010-09-09
> **mklcst said:**
> it works!!! Thank you very much, I asked to italian support but none can able to answer me.
):P

Can you go to the thread tools and mark it as [solved] just in case it helps someone else.

Oh, and congratulations!

---

