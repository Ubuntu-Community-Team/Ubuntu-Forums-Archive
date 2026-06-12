---
title: "Ubuntu remote desktop"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by dale456654 on 2009-10-16
I have an Ubuntu desktop that I like to connect to from my laptop. But can I do this while someone is using the computer? VNC is not an option for this as no-one else can use the computer. I had this working on a vista computer with a termsrv.dll hack but is it possible to connect to the Ubuntu computer on a different user account while someone is using the computer? I have read many guides but they are just too hard for me to follow. Help is really appreciated!

Thanks!

---

### Post by jonobr on 2009-10-16
Hello


When you remote desktop to the other machine, as far as I know, if you use the same login credentials as the user using the machine, they will be logged out.
I think, if you use a different account it will not.

---

### Post by falconindy on 2009-10-16
Use SSH with X11 forwarding. You'll be able to use the computer concurrently with someone else (even if they're logged in on the same name) and you can use any of the graphical apps that reside on the desktop.

You'll need the 'openssh-server' package on the desktop. Connect to it using the -X flag in the connection string, i.e.:
```
ssh -X user@192.168.1.10
```

---

