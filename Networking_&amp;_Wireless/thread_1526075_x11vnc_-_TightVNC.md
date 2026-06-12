---
title: "x11vnc - TightVNC"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by denvro on 2010-07-07
Hello,

I'm using Ubuntu 9.04 and have x11vnc installed. When I try to connect to this Ubuntu desktop from my Windows 7 laptop I get the error "Failed to connect to server". I'm using TightVNC to connect.

I have started x11vnc on the desktop with the following command:
x11vnc -ncache 10 -safer -localhost -nopw -once -auth /var/lib/gdm/:0.Xauth -display :0

In TightVNC I tried to connect to:
192.168.1.x:0
192.168.1.x:5900
192.168.1.x::5900

But none of the above worked. Can anyone help me with this problem?

Kind Regards,
D.

---

### Post by Yarui on 2010-07-07
Have you tried starting the server with fewer options just to test it out?
```
vncserver -kill :0
vncserver :0
```
Have you also tried using :1 instead of :0?  I have seen a lot of guides suggest using :1.  I'm not sure exactly why, but that has worked for me in the past when :0 was having issues.  This would make the port you are operating on 5901 instead of 5900.  I have had some issues with tightVNC in the past and it always ends up getting resolved after screwing with it long enough.

---

### Post by denvro on 2010-07-07
Thanks for your reply. It was the "-locahost" option causing the problem. I have removed this option from the startup script and everything is working fine now!

---

### Post by krunge on 2010-07-07
> **denvro said:**
> Thanks for your reply. It was the "-locahost" option causing the problem. I have removed this option from the startup script and everything is working fine now!
Yes, the "-localhost" option is usually for when you want to connect through an SSH tunnel (i.e. the tunnelled connection appears to come from localhost.)

---

