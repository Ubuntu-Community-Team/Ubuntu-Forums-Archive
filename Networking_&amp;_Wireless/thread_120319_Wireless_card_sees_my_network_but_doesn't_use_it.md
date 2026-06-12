---
title: "Wireless card sees my network but doesn't use it?"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by Brian Kendig on 2006-01-21
I have a secure wireless-B network, and I just picked up a Zyxel ZyAir G-102 wireless card for my laptop and I'm trying to get it to work with Kubuntu 5.10. It *almost* works, but I could use help figuring out the part that I'm missing!

I have to go into a terminal first and run 'ifconfig ath0 up', otherwise KWiFiManager will crash with a segmentation fault. ('ifup ath0' also finds it properly, but wastes time on a bunch of DHCPDISCOVERs that don't find anything.)

I then go into KWiFiManager, click 'Scan for Networks', and it lists the one I want; I change the entry in the 'WEP' column from 'on' to the password and I click 'Switch to Network', it asks me for my root password, then KWiFiManager shows me a green bar which I take to mean that I'm connected.

But the laptop won't actually use the wireless network; I can't ping anything.

What step am I missing, what else do I do to get Linux to use my wireless network?

---

### Post by kasemodz on 2006-01-21
what chipset are you using? I had a realtek rtl8185 chipset and I tried everything but I had the same exact problem as yours. Somehow when I did dmesg it always said no ip-v6 routers found. I somehow have a strong feeling that may be causing all the problem. I disabled it but I still couldn't get it to work. You can try though. Remember to post back if it works.

---

