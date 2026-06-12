---
title: "Network manager removed from task bar"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by meeya on 2010-03-05
I accidentally removed the network manager from the task bar. now it does not load at start up and now I do not know how to enable my  Huawei E220 modem.

---

### Post by meeya on 2010-03-05
sorry I'm on 9.10 64 bit

---

### Post by wojox on 2010-03-05
Does right clicking and Add to panel > Notification Area do anything?

---

### Post by meeya on 2010-03-06
No I can't find anything.

---

### Post by iponeverything on 2010-03-06
open a terminal and do:

```

nm-applet&
disown %1

```

---

