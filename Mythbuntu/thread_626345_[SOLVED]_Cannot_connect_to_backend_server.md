---
title: "[SOLVED] Cannot connect to backend server"
date: 2007-11-29
forum: Mythbuntu
---

### Post by moody1021 on 2007-11-29
Looked at a bunch of posts for resolving the issue. The backend and front are both running on the same machine. It was not an IP issue, it was not mysql.txt or configuration issue. Finally what got the front and back connected was going to the mythbuntu control center and enabling mysql remote connection capability. I found it disabled by default.  I am not sure why this step did the trick since the connection is via 127.0.0.1, i.e., loopback. Maybe that is considered remote?

Hope this helps someone else. I spent a couple of days scratching my head as to why it wouldn't work when the ip and configuration that other posts mentioned were all correct in my setup.

---

### Post by uopjohnson on 2007-11-29
It sounds like you may have specified an ip address in mytthv setup and not 127.0.0.1.  Or you may have specified a host name that your router resolved to an external ip and not to the loopback.  You shouldn't need to enable the service for local connections, however if your myth tries to connect to 192.168.1.10 (or whatever your external ip is) it will fail.

---

