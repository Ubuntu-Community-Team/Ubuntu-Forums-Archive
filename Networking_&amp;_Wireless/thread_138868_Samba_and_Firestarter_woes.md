---
title: "Samba and Firestarter woes"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by cbudden on 2006-03-02
Hey there.

In order to access my Ubuntu shares on Windows, I need to disable firestarter, even though I have told it to allow all connections from the XP PC's IP address.  Ubuntu comes up under workgroup computers on XP but it is unable to connect with firestarter enabled..  Whats going on?
Thanks

---

### Post by kseise on 2006-03-09
I'll bump this.  Anyone have an answer?

---

### Post by chusome on 2006-03-11
Under firestarter go to policy
-Single click so that something is highlighted in the second window.
-then click add rule
-for name, click the down arrow and choose samba(smb)
-under when the source, type in your subnet name ie. 192.168.0.0/24

This will allow you to map drives via ip address. (For some reason it won't work via netbios name) I'll post back if I find an answer to that problem. (its something to do with firestarter)

---

### Post by kseise on 2006-04-05
Thank you.  That seemed to be the answer.

---

