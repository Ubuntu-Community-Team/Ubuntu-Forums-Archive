---
title: "My TP-LINK TL-322G doesn't work"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by Scrubru on 2010-02-26
I try to do wireless man-in-the middle attack with my ASUS laptop and I've alreay got two wlan adaptors, a built-in Atheros NE-785H and a TP-LINK TL-W322G USB wireless adaptor. Either of them is to act as a rogue access point (soft AP). The biult-in adaptor works well but I just can't get the TP-LINK working properly.

I have alreay visited the threads below
[COLOR="Blue"][No Wireless with TP-LINK TL-WN322G found]("http://ubuntuforums.org/showthread.php?t=847192")
[Problems with a TP-LINK TL-WN322G 54g Wireless USB Adapter (ZyDAS zd1211b Chipset )]("http://start.ubuntuforums.org/showthread.php?p=5439953")
[HardwareSupportComponentsWirelessNetworkCardsTP-Link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link")
[tp-link WN322G]("http://old.nabble.com/tp-link-WN322G-td21524214.html")
[Wlan mit TP-LINK TL-WN322G]("http://forum.ubuntuusers.de/topic/wlan-mit-tp-link-tl-wn322g/?highlight=scan#post-1488863")[/COLOR]

I'm running Karmic with 2.6.31-19, according to the Ubuntu help page it should work out of the box, but it just wouldn't work for me. I only got it working with ndiswrapper, which is clearly not what I want to use since it's not supported by aircrack-ng. Any ideas?

Here are results after running _modprobe -v zd1211rw_

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.31-19-generic/updates/cw/zd1211rw.ko 
```

then lsmod | grep zd

```
zd1211rw               52232  0 
mac80211              243496  2 zd1211rw,ath9k
cfg80211              152616  4 zd1211rw,ath9k,mac80211,ath
```

lsusb

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0cf3:1006 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b036 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg | grep zd1211

```
[ 1046.773321] usbcore: registered new interface driver zd1211rw
```

ifconfig shows that there are only three interfaces: lo, eht0, wlan0. The USB wireless adaptor was identified as wlan1 using ndiswrapper.

---

### Post by chili555 on 2010-02-26
> Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID [COLOR="Blue"]0cf3:1006 Atheros Communications, Inc. [/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID [COLOR="Blue"]04f2:b036 Chicony Electronics Co., Ltd [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubWhere is the TP-Link? I see the Atheros and your webcam, but nothing that seems like a second wireless device.

---

### Post by Scrubru on 2010-02-26
I plugged it in, but nothing happened. There should be a red light flashing if it is working.

---

### Post by chili555 on 2010-02-26
Is it defective? Does it work on other computers, or at least show up in *lsusb*?

---

### Post by Scrubru on 2010-02-26
No, it doesn't work for my desktop computer either. It works pretty well under Windows XP though ( with the driver installed ).

---

### Post by Scrubru on 2010-02-26
> **chili555 said:**
> Where is the TP-Link? I see the Atheros and your webcam, but nothing that seems like a second wireless device.

The atheros that shows up in lsusb is the very TP-LINK I've plugged in. I've done lsusb once again with the TP-LINK detached, it's like this

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b036 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Note that there is no Atheros.

---

### Post by flash63 on 2010-03-02
Hello,
try this driver package. Follow the instructions in the first codebox.
[http://forum.ubuntuusers.de/topic/tl-wn721n-bzw-tl-wn722n-von-tp-link-mit-ar927/#post-2383604]("http://forum.ubuntuusers.de/topic/tl-wn721n-bzw-tl-wn722n-von-tp-link-mit-ar927/#post-2383604")

Block the modules **zd1211rw** and **ath9k**
```

echo 'blacklist zd1211rw' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist ath9k' | sudo tee -a /etc/modprobe.d/blacklist.conf

```

---

