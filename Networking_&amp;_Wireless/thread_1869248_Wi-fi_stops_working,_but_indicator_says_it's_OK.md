---
title: "Wi-fi stops working, but indicator says it's OK"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by vatzec on 2011-10-25
Hey. :)

I'm using Ubuntu 11.10. My wireless network connection is usually OK, but sometimes it stops working - I can't even ping my wifi router, though the indicator applet (nm-applet) shows a working connection. I can solve this for approximately a minute by reconnecting to the network (by either turning wifi off and back on or reselecting the same network from the list), but the same thing happens again. It is possible that this only happens when another computer is using the network, also wirelessly. It's hard for me to say if this is a problem with 11.10 - I have used a different laptop with 10.10 before and it worked fine. Do you know what might be the issue?

---

### Post by praseodym on 2011-10-25
Hi,

what hardware is in use? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by vatzec on 2011-10-25
An Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) wireless network card used with ath9k. The card supports 802.11n.

The router had bandwidth set to 20MHz, and 802.11 modes to "g" and "n". I've changed the supported modes to only "g" and so far everything's fine.

---

### Post by praseodym on 2011-10-25
Deactivate the hardware encryption (software encryption not affected):

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by vatzec on 2011-10-25
Thanks for the idea, I'll try it the next time it breaks down. Are you sure this will help? If so, then why?

---

### Post by praseodym on 2011-10-25
ath9k is a little bit buggy

---

### Post by vatzec on 2011-11-12
The 802.11g workaround helps, but it obviously isn't a proper solution. I'll try disabling hardware encryption if I ever need 802.11n. Thank you for you help!

---

