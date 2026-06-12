---
title: "RF_KILL setting, need to edit."
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by Bobblybook on 2009-02-07
Hi everyone!

I haven't been able to get my wireless working since I installed ubuntu. I am using an intel ipw2100 card (integrated). I have tried both the linux and windows (via ndiswrapper) drivers, neither of which helped. Using the windows drivers, I could right click the LAN icon and check "enable wireless" but that didn't do anything either. Using linux drivers I couldn't even do this. However, with ndiswrapper the wireless LED stayed off - with linux drivers this light is on.

I've found out that RF_KILL is set to 2 (hardware radio off) and I believe this is what's causing me to have no wireless. My wireless button is a toggle, yet it doesn't work under linux. Is there any way for me to manually set the RF_KILL setting to 0?

EDIT: FIXED. Using linux drivers and typing these commands in a terminal:

sudo modprobe fsam7400
echo 1 > /proc/driver/wireless/radio
modprobe ipw2100

while I'm not using a fujitsu notebook, this was suggested in another forum somewhere and it does in fact work (it didn't work when I tried it earlier using linux drivers only).

---

