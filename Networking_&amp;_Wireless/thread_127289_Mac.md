---
title: "Mac"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by slimvad on 2006-02-08
Due to a weird but quite legitimate reason I won't explain now I need some advice.
How do I (and can I?) change MAC address on one of my network adapters?
I know for sure this feature is supported by the hardware.
The adapter model is Realtek RTL-8139/8139C/8139C+.
The OS is Breezy 5.10.

---

### Post by mips on 2006-02-08
sudo ifconfig eth0 down hw ether 00:00:00:00:00:01
sudo ifconfig eth0 up

You could also use [http://www.alobbs.com/modules.php?op=modload&name=macc&file=index](http://www.alobbs.com/modules.php?op=modload&name=macc&file=index)

---

