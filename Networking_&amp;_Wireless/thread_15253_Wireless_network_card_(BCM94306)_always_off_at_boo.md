---
title: "Wireless network card (BCM94306) always off at boot"
date: 2005-02-13
forum: Networking &amp; Wireless
---

### Post by petehall on 2005-02-13
Hello. I wonder if anyone could help me. I've managed to set up and configure my wireless network card (detected as Broadcom BCM94306) and that's all working fine, apart from the fact that every time I turn on the computer, it isn't switched on (LED on the back not illuminated).

Once I'm logged in, I have to run sudo modprobe ndiswrapper, and then go into the Network Settings dialog, disable the Ethernet LAN card, and re-enable the Wireless LAN card to get it to work.

Thanks.

---

### Post by grj on 2005-02-13
Try adding ndiwrapper to /etc/modules.

---

### Post by petehall on 2005-02-13
Works beautifully. Thanks very much.

---

