---
title: "How to send messages from ubuntu to windows xp machine"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by dado2000 on 2011-01-11
Hi!

Is there a way to send messages from Ubuntu to windows xp computer, like **NET SEND**, in Windows network enviroment?

Thanks in advance.

---

### Post by PatchesTheCaveman on 2011-01-11
Run this command on a terminal:
```
smbclient -M *<target machine>*
```

Type your message and then press CTRL+D to send.

---

