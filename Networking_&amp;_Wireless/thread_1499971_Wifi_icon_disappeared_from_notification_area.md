---
title: "Wifi icon disappeared from notification area"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by pwaugh on 2010-06-02
While my wifi still is working just fine (I'm here aren't I), the Network Manager has disappeared from the Notification Area on my panel upon reboot.

Have all current patches, so have no clue what to do.  Most likely is a bug.

patrick

---

### Post by ajgreeny on 2010-06-02
Make sure that the network manager is listed in your startup programs.

If not add it in.  The command, if it has disappeared is ```
nm-applet --sm-disable
```

---

