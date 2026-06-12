---
title: "Connect to Windows share printer from 10.10"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by hurricanehrndz on 2010-12-06
I am fairly new with linux so please be patient with me. Anyhow I have shared my cpl-300 from my windows 7 machine to my network, so that may print from my linux laptop to it.

Now whenever I go to system -> Administration -> Printing and try and browse for my printer it asks for a username and password any username or password I enter that is on the windows 7 machine gets rejected.

So I tested to see what would happen if you used smbclient to view the shares available from the windows 7 machine, unfortunately it results in another permission error. The funny thing is I can mount a share using "mount -t cifs". I have tried searching the forums for a solution, but haven been able to find one. I was wondering if anyone could help.

---

### Post by hurricanehrndz on 2010-12-06
Ok seems like i found my answer, it seems i need to update samba to 3.5.6, now i need to know how. New thread.

---

