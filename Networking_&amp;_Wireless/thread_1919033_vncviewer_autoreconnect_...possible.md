---
title: "vncviewer autoreconnect ...possible?"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by TiberiusT on 2012-02-02
I have a laptop running 11.10 with xfce. It runs a permanent vnc connection to a server on 11.10. 32bit both sides. It's vnc4server on the server and I use vncviewer from the package xvnc4viewer on the client. The sessions are shared and persistent.

The laptop is setup with rigorous battery saving modes which all drop the wireless connection when they kick-in. Repowering the wireless/laptop results in vncviewer saying 'connection reset...' and the program closes. I want it to stay open and try to reconnect itself.

I see here [http://www.realvnc.com/products/free/4.1/release-notes.html](http://www.realvnc.com/products/free/4.1/release-notes.html) that the Windows .exe version of realvnc viewer has a cli switch -autoreconnect which is just what I want, but on 11.10, vncviewer -h reveals no such option. nor does xtightvncviewer. 

Tks in advance

T

---

