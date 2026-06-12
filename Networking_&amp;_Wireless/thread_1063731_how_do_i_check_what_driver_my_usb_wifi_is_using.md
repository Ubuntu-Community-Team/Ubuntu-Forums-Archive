---
title: "how do i check what driver my usb wifi is using?"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by mparker81 on 2009-02-08
i am trying to set up kismet in ubuntu, but i need to know what driver my linksys usb is using. is there a command i can type in terminal that will tell me?

---

### Post by issih on 2009-02-08
```
sudo lshw -C network
```

that will list all networking hardware, and lots of info about the different interface, including the driver being used.

Hope that helps

---

