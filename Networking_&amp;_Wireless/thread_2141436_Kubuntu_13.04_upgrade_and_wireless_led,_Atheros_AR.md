---
title: "Kubuntu 13.04 upgrade and wireless led, Atheros AR8152"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by B&amp;Co on 2013-05-02
Hi everybody,
I've just switched to Kubuntu 13.04 from 12.10 and i notice that the wireless led of my asus 1011 netbook does'n work. The wireless interface seems to work correctly because i can turn it on and off using the fn+F2 hotkey but the indicator led doesn't turn off.

i don't even undersand where the problem is; kernel? acpi?
i have an Atheros wireless card (AR8152).

thanks

---

### Post by chili555 on 2013-05-02
Are you sure AR8152 isn't ethernet? What does this tell us?```
lspci -nn | grep 0280
```

---

### Post by B&amp;Co on 2013-05-02
You're right chili555, i red the wrong part of lshw. My wifi card is a  AR9285 (PCI-express)
here the lspci output

```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

Anyway... is my problem a wireless card problem? I mean: isn't the wifi led managed by the os?

---

### Post by chili555 on 2013-05-02
> is my problem a wireless card problem? I mean: isn't the wifi led managed by the os? It's complicated. There is usually a laptop-mode or similar module that converts all the laptop key presses, Fn+F10, for example, into action the kernel can use. It's referred to as laptop-mode because such things are unique to laptops and not desktops nor tablets, phones, Raspberry Pi, etc. Also, some, not all, drivers have a method to change the behavior of the LED. Your wireless driver is among them:> $ modinfo ath9k
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     99BC2D0E2F8B67646D6C273
<snip>
parm:           nohwcrypt:Disable hardware encryption (int)
[COLOR="#FF0000"]parm:           blink:Enable LED blink on activity (int)[/COLOR]
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)That may, in fact, not be what you are looking for, but let's test it temporarily:```
sudo modprobe -r ath9k
sudo modprobe ath9k blink=1
```Any improvement?

Let's see which of the several laptop-mode modules are loaded for your machine:```
lsmod | grep asus
```

---

### Post by B&amp;Co on 2013-05-02
Thanks for your reply chili555!
Unfortunately the modprobe command seems to have no effect. The hotkey still works but the led does not change. I also tried to change the blink option to "0". No changes anyhow...

that's the output of the lsmod
```
$ lsmod | grep asus
asus_wmi               23517  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
video                  18894  2 i915,asus_wmi
wmi                    18590  1 asus_wmi

```

---

### Post by chili555 on 2013-05-02
Sadly, asus-wmi gives us no options:> $ modinfo asus-wmi
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/platform/x86/asus-wmi.ko
license:        GPL
description:    Asus Generic WMI Driver
author:         Corentin Chary <corentin.chary@gmail.com>, Yong Wang <yong.y.wang@intel.com>
srcversion:     62CA511243680BE13E8641A
depends:        sparse-keymap,wmi,video
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversionsI am sorry, I know of nothing else to try.

---

### Post by B&amp;Co on 2013-05-03
Thanks anyway! I'll make some more searches...

---

### Post by B&amp;Co on 2013-05-03
SOLVED!!
I just added
```
acpi_osi=Linux
```
to the /etc/default/grub file.
Now the wifi led turns on and off accordingly to the hotkey press.

Unfortunately the hotkey for disabling the touchpad doesn't work now... I'll investigate...

---

