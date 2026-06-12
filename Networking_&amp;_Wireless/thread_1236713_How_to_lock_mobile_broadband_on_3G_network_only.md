---
title: "How to lock mobile broadband on 3G network only ?"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by londonbabs on 2009-08-10
I'm using a O2 mobile braodband pay as you go huawei E160 modem, never had troubles to install it on Jaunty, but without the original manager, I haven't found an easy way to lock the network to 3G only, and the dongle keeps jumping from one to the other in a very erratic manner, resulting in a wobbly connection.
I was just wondering if anyone knew a simple way around this
I can handle myself with computers, but am still a noob with ubuntu, so any easy explanations would be better appreciated.
Thanks in advance

---

### Post by Macchi on 2009-08-10
I would also like to find a solution for this, but I believe that the main cause of your problem must be poor signal reception for 3G. Switching back to a lower capability such as GPRS & EDGE etc is a last resort for the modem. If locked exclusively on 3G, the alternative is not having a network connection at all!

---

### Post by GeorgeVita on 2009-08-11
Hi **londonbabs** and **Macchi**,
searching internet I found an 'extracted' info for Huawei modems:

```
AT^SYSCFG=13,1,3FFFFFFF,2,4 # GPRS only
AT^SYSCFG=2,1,3FFFFFFF,2,4 # GPRS prefered

AT^SYSCFG=14,2,3FFFFFFF,2,4 # 3G ONLY
AT^SYSCFG=2,2,3FFFFFFF,2,4 # 3G prefered
```

I tested the above using **wvdial** (my 'All weather' method to connect) and GPRS only (as I never had the 3G > GPRS problem). I can state that my E169 was always in 'green led' sssslllloooowwwww internet connection! (this message posted via GPRS network)

I am leaving other tests for you...

Regards,
George

---

