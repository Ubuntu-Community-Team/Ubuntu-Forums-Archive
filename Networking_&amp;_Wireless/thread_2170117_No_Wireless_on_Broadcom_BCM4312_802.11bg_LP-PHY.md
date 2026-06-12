---
title: "No Wireless on Broadcom BCM4312 802.11b/g LP-PHY"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by Dr.Pineapple on 2013-08-24
Hello all.

I am a relatively new user to Linux, and installed the Ubuntu 12.04 on my netbook (Dell Latitude 2100) after having some compatibility issues with another Linux distro I was using. Everything works great, however I cannot seem to get my wireless to work. After a bit of searching, I have tried several suggestions posted on these forums, but none seem to have helped solve my wireless issue. Specifically, I have tried to install new drivers, uninstall and reinstall new / different drivers for my card, yet I still have no wireless. Below you can see my specific wireless card information. Any help that you can give me in resolving this issue would be greatly appreciated! Thank you in advance!

```
-netbook:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
-netbook:~$ lspci -nn -d 14e4:
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

---

### Post by praseodym on 2013-08-25
You only need the missing firmware:
```

sudo apt-get install firmware-b43-lpphy-installer 
```
Remove the STA driver and its config, if applicable:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot.

---

### Post by Dr.Pineapple on 2013-08-25
Hey thanks, Praseodym!

Your suggestions worked perfectly! I appreciated your response and help!

---

