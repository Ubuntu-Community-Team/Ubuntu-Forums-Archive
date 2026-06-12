---
title: "Network Manager Icon not seen on Panel"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by madaswamy on 2010-06-22
Hi All,
Network Connection manager Icon does not appear on the Panel.
I use Ubuntu 10.4
Can anyone help me in getting the same.

Thanks,
MM

---

### Post by dineshs on 2010-06-22
pl refer this
[http://ubuntuforums.org/showthread.php?t=1311790&page=3](http://ubuntuforums.org/showthread.php?t=1311790&page=3)

---

### Post by madaswamy on 2010-06-22
Hi Dinesh,
Thanks, but it did not work for me..

---

### Post by wilee-nilee on 2010-06-22
Are you missing the notification applet, right click on the panel and add it if you are. If the notification applet is there run this in the terminal. I see now that the link suggests the notification applet, try the terminal command.
```
killall gnome-panel
```  this will restart panel, also look in startup applications in system-preferences to see if it is ticked off, although if it was you wouldn't be on the web I think.
[ATTACH]161188[/ATTACH]

---

