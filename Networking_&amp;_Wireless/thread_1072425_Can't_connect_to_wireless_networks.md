---
title: "Can't connect to wireless networks"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Desady on 2009-02-17
Hello folks, i am new to Linux & ubuntu for that matter.
I have installed ubuntu v.8.10 on my DELL Latitude D600. My system is able to notify me of available wireless networks within my range but i am not able to connect the network. Some networks sometime request for Keys which i get an administrator to enter for me but still doesn't connect.
Can anybody help me out? I am ready to assist in any manner.
Thanks a lot!

---

### Post by insineratehymn on 2009-02-17
Does it say anything when it is trying to connect? Or just blink and blink?

---

### Post by superprash2003 on 2009-02-17
you need to choose the right authentication type like 64 bit , 128 bit etc.. try with all options if your unsure..

---

### Post by Desady on 2009-02-17
> **Desady said:**
> Hello folks, i am new to Linux & ubuntu for that matter.
I have installed ubuntu v.8.10 on my DELL Latitude D600. My system is able to notify me of available wireless networks within my range but i am not able to connect the network. Some networks sometime request for Keys which i get an administrator to enter for me but still doesn't connect.
Can anybody help me out? I am ready to assist in any manner.
Thanks a lot!
Hey! thanks to all of you guys out there. I tried the right authentication type (WEP 64/40 bit) and it worked. So anyone with similar problem(s) should first of all check to see if the wireless device drivers are properly installed & configured (Please refer to ubuntu User guide). You must verify if your wireless radio is turned on. After all this is done, try connecting to the wireless network. If prompted for authentication, you can use the WEP 64/40-bit authentication (first on the list). If the network is security-enabled, do well to obtain the key from the network administrater & and enter it in the password field.
Select all default values & click connect. 
That's all, after authentication by the access point or router, a "Connection established" message should appear at the notification area.
If it fails, try entering the correct password again.
Enjoy!

---

