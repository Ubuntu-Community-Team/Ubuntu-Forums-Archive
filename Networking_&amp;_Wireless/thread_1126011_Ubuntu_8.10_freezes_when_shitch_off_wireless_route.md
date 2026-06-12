---
title: "Ubuntu 8.10 freezes when shitch off wireless router"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by x4444 on 2009-04-15
Ubuntu 8.10
Laptop Dell Vostro 1000
Broadcom STA wireless driver

Westell 7500 wireless router. Default Verizon setting. WEP.

if I switch off wireless router. Ubuntu freezes. (CapsLock and NumLock leds start blinking). Nothing helps. Only press power button for 4 sec.
Seems that it is bug in wireless driver.

How can I give you more information to analyze. dump? stacktrace?

---

### Post by Floppyjoe on 2009-04-15
Have you tried Ctrl-Alt-Backspace or Ctrl-Alt-Delete when that happens?

---

### Post by x4444 on 2009-04-16
I moved to b43 driver. Much more stable.
1. b43 does not freeze Linux if I switch off wi-fi router
2. Always up wireless interface on start.
if I not properly shutdown Linux, STA does not start wireless adapter next time I boot. So I need to start Windows first, windows switches on wireless. Then reboot to Ubuntu. Only after that STA starts wi-fi adapter.

---

