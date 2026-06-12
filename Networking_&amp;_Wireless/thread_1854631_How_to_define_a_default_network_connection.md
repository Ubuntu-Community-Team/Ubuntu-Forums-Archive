---
title: "How to define a default network connection???"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by Neoracu on 2011-10-04
Hi.

I'm running 10.04 dual boot with XP My main OS is Lynx I have XP only for task involving my job, using UBUNTU since 8.04.

Want to share my internet connection to my PS3, did it in the past using Firestarter, now is not working anymore bought a Router and I can get ICS in XP but not anymore in Lynx(and as I prefer Ubuntu is annoying to have to boot into windows to make the ICS), I'm using a USB modem to get Internet.

Internet > Laptop > Router > PS3 - Printer.

Happens that when I connect the eth0 to the router, the modem to the laptop and the wireless to the router I got no internet connection because Network Manager takes the wireless as a 'default' once I disconect from the wireless I got internet connection again and the ppp0 is the 'default' connection. I want to get the three conections so I can use my wireless printer.

This what I have now and have to disconnect the wireless to get internet:

ppp0
eth0
wlan0(default)

What I want is:

ppp0(default)
eth0
wlan0

I just can't find a way to set my ppp0 as a default when I have the three connections up and running.

Is there anybody who can give me a hand

---

