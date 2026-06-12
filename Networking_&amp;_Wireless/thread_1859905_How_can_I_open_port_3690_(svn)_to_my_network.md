---
title: "How can I open port 3690 (svn) to my network?"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by sawatdee on 2011-10-14
I set up subversion about a year ago and have been using it with no problem, checking in files almost every day and updating them on another system on my network. For no apparent reason, it suddenly started giving me "connection refused" messages when I try to commit or update. I checked nmap and netstat and discovered that port 3690 is open on localhost only, but not the network. How can I force it to open that port to my whole network and not just its own localhost? And what could have caused it to suddenly close port 3690 to my network in the first place? I have not changed anything on my system or my configuration.

To start the server, I ran "svnserve -d". And running "ps -A" shows that svnserve is indeed running, but the port is not open.

---

