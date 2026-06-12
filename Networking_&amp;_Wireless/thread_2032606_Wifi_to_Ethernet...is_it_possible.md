---
title: "Wifi to Ethernet...is it possible?"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by Music Guy123 on 2012-07-24
Hi there,

This probably won't work but I am just wondering if it was possible! Can you receive internet via wifi and send it out via ethernet to another device (a raspberry pi, or possibly another computer!)? So basically, you receive from your router with your wifi card and then send the internet down your ethernet cable to another device? The speed of the internet doesn't matter.

Any help would be much appreciated, If you need any more details, please just let me know, I am running Ubuntu 12.04 and Gnome 3!

Music Guy

---

### Post by Music Guy123 on 2012-07-24
Is there a way of doing this? I really need to know because I need to be able to do this tomorrow afternoon! I really hope someone can help.

All the best,

Music Guys

---

### Post by Cheesehead on 2012-07-24
Sure. Network Manager does this.

Edit any wireless connection.
Go into the IPV4 settings tab.
Change the Method from Automatic(DHCP) to Shared to Other Computers

Note that an ordinary ethernet cable may not work. Ordinary ethernet jacks are not the same as bridge/router ethernet jacks. Unless your ethernet port has auto-sensing/correction, you need to use a crossover cable or crossover adapter.

---

