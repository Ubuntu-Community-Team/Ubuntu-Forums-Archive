---
title: "Ping can find my ubuntu computer but not it's name"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by Bucephalus01 on 2011-10-12
Hi

I have an ubuntu desktop and a windows 7 desktop and a windows 7 laptop. Now when I ping my other two computers from my windows 7 desktop it works fine if I use ipaddress, but if I try and use hostname it only finds my laptop, and not my ubuntu system.
And when I try pinging my two windows computers from the ubuntu computer it works fine with ip address, but it can't find these computers via hostname.

Does anyone why this happens?

David

---

### Post by Elysius on 2011-10-12
Might be a dns issue, don't know if this still counts for 11.04. Otherwise just add your ip plus hostname in the hosts file on your window clients. (c:\windows\system32\drivers\etc)

Read this thread [http://ubuntuforums.org/showthread.php?t=928776](http://ubuntuforums.org/showthread.php?t=928776)

---

