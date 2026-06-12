---
title: "problems with Internet"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by thempus on 2009-12-06
Today I did the latest security updates, and now only have internet on skype and Deluge. In the programs center, firefox, amsn and opera, I can not access the Internet.

I have Ubuntu 9.10

Someone can tell me what to do to solve this problem?

I have a 3G/mobile internet access.

Tanks

---

### Post by gorlok on 2009-12-06
I have a similar problem. Firefox, pidgin and xchat stopped working yesterday after I did an update. Seems to be a problem connection to URL:s. Torrents (deluge) are still working fine. My connection is 10mbit wired. Help please!

---

### Post by thempus on 2009-12-06
I have solve the problem :D

After the upgrade, the nameserver have been deleted.

sudo gedit /etc/resolv.conf

Enter the nameserver in the file.

;)

---

### Post by Iowan on 2009-12-06
Hope it stays - that file has a habit of getting overwritten. If it does, there are (probably) some options to fix it...

---

