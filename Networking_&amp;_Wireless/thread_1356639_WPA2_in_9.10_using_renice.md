---
title: "WPA2 in 9.10 using renice"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by a-web on 2009-12-16
I was having problems connecting to a WPA2 network, but eventually fixed it using```
sudo renice +19 $(pidof wpa_supplicant)

```every time I boot.  Here is the thread where that happened: [http://ubuntuforums.org/showthread.php?t=1303516](http://ubuntuforums.org/showthread.php?t=1303516).

Now, is there a way to do that automatically so that I don't have to open up a terminal window and remember that command every time I reboot?
Cheers.

---

### Post by ajgreeny on 2009-12-16
Add the command, without the sudo, to /etc/rc.local somewhere between the **#!/bin/sh -e** and **exit 0** and it will be run at each boot.

---

### Post by a-web on 2009-12-17
Perfect!  Many thanks.

---

