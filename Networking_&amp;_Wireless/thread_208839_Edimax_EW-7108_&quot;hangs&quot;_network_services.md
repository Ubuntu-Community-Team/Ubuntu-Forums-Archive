---
title: "Edimax EW-7108 &quot;hangs&quot; network services"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by soofsoof on 2006-07-04
After a lot of searching, I bought the Edimax EW-7108PCg wireless card. It should have worked 100% on linux.

Indeed, when I first inserted it and booted up the system I saw the "activity" light on the card blinking, all looked well, I saw that the rt2500 was loaded, and even manged to connect to a network - the "link" light turned on, the dhcp request was answered by the network, I got an IP an DNS entries - all looked great.

The specific network required MAC authentication: it identified the MAC address of my card, asked me for my password (not a "network" password, just a one confirming I am a student there) and I was told that registration for the network is complete, and I have to restart my computer.

When restarting, the lights on the card did not blink, there was no activity at all, as if the card is "dead". Moreover, the card somehow made the whole networking services get "stuck" - I cannot open system->networking, kill or restart the dhclient, connect using my ethernet - nothing. The computer is 90% stuck.

It is needless to say that if I reboot without the wireless card everything is working well. Even if I boot from a live CD WITH the wireless card -all is well, the card is identified and active...

It seams like something in my network configuration/services was changed after first connecting successfully to a wireless network and ever since pluging in the wireless card (or booting up when it is inside) makes the whole system get stuck.

Any ideas?

---

