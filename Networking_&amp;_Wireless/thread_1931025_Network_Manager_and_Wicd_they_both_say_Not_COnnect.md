---
title: "Network Manager and Wicd they both say Not COnnected while connected!!!"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by october1917 on 2012-02-24
During a text mode Debian Testing installation I was promted to use an internet connection. As there was no cable conected to the ethernet, I manually entered the ESSID and the key. The installation indeed established internet connection using the Wireless interface.

As soon I was loged in the new installation I saw that although I was connected to the internet (I was browsing) the network manager applet was showing x (device not managed!!!). Then I installed the WiCD, which shows no wireless networks!!!

Alright, there is no problem as soon as I'm connected. But ...why?

Any ideas?

---

### Post by kurt18947 on 2012-02-24
I'm not sure you can use both at the same time.  There are networking gurus around here; I'm not one but I'm pretty sure they conflict.    I believe you have to uninstall or disable one of the two.  Just try to not find yourself with NO network management utility installed.  There are ways around that but it's not so simple.

---

### Post by huyie on 2012-02-24
Check /etc/network/interfaces
Your wireless connection is most likely set up in there.
If you rather Network Manager or Wicd to take over your wireless, you need to comment the wireless section out.

---

### Post by october1917 on 2012-02-24
> **huyie said:**
> Check /etc/network/interfaces
Your wireless connection is most likely set up in there.
If you rather Network Manager or Wicd to take over your wireless, you need to comment the wireless section out.

That was it. Thanks a lot!

---

