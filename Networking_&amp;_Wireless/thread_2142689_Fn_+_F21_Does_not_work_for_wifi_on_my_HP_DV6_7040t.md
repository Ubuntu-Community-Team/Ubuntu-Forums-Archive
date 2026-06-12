---
title: "Fn + F21 Does not work for wifi on my HP DV6 7040tx"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by vikkyhacks on 2013-05-06
I use this laptop
[COLOR=#000000][FONT=verdana]http://h10010.www1.hp.com/wwpc/in/en/ho/WF06a/321957-321957-3329744-64354-64354-5226230.html?dnr=1

[/FONT][/COLOR]
I installed **bcmwl-kernel-source** driver for my BCM4313 and I am able to connect to the any wifi network. But I cannot disable/enable the wifi using the Fn+F12 key. It usually stays white when on and orange if off. But no matter how many times I press Fn+F12 it always stays white. If I click on disable wireless networking from unity or gnome panel then the color goes orange. The software on unity is able to change the indicator color of the wifi but the hardware switch (Fn+F12) does not work.


[psycho:~] $ lspci | grep BCM0a:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

---

### Post by praseodym on 2013-05-06
Please check:
```

lsmod
rfkill list
```

---

### Post by vikkyhacks on 2013-05-06
lsmod -> output is at [http://pastebin.com/brZAr0vg](http://pastebin.com/brZAr0vg)
```
1z [psycho:~] $ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



```

---

### Post by praseodym on 2013-05-07
Try to unload this module on the fly:

```
sudo rmmod hp_wmi
```

---

### Post by vikkyhacks on 2013-05-08
I tried ```
rmmod hp-wmi
``` but that did **NOT WORK. **I even went to the extent of adding that driver to my blacklist.

```
nano /etc/modprobe.d/blacklist.conf
blacklist hp-wmi
```

---

