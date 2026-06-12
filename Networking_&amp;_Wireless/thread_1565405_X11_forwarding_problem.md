---
title: "X11 forwarding problem"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by cowteats on 2010-08-31
I have problem forwarding X11 on a remote server running ubuntu 10.04 that I rented from Keyweb.
My PC is a windows 7 with XWin Server from Cygwin as well as SSH Secure Client with X11 forwarding enabled in Tunnelling. On the server, I installed xauth, x11-apps and firefox. I tried running both xclock and firefox from the server, there was no error message at all as if the programs are running fine: but the display does not get forwarded to my PC.

Before this, I already experimented with X11 forwarding on my second PC (also running ubuntu 10.04) on my home network. I was able to run xclock and firefox off my second PC by connecting with SSH Secure Client. 

Am I missing some packages or configuration that prevents me from running X11 off the remote server?
Thanks in advance.

---

