---
title: "Wireless only works with liveCD"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by KLineD on 2006-04-11
Hello!

I recently bought a wireless router and wireless lan card. My wireless card is a SMCWPCI-G and I see [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards") that it's supported out of the box.

When I boot using the Dapper LiveCD Flight 6 I get a wireless configuration widget in the top menu bar and I can connect just fine. My card is recognized as at0 and I can browse the web and see the other computers in my network.

However when I installed the LiveCD to my computer, Ubuntu doesn't recognize the card. I ran update-pciids as suggested in the [Wireless Network Card page]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards") in the Ubuntu Wiki but to no avail.

I don't know if the fact that my /home directory is from my previous Ubuntu installation has anything to do with it (I didn't formatted /home and it kept all my settings).

---

### Post by KLineD on 2006-04-12
Never mind, seems that the new LiveCD installer from Dapper Flight 6 is not working correctly with my computer, as not only the wireless was not working but also the keyboard and hostname were left as default.

I installed my system with the normal installer in flight 5 and the card got detected by the installer. DHCP failed but once I manually configured it, everything went smooth.

---

