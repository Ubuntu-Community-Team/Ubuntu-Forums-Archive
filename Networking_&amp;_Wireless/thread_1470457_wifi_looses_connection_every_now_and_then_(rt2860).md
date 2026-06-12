---
title: "wifi looses connection every now and then (rt2860)"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by NixForFree on 2010-05-02
My wireless card rt 2860 works fine with ubuntu 8.10 / 9.10, but every now and then i have to reconnect manually. :(

The tray icon allways shows a status of 'connected', but after a few minutes the connection gets lost, especially when new wireless accesspoints in the neighbourhood are detected or swiched off. anyone an idea?

---
ASUS EEE PC 1000H
RaLink rt2860

---

### Post by szim90 on 2010-05-07
There are some problems with the rt2860 driver in lucid.

It might be this bug:
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/496093)

---

### Post by vallvi on 2010-05-09
I had a similar problem, and found a solution here:
[http://ubuntuforums.org/showthread.php?t=1467877](http://ubuntuforums.org/showthread.php?t=1467877)

---

### Post by NixForFree on 2010-09-01
Thanks for your replies. Recently I upgraded to Lucid, and the problem is still the same (as I exspected from what I read in the forum).

@szim90: I tried to install the linux-backport.... modules as described in your link. After that my wifi wouldn't connect anymore at all. Then I had to blacklist all of the ralink-backportmodules to get the wifi working again as before.

@vallvi: The solution in your linked post unfortunately doesn't apply to my RaLink 2860 (pci) device. Firstly, I've not got an usb-device, but a pci, and it's not RaLink 28**70**, but RaLink 28**60**.

So, perhaps someone has got a solution in the meantime? Or probabely we'll have to wait for the 2.6.33 kernel?

---

### Post by NixForFree on 2011-05-08
Thanks for your replies. I tried your suggestions and decided to wait for newer kernel versions, which might have been the right decision.

---

