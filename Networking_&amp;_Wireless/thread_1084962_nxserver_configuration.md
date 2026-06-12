---
title: "nxserver configuration"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by rcmn on 2009-03-02
I though /etc/nxserver/node.conf this file along with other file located in /usr/share/ were responsible to configure the server.

Since the files in /usr/share from the ubuntu team state(do no edit this file) I turn my attention to "/etc/nxserver/node.conf".
But with no success.

I have been trying to get an option to "disconnect" but keep my session running. So i thought i found the option in "node.conf" but nothing seems to happen. Then i thought maybe I needed to configure the server so it give the client the option to have a menu to disconnect .I founf something like that but ,again , nothing change. 

the option i tried to enable in node.conf:
ENABLE_PERSISTENT_SESSION="all"
ENABLE_PULLDOWN_MENU="1"

---

