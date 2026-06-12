---
title: "Ethernet help"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2010-10-26
Hello

My homeserver has onboard ethernet, however it's incredibly slow, so I added an ethernet card I had around the house and everything worked fine. Then I took it out to test it on another computer, when putting it back in, ubuntu doesn't connect, the whole network menu is greyed out, but the link light is on.

When I plug it back into the onboard, it fires up fine

Any ideas? :(

Thanks

Tom

---

### Post by Colo2 on 2010-10-26
No ideas?

---

### Post by alexandari on 2010-10-26
```
 sudo ifup eth0 
```

---

### Post by Colo2 on 2010-10-26
> **alexandari said:**
> ```
 sudo ifup eth0 
```

> Ignoring unknown interface eth0=eth0


:|

---

### Post by Colo2 on 2010-10-26
Bump

---

### Post by Colo2 on 2010-10-26
Nvm, I fixed it ;) was a hardware issue. Just put the device in another PCI slot

---

