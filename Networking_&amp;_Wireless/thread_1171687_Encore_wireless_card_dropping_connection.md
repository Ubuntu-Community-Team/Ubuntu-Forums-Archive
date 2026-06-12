---
title: "Encore wireless card dropping connection"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by weazoe on 2009-05-27
I installed an Encore ENLWI-N wireless PCI card. Ubuntu detected it and connected without a problem. However, the card drops the network on a random (but typicaly daily) basis. I have to restart the system to pick it up again. I installed the driver from the Encore website and no change. Can anyone tell me how to determine if the problem is with the card or with my system?

Thanks for any answers,
Weaz

Ubuntu 9.04
AMD processor
Asus MoBo

---

### Post by OzOle on 2009-06-01
Hi weazoe,

I have a similar problem and searching through the Ubuntu forum I discovered that many are reporting similar problems. You should report it as a bug in Launchpad so that the developers can work on the problem.

After a lot of experimenting I discovered that in my case the wireless connection drop when the screen saver/power management switches the screen to blank screen. After I changed the setting to not blank then the wireless did not disconnect. We have different hardware, so I don't know if changing the setting will get you around your problem, but you could try it.

---

