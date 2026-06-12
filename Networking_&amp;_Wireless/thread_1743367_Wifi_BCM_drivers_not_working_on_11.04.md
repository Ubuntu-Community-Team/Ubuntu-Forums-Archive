---
title: "Wifi BCM drivers not working on 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by ralanyo on 2011-04-29
This is unlike other installs that I have done. Usually I update the repositories in synaptic and the new wifi drivers are there to install. I just installed 11.04 and I am getting "no proprietary drivers on this system" and I wifi says device not ready (firmware missing).

I have tried a bunch of fixes and none of them seem to work. Anyone having this issue or know of a fix.

its a dell 6000 laptop, with a bcm4318 card. Any help would be greatly appreciated. thanks

---

### Post by josephmills on 2011-04-29
```
lspci -vnn | grep 14e4 
```
thanks

---

### Post by ralanyo on 2011-04-29
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by josephmills on 2011-04-29
```
lsmod | grep b43 
```
```
dmesg | grep b43 
```
thanks

---

### Post by collisionystm on 2011-04-29
> **ralanyo said:**
> This is unlike other installs that I have done. Usually I update the repositories in synaptic and the new wifi drivers are there to install. I just installed 11.04 and I am getting "no proprietary drivers on this system" and I wifi says device not ready (firmware missing).

I have tried a bunch of fixes and none of them seem to work. Anyone having this issue or know of a fix.

its a dell 6000 laptop, with a bcm4318 card. Any help would be greatly appreciated. thanks


[http://ubuntuforums.org/showthread.php?p=10736018](http://ubuntuforums.org/showthread.php?p=10736018)

I followed the instructions, ran the Additional Drivers app and after a reboot... happy happy.

---

### Post by ralanyo on 2011-04-29
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  2 b43,b44

<br><br>
[    1.696099] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.626313] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.750206] Registered led device: b43-phy0::tx
[   19.750330] Registered led device: b43-phy0::rx
[   19.750459] Registered led device: b43-phy0::radio
[   19.995144] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   19.995151] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   19.995156] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by spiky001 on 2011-04-29
I just got my same card working by going to synptic manager downloading firmware b43 then rebooted

---

### Post by josephmills on 2011-04-29
> **ralanyo said:**
> b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  2 b43,b44

<br><br>
[    1.696099] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.626313] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.750206] Registered led device: b43-phy0::tx
[   19.750330] Registered led device: b43-phy0::rx
[   19.750459] Registered led device: b43-phy0::radio
[   19.995144] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   19.995151] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   19.995156] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

go to synaptic and install the firmware-b43-installer

---

### Post by josephmills on 2011-04-29
after done on post 8 could we see a ```
dmesg | grep b43 
```
and a ```
rfkill list 
```

---

### Post by ralanyo on 2011-04-29
That worked. Thanks so much! Here is what it says now

[    1.657327] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.713774] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.838878] Registered led device: b43-phy0::tx
[   19.839001] Registered led device: b43-phy0::rx
[   19.839116] Registered led device: b43-phy0::radio
[   20.356633] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

Soft blocked: no
Hard blocked: no

---

### Post by josephmills on 2011-04-29
please mark as solved thanks and happy wireless 




> **ralanyo said:**
> That worked. Thanks so much! Here is what it says now

[    1.657327] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.713774] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.838878] Registered led device: b43-phy0::tx
[   19.839001] Registered led device: b43-phy0::rx
[   19.839116] Registered led device: b43-phy0::radio
[   20.356633] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

Soft blocked: no
Hard blocked: no

---

### Post by redrach on 2011-04-29
> **ralanyo said:**
> 03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

