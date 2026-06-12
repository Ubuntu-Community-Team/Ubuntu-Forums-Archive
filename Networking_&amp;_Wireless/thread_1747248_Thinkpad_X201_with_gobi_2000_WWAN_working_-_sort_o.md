---
title: "Thinkpad X201 with gobi 2000 WWAN working - sort of"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by mattpatey on 2011-05-02
Hi,

I'm running ubuntu 11.04 (32-bit) on a Lenovo X201 with Gobi 2000 wwan card. I have got it working by installing gobi-loader and copying the three firmware files from my Windows installation, but there are a couple of quirks that I am hoping someone can help me with.

When the computer is switched on, and the wwan is switched off, clicking "Enable Mobile Broadband" switches on the indicator LED, everything works fine and I can connect. However, if I then try to switch off the wwan using the same menu, the wwan seems to be deactivated, but the indicator LED remains on. Once in this state, the WWAN remains switched on even after rebooting. It can be reset by rebooting into Windows, turning it off there, and then booting back into Linux.

This isn't a great problem, but the system seems to use more power after activating and it would be nice to be able to control it a bit better. I have found that by using the command "rfkill block wwan" I can switch off the wwan completely, but for some reason it is not possible to re-enable it using the menu (only "rfkill unblock wwan" works)(it is possible to re-enable bluetooth/wifi using the GUI after issuing the appropriate rfkill command).

I'm not sure whether I should just report this as a bug, but if anyone has any ideas I will be grateful to hear them.

---

