---
title: "Problem with wireless network"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by mrmichael on 2009-06-10
Greetings!
I ve just installed the new ubuntu 9.04, and I am using a wireless adapter card to connect to the web. Ubuntu finds my network and it connects but for some reason I do not get the proper packets. I can't open webpages, can't download updates etc etc.
Should I edit some files, or perhaps edit and configure my connection?

Thanks a lot,
Mike
:)

---

### Post by yaroto98 on 2009-06-10
can you ping the router?

```
ping 192.168.0.1
```?

---

### Post by mrmichael on 2009-06-10
Hey there!
Uhm my router is set to 192.168.1.1, but I can't ping this one either....

---

### Post by mrmichael on 2009-06-10
Hey there!
Uhm my router is set to 192.168.1.1, but I can't ping this one either....

---

### Post by yaroto98 on 2009-06-10
if you can't ping it then you're not really connected (even if it may say you are). Often times with ndiswrappers you might not have full encryption capabilities (usually WPA). Try removing the security (WPA(2) or WEP) from the router, and see if you can connect. If you can, try something like just WEP, if that works, you may have to stick with WEP.

---

### Post by mrmichael on 2009-06-10
Yeah I tried that before, and I left my router with no security but didn't work either! Actually my browser loaded only the title of the page and some broken images but that's all. I had the same problems with windows xp but once I set an ip to the machine it worked perfectly... Is there something else I can try ?

---

