---
title: "Wireless works from terminal but not through Wicd or Network Manager"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by freehunt on 2010-09-09
I'm currently running 10.10, up to date, since it's the only thing I've found that lets me touchscreen work perfectly on my Lenovo IdeaPad S10-3t. However, after installing, things will work fine for a few hours (and a few hibernations, it's a laptop I use for class), then the wireless will refuse to connect. Until today, the only thing I found to fix it was to do a fresh install, but I can't do that every day. A classmate worked a few commands through the terminal that got me online, but not with Network Manager or Wicd. Unfortunately, I am not knowledgeable enough to figure it out on my home network, which is WPA secured (school's network is unsecured, authorized through a browser login).

Now that I know the wireless card is capable of connecting, I want to know why neither of these applications can get connected. lspci sees my wireless card, iwconfig brings back info about the card, my interfaces file looks fine. The card is working, but neither Network Manager nor Wicd can connect, Wicd says it cannot obtain an IP address, if I set it to static, it says it cannot validate the AP. Network Manager runs for a bit, then says disconnected. Wired works fine, but I can't bring an ethernet cable with me everywhere. Can anyone help me figure this out?

---

### Post by grahammechanical on 2010-09-09
Just a guess. Is there a hardware switch, a key press that lets you turn off the wireless card to save battery power? Is wireless being switched off during hibernation but not switched back on? Does it need to be physically switched on after a start-up from hibernation. What is the good of almost instant off and instant on by closing and opening a lid if the battery is flat because some systems are left running. I assume that the back light for the display get automatically switched off when the lid is shut, so why not the wireless card.

Regards.

---

### Post by freehunt on 2010-09-09
I had thought something similar, but I've flicked the switch on and off a few times to see if the wireless would reconnect, and it doesn't. There *is* a switch, but I don't think it's the issue here. Thanks for the reply.

---

