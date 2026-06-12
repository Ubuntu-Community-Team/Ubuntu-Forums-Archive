---
title: "Firefox and Evolution"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by boonie rat on 2011-12-01
I just did the latest update on 11.04. The update completed and required a reboot. After the reboot Firefox and Evolution won't connect to the internet. The system connects via wlan1 (hardwire) or wlan1 (wireless), picks up an IP address and correct DNS. I can ping out. Now the weird, I have a virtual XP machine running in Virtualbox, IT CONNECTS TO THE INTERNET !!
Any ideas?

---

### Post by boonie rat on 2011-12-01
I found the issue. The update installed the 2.6.38-13 kernel which hosed me. Rebooted into 2.6.38-12 and all works.

---

