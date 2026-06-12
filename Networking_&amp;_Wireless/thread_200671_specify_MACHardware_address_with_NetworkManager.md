---
title: "specify MAC/Hardware address with NetworkManager?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by netztier on 2006-06-20
Hi all!

For some wireless networks I'm using, I need to configure another MAC/Hardware address for my atheros based card other than the "burn-in address".

With /etc/network/interfaces, it was possible to configure the address directly there. But using NetworkManager, one has to uncomment all configuration options for NICs to be managed by NetworkManager.

So where can I specify the hardware or MAC address with NetworkManager?

thanx & kind regards

Marc

---

### Post by netztier on 2006-06-23
Finally, I found **macchanger** which does the trick perfectly 
for me. Installed it with *aptitude install macchanger* and whenever I need to 
change the hardware address, I do this:

[LIST]
[*]disable wireless in NetworkManager
[*]**sudo macchanger -m xx:xx:xx:xx:xx:xx ath0 **on a console
[*]enable wireless in NetworkManager
[*]use new MAC address
[/LIST]


kind regards

Marc

---

