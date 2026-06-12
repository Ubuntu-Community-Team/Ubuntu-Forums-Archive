---
title: "Cannot connect to WPA networks using Trendnet 421pc wifi card."
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by benoitcsirois on 2008-12-28
Actually the title is a bit misleading. It works *every once in a while*.

Distro: Xubuntu 8.10
Router: Dlink 614+
Encryption: WPA2
Card: Trendnet 421pc C1.xR
Chipset: RTL8185
Driver: ndiswrapper (tried both Realtek and Trendnet's XP drivers, have also tried the driver automatically loaded by kernel, I think it was rtl8180)
Connection manager: Gnome network manager
*edit*: wpa-supplicant is installed.

Problem: I can't seem to connect to WPA-protected networks. :( But for some reason, sometimes when I switch from wired to wireless, it starts working. It only worked on a few occasions, I cannot voluntarily reproduce the conditions to make it work. It *appears* to be random.

I strongly suggest you do not purchase this card if you plan on usng it with Ubuntu. I have wasted about 6 hours on this problem and have yet to find a solution.

I have not tried WEP. WEP sucks anyways.

--
Ben

---

### Post by jayrix on 2008-12-28
I just changed channel on my router and it worked perfectly .. was default on 13 switched it to 1 and my wireless was suddenly there :D

and i know several people doing this with success.

---

