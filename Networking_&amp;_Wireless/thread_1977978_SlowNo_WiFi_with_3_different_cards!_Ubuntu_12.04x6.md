---
title: "Slow/No WiFi with 3 different cards! Ubuntu 12.04x64"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by Bushi86 on 2012-05-11
Hey everyone,

My machine refuses to keep a stable wifi connection, and I'm completely lost.

Ever since I installed Ubuntu, my wifi has been jacked up. It takes forever to connect to the network, and is either unable to connect to the Internet, or is extremely slow whenever it does. The connection also drops every couple of minutes.

I started out with a Rosewill RNX-N300X PCI wifi card (uses the Ralink 2800 PCI chipset), and I searched this forum and the Internet extensively for about a week trying to fix it. I tried a whole bunch of suggestions that I found, but none of them seemed to work. Some would fix it temporarily, but the issues kept coming back.

After smashing my head against the keyboard a couple of times, I decided to try a different wifi card. I ran down to Best Buy and bought a Netgear 802.11n USB stick (it was on sale :P), but had the exact same issues. Since it wasn't faring any better, I went back and returned it the same day.

After searching Google for a card that was known to be fully compatible with Ubuntu, I decided to buy a D-link DWA-556 (uses an Atheros 5xxx chipset). I installed it and booted up, and it was showing up as UNCLAIMED. I did a sudo modprobe ath9k, and the wifi came online. However, I still had slow-to-nonexistent Internet.

Since I was on the verge of becoming suicidal, I decided to boot back into Windows and try again another day. But guess what? Windows was doing the same thing!!! I threw the old card back in to try and see if maybe the new D-link wasn't working with Windows, but no dice...still slow-to-nonexistent Internet!

I've also tried two different routers (both were Linksys WRT300N v1.1, but one of them is running DD-WRT), so I don't think that's the issue. My laptop, a MacbookPro7,1 running OS 10.7.4, has 100% reception on my computer desk, so it's not a problem with range. Wifi on this desktop was running perfectly fine in Windows 7x64 before I added a new SSD and dual-booted Ubuntu. Also, please note that the three different wifi cards used three different connections (one PCI, one USB, and one PCIe). I also updated the BIOS on my motherboard, but that didn't do anything to help the situation.

What on Earth could be causing such madness?? Someone PLEASE help! I'm desperate!

TL;DR - wifi is broken in Ubuntu and Windows, tried 3 different cards & 2 different routers, but nothing works. HELP!

---

