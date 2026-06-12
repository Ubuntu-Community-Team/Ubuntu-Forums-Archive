---
title: "Using the DVD rom of another computer"
date: 2006-04-21
forum: Networking &amp; Wireless
---

### Post by geniusvicks on 2006-04-21
I have an Ubuntu Desktop and a Windoze XP laptop. My laptop has a DVD drive, which I want to access with my Ubuntu Desktop PC. What do I do?

---

### Post by jethro10 on 2006-04-21
Do you not just share it like any other windows folder or drive?

If your question is more basic than that you'll need samba client installed on the ubuntu box first,
set it in the same workgroup as the WinPc.

Jeff

---

### Post by geniusvicks on 2006-04-21
[QUOTE=jethro10]Do you not just share it like any other windows folder or drive?

If your question is more basic than that you'll need samba client installed on the ubuntu box first,
set it in the same workgroup as the WinPc.

Jeff[/QUOTE]

I've downloaded samba but I donno how to configure it can anyone help me?

---

### Post by Jason_25 on 2006-04-21
You don't need samba to connect to windows shares.  smbclient and nautilus can do that for you.  Either read up on the manual page for smbclient or click places > network servers.

---

