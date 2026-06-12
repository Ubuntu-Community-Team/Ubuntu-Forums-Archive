---
title: "Ssh vnc"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by baddnady23 on 2010-09-03
When configuring my remote desktop preferences, it says that my machine is only viewable to the local network... Does this mean that I can't SSH into it from the outside and if so, how do I fix is so that I can....

---

### Post by Iowan on 2010-09-03
Do you have port-forwarding set up on your router?

---

### Post by baddnady23 on 2010-09-03
> **Iowan said:**
> Do you have port-forwarding set up on your router?

Yes I do

---

### Post by CharlesA on 2010-09-03
You can ssh into it (and create a tunnel for port 5900) then connect to it via 127.0.0.1:5900.

Opening VNC to the internet is a bad idea, even if you set it up so that you have to allow the connection attempt.

---

