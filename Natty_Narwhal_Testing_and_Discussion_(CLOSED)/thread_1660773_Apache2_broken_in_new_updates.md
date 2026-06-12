---
title: "Apache2 broken in new updates"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by siucdude on 2011-01-05
Ok so I don't know how to explain this but the new updates of apache2 have broken something.
Now before any assumptions, this is a development server so its ok but wanna report it and don't know where to begin.
I have this on a static IP and I run 5+ testing databases on this for various clients
OCS, Nolapro, Ticket System, GLPI, 
Anyways I CAN access the sites fine, but when i try to login as user or admin I get errors, and I try every browser outhere to see if its browser related. 
NO luck if anyone has any idea please send me a private message and I will give you the link to the site, I don't want to post this here.
Anyways, just curious if anyone has had issues on this also? Again its Natty and its development and testing...
Thank You
TJ

---

### Post by cariboo on 2011-01-05
What kind of errors if any are you getting in /var/log/apache2/error.log?

---

### Post by siucdude on 2011-01-05
I attached the error log, there are things that I compared from last week and found them to be the same, 
Like loading the xcached.so, I have not found time to clean it up. Will do over the next 24 hours, and mod_webauth I was trying to disable my mods tonight and work through that.
Let me now if you need anything else.
TJ

---

### Post by siucdude on 2011-01-06
Got some juicy info from gdb...
If anyone has ideas let me know.
thx

---

### Post by dr_kabuto on 2011-01-08
[https://bugs.launchpad.net/bugs/697105](https://bugs.launchpad.net/bugs/697105)

---

### Post by siucdude on 2011-01-08
thank you his updated package worked.

---

