---
title: "My Braodcom wireless just stopped working?"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by Hazelip on 2009-12-10
It was working last night, but when I brought it out of hibernate this morning, it no worky on my HP Pavilion DV6000.  I'm stumped.

It's acting like it doesn't even see the wireless NIC.  As a noob, can someone point me to a way to verify that my OS (9.04) can even see the wireless NIC?

Thank you very much,
Jake

---

### Post by bkratz on 2009-12-10
> **Hazelip said:**
> It was working last night, but when I brought it out of hibernate this morning, it no worky on my HP Pavilion DV6000.  I'm stumped.

It's acting like it doesn't even see the wireless NIC.  As a noob, can someone point me to a way to verify that my OS (9.04) can even see the wireless NIC?

Thank you very much,
Jake

The easier way would be to type   (in the terminal)

lspci | grep Wireless              (LSPCI in lowercase)

or  

if you don't see anything just lspci

---

### Post by Hazelip on 2009-12-10
Great.  Looks like my Broadcom died...

---

