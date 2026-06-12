---
title: "Cinnamon network manager applet not retaining mobile broadband settings"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by felgro on 2013-08-07
[COLOR=#808080]*[originally posted in desktop forum as it appears specific to cinnamon - [http://ubuntuforums.org/showthread.php?t=2165931]](http://ubuntuforums.org/showthread.php?t=2165931])*[/COLOR]

I am having problems with the nm-applet component of the Cinnamon desktop on Ubuntu 12.04 (precise). 

My setup is such that I frequently switch between smartphone, a regular  use 3g mobile dongle and a prepaid 3g dongle. The last two are the issue  - they have different APNs, one requires a login and one doesn't. They  need to be distinct from each other as listed connections.

The network settings component nm-applet is not remembering the  different configs the way it used to in Gnome 2. Further, if I add the  first connection then add the second, the first gets deleted. I also  have the problem of not being able to subsequently access the settings  area without one of the dongles connected and configured. This is pretty  annoying. I have also found duplicate files created here -

```
me@home:/etc/NetworkManager/system-connections$ ls -l /etc/NetworkManager/system-connections/
total 16
-rw------- 1 root root 332 Aug  7 13:37 Telstra Telstra Internet*Wap
-rw------- 1 root root 266 Aug  7 12:43 Telstra Telstra Internet*Wap 1
-rw------- 1 root root 377 Aug  7 11:18 Telstra Telstra (Next G)
-rw------- 1 root root 369 Aug  7 12:40 Telstra Telstra (Next G) 1
```

The applet is the one that is part of cinnamon applets set up area - and  it is plugging into the gnome nm-applet as far as I can tell. But I may  be wrong, I'm also lost as to where to find info on what is actually  running. It's pretty annoying. Unity does not have this problem, but  Unity makes me want to throw my notebook across the room. Can anyone  point me in the right direction to fix this?

---

