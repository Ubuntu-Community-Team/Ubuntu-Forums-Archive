---
title: "[SOLVED] 8.10 on DEll Desktop hangs during boot with Belkin F5D7000uk"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by kunnagh on 2009-01-05
Despite [what this link says]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCI") about the Belkin F5D7000uk (Ver 7021uk), I have spent two frustrating days trying to get it to work under 8.10.  The card works perfectly on the same PC when I boot into XP.  This card uses the Realtek 8185 chipset.

Initially, with Network Manager installed, it caused a hang just before the username screen appeared, while the circular 'waiting' cursor was displayed.  I tried using ndiswrapper, using various suggestions from this an other forums, to no avail - the driver 'net8185' is present, but the boot still hangs.  Removing the card enables the PC to boot properly, having it installed whilst booting causes the hang.

Eventually, I removed Network Manager and tried to use network-admin instead.  This time, the PC booted fine with the card in.  It was then visible in lspci (as wireless Belkin device 1799:700f, as expected) and also in iwconfig.

Running network-admin showed the interface as an option but as soon as I configured the wireless device and clicked 'OK' to save the settings, the PC froze completely.

After a restart, the wireless card is again deselected, and reconfiguring it causes a freeze every time.

Attempting to configure it by using iwconfig and editing /etc/network/interfaces manually (adding auto wlan0 and iface wlan0 inet dhcp lines) caused the PC to hang on boot again, this time with the orange bar almost halfway across the startup screen.  Attempting a 'restore' boot causes the hang again, with 'Starting network interfaces' or some such as the last action of the boot before the hang...

I'm at a bit of a loss.  The hardware seems fine (because of the XP working OK thing), the drivers are the up-to-date ones and yet I cannot get an active card and a working booted PC at the same time.

There's a forehead-shaped dent in my desk as well.  Does anyone have any ideas...? :(

Thanks in advance...

---

### Post by kunnagh on 2009-01-06
Actually - never mind - after two days of struggling, I found [these instructions]("http://spikeymikey.net/2008/11/04/belkin-f5d7050/"), some of which I had already done, but not in the order suggested here.  I still had to remove Network Manager and use network-admin, but the rest of this worked fine, and now the wireless network is flying.

---

