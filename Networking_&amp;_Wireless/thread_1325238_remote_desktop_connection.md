---
title: "remote desktop connection"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by windowsfree on 2009-11-13
I have enabled Remote Connection on ubuntu 9.04 laptop.  I used the address it gave me to connect to it and when attempting to connect with a Windows XP session it will not connect.  I even allowed it to figure network connections automatically and it will not connect.  Any suggestions?

Thanks

---

### Post by hedoe on 2009-11-13
ill be watching this one

---

### Post by W. Irving on 2009-11-14
I'm not sure the native XP remote desktop client will work as a true VNC client. I tried it on my systems, with all sorts of strange results on the Windows computer..
You have opened port 5900 on the Ubuntu machine, yes? ;)
These are (two of) your options, that both work really well:

[LIST]
[*][http://www.realvnc.com/](http://www.realvnc.com/)
[*][http://www.uvnc.com/](http://www.uvnc.com/)
[/LIST]

---

### Post by Tsquad on 2009-11-14
I actually just did this last night with my new 9.10 computer and my vista pc. I set static ips on both of them, and then set the remote desktop settings like you did on ubuntu, except i have the "ask for password" box checked and the one above it about giving permission each time someone trys to connect unchecked. Then using ultra vnc it worked the first time.

---

### Post by dhughes on 2009-11-16
> **W. Irving said:**
> I'm not sure the native XP remote desktop client will work as a true VNC client. I tried it on my systems, with all sorts of strange results on the Windows computer..
You have opened port 5900 on the Ubuntu machine, yes? ;)
These are (two of) your options, that both work really well:


 I think everyone has wanted to do this at one time or another myself included, from what I have read VNC supports RDP protocols but RDP won't support VNC protocols. Even different ports are used, VNC uses 5900 but RDP uses 3389.

---

