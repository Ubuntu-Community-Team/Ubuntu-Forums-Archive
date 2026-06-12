---
title: "Help with wireless network adapter"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by tj.chambers89 on 2009-05-03
Hi all,
Im new to linux so bare with me lol.
 I just installed Linux ubuntu on my desktop, Simply because i hate windows, and im too cheap to spend thousands on a mac.

My question is that i have a Wireless network card in stalled on my desktop, made by "D-Link" . The model number is "WDA-1320". I cant seem to find anyway of getting it to work with Ubuntu. I have another laptop in the house with windows on it. I used it to go to d link's website and check for a "linux driver" but couldn't find one.

Can anyone offer any tips, pointers or support?

Thnx.

---

### Post by chili555 on 2009-05-03
According to this: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)  your card uses the Atheros 5005G chipset. Please try opening a terminal (Applications -> Accessories -> Terminal) and type:```
sudo modprobe ath_pci
iwconfig
```Do you now see a wireless interface? Can you click the Network Manager icon on the upper right, see your network and connect?

---

### Post by RedSingularity on 2009-05-03
If the above doesnt work post the output of "lspci" just to verify the chipset.

---

### Post by pi3832 on 2009-05-03
> **Shadow121 said:**
> If the above doesnt work post the output of "lspci" just to verify the chipset.

If it doesn't work, then you might-could post all the info listed in:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

