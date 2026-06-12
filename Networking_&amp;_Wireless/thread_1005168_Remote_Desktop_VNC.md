---
title: "Remote Desktop VNC"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by moisessalum on 2008-12-08
Hi, I'm trying to connect to a friend's computer via VNC, but when I try to connect to his computer it gives me this message.
> unable to connect to host: Connection refused (111)

What can I do??

I know my friend's ip and he doesn't ask for password to connect via remote desktop, I don't know why my connection is refused.

We both use Ubuntu 7.10.

---

### Post by techboywi on 2008-12-08
Does your friend have the proper port forwarding rules setup on their router?

---

### Post by MockY on 2008-12-08
You can also use Hamachi to set up a vpn tunnel. That way you most likely don't have to care about any firewall rules and port forwarding. But it requires both of you to have it installed.

Download it from [https://secure.logmein.com/products/hamachi/list.asp](https://secure.logmein.com/products/hamachi/list.asp)

And then install the GUI for it from here
[http://hamachi-gui.sourceforge.net/download.html](http://hamachi-gui.sourceforge.net/download.html)

---

### Post by superprash2003 on 2008-12-08
for vnc you need to ensure port 5900 is open

---

