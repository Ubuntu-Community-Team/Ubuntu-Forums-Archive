---
title: "WiFi not working with any security mode"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2013-04-23
Ubuntu 12.10 x64

lspci:
```

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

I can't connect to WiFi with this card.  It acts like it wants to connect then asks for my passcode again.  I've tried WPA/WPA2 and WEP.  This router works fine with my Ubuntu 12.10 desktop.  Any ideas would be appreciated.

---

### Post by kr651129 on 2013-04-23
Ha, the answer was right in front of me. ABG.  It's an older laptop that doesn't support N, I had to switch my router to mixed mode.

---

