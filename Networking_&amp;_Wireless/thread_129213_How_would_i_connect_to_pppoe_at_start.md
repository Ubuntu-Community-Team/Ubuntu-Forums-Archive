---
title: "How would i connect to pppoe at start"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by %hMa@?b&lt;C on 2006-02-13
I have DSL and conect with PPPoE i would like it so that i connect at boot, and also run this
sudo ifconfig lo localhost  
is that possible to do  and how?

---

### Post by mips on 2006-02-13
Somewhere towards the end of the pppoeconf utility is an option that says "Your PPPD is configured now. Would you like to start the connection at boot time", Yes or No.

Could probably enable it via a config file or menu somewhere.

---

