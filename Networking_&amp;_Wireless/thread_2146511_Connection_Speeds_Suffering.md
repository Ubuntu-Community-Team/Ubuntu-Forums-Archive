---
title: "Connection Speeds Suffering"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by mjkaufer on 2013-05-18
Hi,
I'm a new Linux user. I switched from Windows 8 to Ubuntu 13.04 today (dualboot). I love Ubuntu. However, there's been one flaw. I feel that the connection speeds have been suffering. It goes on and off sometimes, where it'll be at normal speed and then it'll go to taking around twenty seconds for Google to load. I've had no problems with this before using Windows 8 (all on the same computer and on the same network). Has anyone else experienced this, or does anyone have any ideas as to what to do?

Thanks,
Matthew Kaufer

---

### Post by praseodym on 2013-05-18
Hi there,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a

```
Is it about LAN or wireless?

---

### Post by mjkaufer on 2013-05-18
I'm wireless. It looks like the WiFi connection drops. If I turn off WiFi (on my laptop) and re-enable it, I'm then able to connect, which leads me to think that the problem is with the kernel. I've looked around and it seems that others have had this problem as well.
I'm trying what this link describes at the moment.
[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

---

### Post by mjkaufer on 2013-05-18
Here are the results from the test. My computer had been losing the wifi and such a bit before I ran those commands. Again, this had never happened when I had Windows 8 running.
[http://pastebin.com/wqAJx5zD](http://pastebin.com/wqAJx5zD)

---

