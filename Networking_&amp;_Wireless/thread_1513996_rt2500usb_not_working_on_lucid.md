---
title: "rt2500usb not working on lucid"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by kissson on 2010-06-20
it is absolutely working on slitaz (I swear)
in slitaz , I install the rt2500usb firmware by it's package manager
and then

modprobe rt2500usb
ifconfig wlna1 up
iwconfig wlan1 essid abcd1234 key s:12345
udhcpc -i wlan1

then everything go

and lucid only shows 'not associated' in iwconfig after I wake the interface up (actually it is up , modprobe ed when boot time, I do it once more ) and issue the essid command

any idea ?
please help

---

