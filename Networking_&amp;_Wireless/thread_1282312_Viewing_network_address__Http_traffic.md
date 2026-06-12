---
title: "Viewing network address / Http traffic"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by marcon00 on 2009-10-04
Hello,

I can't seem to find anything that would show me my internet traffic with exact connections. What i mean, is that i want to track down from where my other program *client updater * is downloading a patch from.


Let me try to elaborate if im unclear : 

Client connects to a server to download a patch 

i want to know whats the adress of the server and the path to the patch so i dont really need to use the clien. any suggestions ? thanks in advance.

---

### Post by spd106 on 2009-10-04
You can see the current open (TCP) connections using the following command line tool.
```
netstat -t
```

Otherwise you might try running tcpdump, which should be installed by default or the venerable Wireshirk, which is in the Universe repository.

---

