---
title: "MAC Address changing problems - HELP"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by slcsfinest801 on 2012-02-11
Hi guys, I'm having quite a bit of problems changing my MAC.

Here is what I do:

- Disable network services (top right screen)
- Launch terminal
- sudo airmon-ng stop wlan0
- sudo ifconfig wlan0 down
- sudo macchanger -m 00:11:22:33:44:55 wlan0
- sudo airmon-ng start wlan0
- sudo ifconfig wlan0 up

I check my mac address and i see that macchanger has changed it. And I think: cool!

BUT, as soon as I enable the network services (top right screen) and I do a MAC check, the address goes back to the previous one and it doesn't keep the one that i assigned.

What can i do?

---

