---
title: "Can't get wireless working"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by pacjack360 on 2010-02-14
I need to get the wireless working on this HP dv9005us, I ran lspci and it says the card is "Broadcom Corporation BCM4311 802.11b/g WLAN (rev 1)" and so far I've tried the method that says "Installing drivers for the BCM4311,4312,4321,4322 Cards" on [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and in hardware drivers it says the Broadcom STA wireless driver is activated and in use. Neither iwconfig or ifconfig make any mention to wireless.

---

### Post by night_fox on 2010-02-14
Is your wireless light on? (if you have one)

Did you reboot?

try:
```
ifconfig wlan0 up
```

or do lsmod to determine if there are conflicting wireless drivers.

---

### Post by pacjack360 on 2010-02-14
> **night_fox said:**
> Is your wireless light on? (if you have one)

Did you reboot?

try:
```
ifconfig wlan0 up
```

or do lsmod to determine if there are conflicting wireless drivers.The ifconfig wlan0 up command gave me "wlan0: ERROR while getting interface flags: No such device" and I didn't even see anything with the slightest mention to anything wireless in lsmod

---

### Post by lidex on 2010-02-14
Have a look here, section B:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless")

---

