---
title: "Wireless randomly changing names ath0 to wlan0"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by mechgt on 2012-05-29
Running 12.04 Precise
When I boot my machine, sometimes my wireless adapter comes up as wlan0, and sometimes it's ath0.  It's done this before (changed) but really only when I did a distro upgrade, not frequently as it's doing now.  Now it's almost like it alternates every time I reboot (or at least very frequently when I reboot).

It works in either case and is transparent to me with the exception that I've got an application that binds to the adapter by name (MediaTomb) and won't run until I change the config file to match the current adapter name.  Any clue why it does this?

FYI, I had to go into a network config file and toggle 'managed' somewhere when I first upgraded to 12.04 (changed it from the default) in order to make the wireless work.

---

### Post by chili555 on 2012-05-29
Please open a terminal and run and post:```
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig
```Thanks.

---

