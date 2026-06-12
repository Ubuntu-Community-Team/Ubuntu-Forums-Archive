---
title: "wlan2 disappears when laptop turned off."
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by joelgeez on 2013-03-30
When I found out that my internal wireless adapter (Realtek 8197) was limited to no more than g protocol, I purchased a Rosewill RNX-N180UBE wireless adapter. Plugged it into a USB port, told computer to use wireless connection at wlan2. It worked just fine. Green light blinking. Speed good. Web access good. All good. EXCEPT when I turn off computer and restart, 'puter doesn't see wlan2 anymore. If I pull USB cable out of port, I get many lines of code, more than I can write down and I can't capture because computer down.

After some putzing around, the best workaround I've found is to remove USB cable from port when turning of machine. When starting machine, I put USB back in port and all is good once again. I just have to make sure that I've disconnected the wlan0 connection.

So, my question is: How do I keep wlan2 as default connection when rebooting computer?

Sorry to ramble, but new to the whole wireless thing, and not a lot more experienced with Ubuntu 12.04.

Thanks,
J

---

### Post by Hadaka on 2013-03-30
Hi,to edit your connections.
click the wireless icon..upper right
you should see both internal and usb wifi's
click edit connections
click wireless..
click your connection name
click edit
uncheck Connect Automatically...internal wifi
repeat above for usb connection
check  Connect Automatically

---

### Post by joelgeez on 2013-03-30
Hadaka---
Thanks. I had tried that already but I just tried it again, making double sure I was saving at every step. Restarted machine and it still disappeared. Had to reboot a second time, remove cable, etc., etc.

But thanks for responding anyway.
J

---

