---
title: "Acer 6530G Sound coming though headphones and speakers"
date: 2011-06-18
forum: Multimedia Software
---

### Post by jonny3010 on 2011-06-18
Acer 6530G Sound coming though headphones and speakers
How do i make it only headphone when pluged in

Jonny

---

### Post by lidex on 2011-06-18
You could do a search, or I could make it easy for you.
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=acer-aspire-6530g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by jonny3010 on 2011-06-19
Thanks that fixed the problem

---

### Post by Yellow Pasque on 2011-06-19
Please mark thread solved.

---

