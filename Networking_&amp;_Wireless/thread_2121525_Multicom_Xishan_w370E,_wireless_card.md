---
title: "Multicom Xishan w370E, wireless card"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by zeneca97 on 2013-03-02
Okay, so I'm new here. I've just installed Ubuntu at this pc (laptop, multicom Xishan w370E) along with Windows 7 which I've had for a long time. I'm trying to get my wireless card to be detected, but all I see is wired network, and that works fine. I'm bit of a noob to computers, especially Ubuntu and linux, so if someone could guide me it would be helpful. Is there something I could do? Thanks. :)

---

### Post by mamamia88 on 2013-03-02
I googled your laptop with wireless and one of the first results was [http://askubuntu.com/questions/262357/realtek-8192ce-wireless-driver-install-to-multicom](http://askubuntu.com/questions/262357/realtek-8192ce-wireless-driver-install-to-multicom) So i'm going to assume that is the card you have correct?  2 useful commands that might help you a little are lspci and lsmod.  lspci lists devices which probably includes your wireless card.  You can't fix it without knowing the exact model.  lsmod lists kernel modules loaded. See if there is anything that looks like it could be your wireless driver.

---

