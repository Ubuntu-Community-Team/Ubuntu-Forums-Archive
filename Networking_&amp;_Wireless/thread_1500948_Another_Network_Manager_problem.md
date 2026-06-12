---
title: "Another Network Manager problem"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by pac-man on 2010-05-22
same exact problem for me, after I suspended to ram the computer couldn't wake up so I had to force shut it down by pressing the power button and holding it.

When I turned it back on the network icon said "unmanaged" and when I tried to access knetworkmanager nothing comes up.

I tried suspending again as mentioned here and the problem remains.

:(

---

### Post by lexxonnet on 2010-06-03
Thanks for the solution, the suspend-resume thing worked for me. pac-man, try editing this file: /etc/NetworkManager/nm-system-settings.conf and change from unmanaged to managed. That might help. Found that solution on another thread.

Either way, this is a pretty annoying bug. It seems that shutting down the computer when it is suspended leads to this.

---

### Post by Iowan on 2010-06-03
Split from [this ]("http://ubuntuforums.org/showthread.php?t=1476910") SOLVED thread.

---

