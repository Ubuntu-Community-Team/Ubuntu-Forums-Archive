---
title: "Server Drops Connection Momentarily"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by xcrx on 2010-12-30
I have a server running Ubuntu 10.04. I use it for mysql as well as samba file sharing across 10 computers. It had been working out great. I only ever needed to restart after I would install updates and to sort of thing. Starting this week however, it has started kicking all the computers off of both mysql and the samba shares every few minutes. It is very strange. The mysql connection can be restored just by closing the database and reopening it. The file shares are only a problem if you try to access them though a program other than your file browser (e.g. save a file you are working on in word to the server). The server never shuts down and all services can be reconnected immediately. It is very strange. 

I do believe that the server installed some automatic updates at the beginning of this week when this all started happening. I am not sure if one of the updates is causing the server to do this or not.

Any help is very much appreciated.

---

### Post by xcrx on 2010-12-30
I downloaded Etherape to try and get a better idea of how the connection is working. It appears to drop my mysql connection if it is idle for 60 seconds. I really have no idea why. Has anybody else ever had this problem?

---

