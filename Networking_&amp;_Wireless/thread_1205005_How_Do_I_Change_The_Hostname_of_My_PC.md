---
title: "How Do I Change The Hostname of My PC?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by ADyingSoul on 2009-07-05
Upon installation of Ubuntu I was asked to give my PC a name. Now, post-install, I want to change it. Is this possible? Any help is greatly appreciated.

---

### Post by mhgsys on 2009-07-05
Have a look here
[http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/](http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/)

---

### Post by ADyingSoul on 2009-07-05
I went to the link, but it said it's not permanent, and I don't really understand the instructions. I'm new to Linux. :(

---

### Post by Wobblybob on 2009-07-05
open a Terminal [Applications], [Accessories], [Terminal] and type or copy

**sudo gedit /etc/hostname**

and hit [Enter] you will then be asked for your password, and then the file called hostname which is in the /etc directory will open and it should list your current hostname. Change it and resave then in the same terminal window type or copy and paste,

**sudo /etc/init.d/hostname.sh start**

this should restart the hostname.sh file which will update your hostname immediately and your hostname will permanently he changed.

---

