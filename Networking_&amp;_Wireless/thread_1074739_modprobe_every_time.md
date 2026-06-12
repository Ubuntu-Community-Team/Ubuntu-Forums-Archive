---
title: "modprobe every time"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by jtmedin on 2009-02-19
Finally got my rtl8187 wireless going but now i find i must 'sudo modprobe rtl8187' each time i boot. How do i make that perminate? BTW my notebook also has broadcom wireless built in but it doesnt work so had to get a rtl8187 dongle.

---

### Post by kevdog on 2009-02-19
echo rtl8187 | sudo tee -a /etc/modules

That will do it!

---

### Post by jtmedin on 2009-02-23
Ok thanks that does it.

---

