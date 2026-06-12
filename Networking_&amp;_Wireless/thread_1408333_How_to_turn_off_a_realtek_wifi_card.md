---
title: "How to turn off a realtek wifi card?"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by AlexZaim on 2010-02-16
Hello, i have a realtek 8191se wifi card.

I have downloaded the driver installed it, and it works fine. But i can't get to turn it off. I do have the ability to unload the driver's kernel modules and the sysyem does not see my card after that. That's ok, but i'm thinking it still uses my battery power. The wifi led is always on no matter what i do. The fn+<wifi key> doesn't to anything.

So how can i turn off my wifi card?

---

### Post by chewearn on 2010-02-16
I have an eeepc 900.  I turn off the built-in wifi by:
```
echo 0 >/sys/devices/platform/eeepc/wlan
```and turn it on by:
```
echo 1 >/sys/devices/platform/eeepc/wlan
```It is possible, your set-up has a similar path for this.

Note:
The actual turn on/off script has a series of modprobe commands to load/unload modules.  The echo 0/1 above is only the final hardware switch toggle.

---

### Post by AlexZaim on 2010-02-27
```

$ locate wlan
/lib/modules/2.6.31-19-generic/kernel/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.31-19-generic/kernel/drivers/staging/wlan-ng
/lib/modules/2.6.31-19-generic/kernel/drivers/staging/wlan-ng/prism2_usb.ko
/usr/local/src/rtl8192se_linux_2.6.0014.0115.2010/ifcfg-wlan0
/usr/local/src/rtl8192se_linux_2.6.0014.0115.2010/wlan0dhcp
/usr/local/src/rtl8192se_linux_2.6.0014.0115.2010/wlan0down
/usr/local/src/rtl8192se_linux_2.6.0014.0115.2010/wlan0up
/usr/share/app-install/desktop/kwlan.desktop
/usr/share/app-install/icons/kwlan.png
/usr/src/linux-headers-2.6.31-17/drivers/staging/wlan-ng
/usr/src/linux-headers-2.6.31-17/drivers/staging/wlan-ng/Kconfig
/usr/src/linux-headers-2.6.31-17/drivers/staging/wlan-ng/Makefile
/usr/src/linux-headers-2.6.31-17-generic/include/config/wlan
/usr/src/linux-headers-2.6.31-17-generic/include/config/usb/net/rndis/wlan.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/wlan/80211.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/wlan/pre80211.h
/usr/src/linux-headers-2.6.31-19/drivers/staging/wlan-ng
/usr/src/linux-headers-2.6.31-19/drivers/staging/wlan-ng/Kconfig
/usr/src/linux-headers-2.6.31-19/drivers/staging/wlan-ng/Makefile
/usr/src/linux-headers-2.6.31-19-generic/include/config/wlan
/usr/src/linux-headers-2.6.31-19-generic/include/config/usb/net/rndis/wlan.h
/usr/src/linux-headers-2.6.31-19-generic/include/config/wlan/80211.h
/usr/src/linux-headers-2.6.31-19-generic/include/config/wlan/pre80211.h

```

I can't locate the needed file.
I also noticed that if i turn off the wifi in windows it stays turned off in linux. Thus some hardware changes that i do in win they affect them in linux too. Even the webcam keeps it's visual effects when i enter linux.

---

### Post by chili555 on 2010-02-27
Please try:```
sudo rfkill block wifi
```Or:```
sudo rfkill block all
```If it works, start it back up with sudo rfkill [COLOR="Red"]un[/COLOR]block etc.

---

### Post by AlexZaim on 2010-02-28
Doesn't work either way. The led is still on and the i can still get signals.

---

### Post by AlexZaim on 2010-03-05
I tried 

```

sudo iwconfig eth1 txpower off 

```

But it doesn't work. It says that operation is not supported. Please, anyone, any more ideas?

---

### Post by AlexZaim on 2010-06-10
I've upgraded to 10,04. This is what i get out of the last command (the rest don't work either)
```
$ sudo iwconfig wlan0 txpower off
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.

```

Please give more advices!

---

### Post by AlexZaim on 2010-06-14
bump

---

### Post by jdonbook86 on 2010-10-27
I would be careful about turning off the internal wifi card/ circuit. My acer latitude 800 has a hardware bridge built in for fast switching between wired and wireless situations. I find that if I turn it off in gnome, all my internet connections go down, including wired. The little light is annoying, but better to have a connection. My external wifi is a usb AE1000 by Linksys. That sucker was also a pain in the *** to get working in v10.10.

---

