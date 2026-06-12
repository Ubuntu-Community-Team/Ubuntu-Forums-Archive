---
title: "Can't connect to internet ubuntu 10.10"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by 1q2w3r on 2011-01-09
Hello. I've recenetly installed ubuntu 10.10 (64-bit) on my hp touchsmart iq525, but it refuses to connect to the internet. However I had no problems on 10.04. I was wondering if anyone had a link to the newest driver for my wireless lan card:

PCI wireless card (Realtek RT2700E 802.11n Wireless LAN)

or any ideas about what's wrong.

---

### Post by amsterdamharu on 2011-01-09
Can you connect by cable? That would make it a lot easier, Ubuntu might detect your card and install drivers for it.

The detection should start automatically but you can press alt + F2 and type jockey-gtk

I was unable to find your card using google (search for site:packages.ubuntu.com realtek 27). Did the card work out of the box in 10.04 or did you have to install something?

What is the output of  the following command?
```
sudo lspci | grep eal
```
Or if your wireless is usb:
```
sudo lsusb | grep eal
```

Another thing to consider is that you might have a key combination that can switch your card on or off so make sure it's on.

---

