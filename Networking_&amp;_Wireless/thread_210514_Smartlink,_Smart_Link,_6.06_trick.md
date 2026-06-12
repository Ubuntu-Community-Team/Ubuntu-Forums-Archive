---
title: "Smartlink, Smart Link, 6.06 trick"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by Omnios on 2006-07-07
Hi my dad has a Smartlink es 2838 2839 modem. With Ubuntu 5.10 his port was port 14 and he tryed to set it up using his old port to connect which did not work. Anyways after doing some problem solving I got him to run the following command in the Terminal.
```
 $ sudo wvdialconf /etc/wvdial.conf
```

 Which told him the modem was now on port 4, after figuring this out his modem worked again without the addition of any extra drivers.

---

