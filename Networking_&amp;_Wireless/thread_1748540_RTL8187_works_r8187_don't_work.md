---
title: "RTL8187 works r8187 don't work"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by _Matt_ on 2011-05-03
Hi everybody!
I use Ubuntu Maverick 10.10 and i have also BackTrack 4 RC2.
I have this problem: i want to learn to use aircrack trying to crack my wireless network. I have a wireless card with RTL8187b chipset.
I followed this guide: [http://www.janoweb.net/tutorials/installazione-drivers-rtl8187-r8187-rt2800usb-su-ubuntu-lucid-maverick.html#axzz1Ky4yqrfA](http://www.janoweb.net/tutorials/installazione-drivers-rtl8187-r8187-rt2800usb-su-ubuntu-lucid-maverick.html#axzz1Ky4yqrfA) to install patched drivers, both RTL8187 and r8187, i blacklisted file as is written in the guide and i activated only the RTL8187 and the wireless card works but this driver is not good for injection. So i activated r8187 one but using "iwconfig" the wifi card is not seen by the system so i don't have the name of the card to use with aircrack.
Using BT, where drivers are installed patched, i have the same result.
Using airdriver i can see that is loaded only the mac80211 stack and i can't load ieee80211 stack but i don't know if this is the problem.

I hope someone can help me :)

---

