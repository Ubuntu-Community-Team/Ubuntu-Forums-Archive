---
title: "Proprietary b43 driver won't activate"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by oiler920 on 2009-12-24
I have a Dell Latitude D600 with a Broadcom BCM4306 (rev.02 14e4:4320) wireless card inside. It is supported by the b43legacy driver (according to the project's website). When I try to activate it in Hardware Drivers, it doesn't work. A window with a progress bar pops up for a second, then disappears. When I reboot to see if it worked, it's still marked unactivated.

---

### Post by focwiz on 2009-12-24
> **oiler920 said:**
> I have a Dell Latitude D600 with a Broadcom BCM4306 (rev.02 14e4:4320) wireless card inside. It is supported by the b43legacy driver (according to the project's website). When I try to activate it in Hardware Drivers, it doesn't work. A window with a progress bar pops up for a second, then disappears. When I reboot to see if it worked, it's still marked unactivated.

Try downloading and installing the Broadcom STA wireless drivers.  That's what I had to do to get my Broadcom wireless working.

---

### Post by oiler920 on 2009-12-24
Never mind; I found the solution buried in the documentation. They should really tell the user what to do rather than make them dig through the ONLINE docs. I mean, nearly all laptops sold today have either Intel, Atheros, or Broadcom Wi-Fi chipsets. Intel drivers are great, most Atheros chips are good, but Broadcom chips have always been in a sorry state. Let's hope the community (or at least Ubuntu's maintainers) get their act together. </rant>

Anyway, here's that doc page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

