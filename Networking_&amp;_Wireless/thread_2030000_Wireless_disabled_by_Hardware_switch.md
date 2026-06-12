---
title: "Wireless disabled by Hardware switch"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by rickm1945 on 2012-07-20
I have Ubuntu 12.04 on my laptop. My wireless has been working fine until now. When I open to network connection it says "Wireless disabled by hardware switch" Anybody know I can correct this?

---

### Post by kurt18947 on 2012-07-20
Assuming your wireless really isn't disabled by a hardware switch or keyboard F key combination you could try this from an account with sudo privileges:

"sudo rfkill unblock all"

---

### Post by rickm1945 on 2012-07-20
> **kurt18947 said:**
> Assuming your wireless really isn't disabled by a hardware switch or keyboard F key combination you could try this from an account with sudo privileges:

"sudo rfkill unblock all"
Thanks that fixed it.

---

