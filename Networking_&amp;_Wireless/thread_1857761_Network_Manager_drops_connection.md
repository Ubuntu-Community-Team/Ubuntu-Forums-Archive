---
title: "Network Manager drops connection"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by daniel.p on 2011-10-10
I finally got wireless up and running after days of trial and error, but have encountered a new problem. Network manager drops the connection fairly regularly and will not reconnect. I've read around and found it's a common issue, but haven't found a solution other than a reboot (which is really annoying).

I had a fresh install of Blackbuntu which is based off Ubuntu 10.10, installed firmware-b43-lpphy-installer, and then the 3.0.4 kernel from Ubuntu. That got my wireless working finally. 

When the connection drops it attempts to reconnect then I get a window asking for my WPA key. It tries to connect again, and once again I get the window asking for the WPA key. After a reboot wireless connects no problem. Are there any solutions to this problem? Or am I stuck just rebooting each time it happens?

The one thing I noticed is the connection is relatively stable if I'm just using firefox, IRC, etc. but if I attempt to download something (i.e. and update) the connection drops within minutes.

---

### Post by garvinrick4 on 2011-10-11
Do not know how to fix the driver problem in your install but
this will restart network-manager as to not have to reboot.
```
sudo /etc/init.d/network-manager restart
```

---

