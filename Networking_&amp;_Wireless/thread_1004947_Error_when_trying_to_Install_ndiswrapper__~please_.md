---
title: "Error when trying to Install ndiswrapper  ~please help"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by Nocookiepuffs4u on 2008-12-07
I get the following message when trying to install "NDISwrapper" through the "Add/Remove Application" =

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


any help will be appreciated :)

---

### Post by Ayuthia on 2008-12-07
> **Nocookiepuffs4u said:**
> I get the following message when trying to install "NDISwrapper" through the "Add/Remove Application" =

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


any help will be appreciated :)
Have you tried going into the Terminal and typing:
```
sudo dpkg --configure -a
```If so, were there any error messages?

From that message, it looks like the system had problems that last time you installed/removed an application.

---

### Post by Nocookiepuffs4u on 2008-12-07
The code worked and was successfully installed =)

Thanks, your my new hero!

---

### Post by Ayuthia on 2008-12-07
Can I now have some cookie puffs?

---

