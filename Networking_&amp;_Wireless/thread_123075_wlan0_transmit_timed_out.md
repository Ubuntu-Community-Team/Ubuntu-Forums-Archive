---
title: "wlan0 transmit timed out"
date: 2006-01-29
forum: Networking &amp; Wireless
---

### Post by malte on 2006-01-29
I'm sorry I have already posted this, in response to a post picturing a similar problem, but I can't find a solution.

I'm using the at76c503 module for an Atmel wireless USB card
```

malte@malteo ~ $ lsmod |grep at76
at76c503_rfmd          42500  0
at76c503               97248  1 at76c503_rfmd
at76_usbdfu             6084  1 at76c503
usbcore               118396  7 quickcam,at76c503_rfmd,at76c503,at76_usbdfu,ehci_hcd,uhci_hcd

```
**Without any apparent reason**, my connections stops working and I get this in /var/log/messages
```

[4311820.929000] NETDEV WATCHDOG: wlan0: transmit timed out
[4311820.929000] /home/malte/Download/at76c503a/at76c503.c: wlan0: tx timeout.

```
I need to ifup/ifdown wlan0 to get it running again.

The problem appears with the updated CVS module too, it didn't happen with hoary or my old Gentoo, and, I repeat, without any apparent reason or due to a specific program or high or low network traffic.

I'd like to know if someone has (or, better, had!) the same problem, it really drives me nuts :evil:

---

### Post by malte on 2006-02-08
It seems the connection drops whenever there's a high traffic on the interface, like aMule downloading, AMSN webcams and a wget...

Please, help :(

---

### Post by malte on 2006-02-10
... and adding "noapic nolapic" to the kernel options didn't help too!

I'm desperate now!

---

### Post by malte on 2006-02-11
:confused: The problem just appeared again and this time my keyboard didn't work too!!! I had to reboot!

I'm trying to give you some hints, because I really don't know how could cause this "strange" thing! Is it possible that I'm the only one with this problem???

---

