---
title: "Realtek 8187b problems with 8.10"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by chevyvan10 on 2008-12-26
Ok... I've got a problem.

Last night I installed Intrepid on my old compaq laptop. The install went fine, everything works well... I just can't get my wireless card to work. Its a USB dongle style rtl8187b based card. I've tried for hours to get it to work, with no luck. 

The problem I'm running into is when I'm trying to connect to my WEP enabled network, it connects to the router, but times out before I can get assigned an IP address (which seems to take about a minute). Initially I thought it was a problem with the network manager, so I tried using Wicd. Just like network manager, it got stuck at the part where its requesting an IP address.

I've tried using Ndiswrapper with the win98 driver, and I've used the driver in the stock kernel... both with the same result. In the past, I've gotten this card to work flawlessly with Ndiswrapper on 8.04. I'm starting to run out of ideas. This SHOULD be working. This card definately works on my OSX86 machine, so I don't think its a physical defect with the card. Thanks everyone!!

---

### Post by AlexBellisBrown on 2008-12-26
I have the same wireless card. Have you noticed if the signal is lower in Ubuntu than with Mac? Also, if you have had it working in Ubuntu, did the connection drop from time to time? Could you post the outcome of lsusb from the terminal, just to be sure of the card?

---

