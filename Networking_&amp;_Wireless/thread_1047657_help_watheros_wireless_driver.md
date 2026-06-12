---
title: "help w/atheros wireless driver"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by li0id on 2009-01-22
I'm having trouble getting my wireless card to work in ubuntu. im using version 10.8. i followed all the discussing it online and still cant seem to get it to work. I installed ndisgtk and installed a atheros driver i found at the burn the sorbonne site, yet is still isnt working. when i run a iwconfig, it states that there are no extensions. i blacked listed ath-pci, ath-hal, bcm43xx, b43, b43legacy, ssb. i even tried only blacklisting ath-pci and ath-hal and restarting but no use. this is my wireless card i use. ```
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
```

i also have a realtek card.  ```

```02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

could someone tell me what im doing wrong.

and also i have the driver files for my card for windows that i downloaded, but im not sure which inf file to use from there.

thanks in advanced.

---

### Post by li0id on 2009-01-22
bump

---

### Post by kevdog on 2009-01-22
To install the backport modules, just search for it on Synaptic or use apt-get, it's called linux-backports-modules-intrepid. Then on System/Administration/Hardware Drivers make sure Atheros driver is activated. The name of the specific module you want is known as ath5k.

---

### Post by Me! on 2009-01-22
You can use:
[Asus F5RL wireless running steps In fresh Kubuntu 8.04]("http://ubuntuforums.org/showthread.php?t=1047978")

---

