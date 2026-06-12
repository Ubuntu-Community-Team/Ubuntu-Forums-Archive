---
title: "nfs bad encoding"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by timmson on 2009-04-04
Hello!
I have some trouble... I have router Asus Wl-500g and USB-HDD WD 500 GB.
When i connect my hdd to usb directly, encoding is right.
When i mount muy hdd over nfs from my router, russion character is bad.
How to solve this problem?

---

### Post by kreggz on 2009-04-04
Try and use scp to see if it does the same. 

You could try lowering your MTU to 1300...

---

### Post by timmson on 2009-04-04
scp have a same result(

---

### Post by kreggz on 2009-04-04
If you are trying to connnect over the WAN, does lowering your MTU size help?

---

### Post by timmson on 2009-04-04
No, i trying only in my local network

---

