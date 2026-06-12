---
title: "Can't connect wireless on new install."
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by Holyalchemy on 2013-02-13
Hi all,

I've recently installed 12.10 on my HP elitebook laptop. When I try to connect my wireless I keep getting prompted to enter the wireless key. At first I thought I was dumb and couldn't type so I copy and pasted from the router into the field and it's still refusing it. Sits on connecting, then pops up with Wireless Network Authentication Required. I've checked the characters and they're matching the router. Any ideas what I've gotten wrong here?

Thanks,
HA

---

### Post by Warren Hill on 2013-02-14
The fact that it is asking for a password says its connecting but the fact it needs it over and over again suggests the connection is being lost.  Perhaps due to interference from other peoples network 

If you run

```
sudo iwlist scan
```

In a terminal this will tell you what other signals there are nearby.  If you find any using the same or adjacent channel number as you then try changing the channel number in your router.  There is usually a web page interface for this and the documentation that came with your router will tell you how to change the channel.

-------------
If this fixes your problem don't forget to mark the question solved.

---

### Post by Holyalchemy on 2013-02-27
I've run that, it only sees my wifi router on channel 12. I changed it to one, ran it again, and saw another router. Moved it to 6, and tried connecting again, still getting the same popup for passwd.

---

### Post by Bucky Ball on 2013-02-27
*Thread moved to **Networking & Wireless**.*

---

