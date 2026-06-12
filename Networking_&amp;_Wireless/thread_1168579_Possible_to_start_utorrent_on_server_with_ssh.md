---
title: "Possible to start utorrent on server with ssh?"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Karakh on 2009-05-24
Is it possible to start utorrent running on the server through ssh? I can get it running and displaying on the client by logging in with -X, but I need to be able to start it running on the server and log out, leaving it running on the server.

(Networking noooob. Be gentle.)

---

### Post by mellowd on 2009-05-24
try screen


I use rtorrent with screen and can ssh in from home or work to check the status of rtorrent. I can even ssh in in and view rtorrent with my phone

---

### Post by update_manager on 2009-05-24
> **Karakh said:**
> Is it possible to start utorrent running on the server through ssh? I can get it running and displaying on the client by logging in with -X, but I need to be able to start it running on the server and log out, leaving it running on the server.

(Networking noooob. Be gentle.)


Possibly, but I'd recommend using:
- a console torrent client that can be launched and sent into the background over SSH (ctorrent)
- a client that has a web based configuration option (deluge-webui)

---

### Post by Karakh on 2009-05-24
Ive looked at most of the native torrent clients, but the only one I can find with rss support (that can save different filters to different locations) is uTorrent. Unfortunately...

---

