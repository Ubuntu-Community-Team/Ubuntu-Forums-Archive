---
title: "Belkin F5D7050v4 working in Ubuntu Karmic"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2009-11-12
Despite the problem with my connection fading out, Ubuntu Karmic can support it. The Belkin F5D7050 v4 USB adapter can be patched with this driver: [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

In order to get it working, download the latest 'build-essential' from synaptic. Untar the file. Open a terminal and 'cd' to the untarred directory. Then type:
'make'
(if no errors), type 'make install'
then, type 'make unload'
finally type 'modprobe zd1211rw'

Run 'iwconfig' to verify that wlan0 pops up and you're good to go.

If an admin with wiki access could up-date this section: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB)
The USB wireless device is listed under the last entry.

---

### Post by gordonreid1992 on 2009-11-21
looks great, any idea which driver i should use for a Belkin F5D8001?

---

### Post by espressobeanie on 2010-01-31
No clue. Try googling it and maybe you can find the manufacturer. The version number is on your USB stick or whatever, and it's in very small print.

---

