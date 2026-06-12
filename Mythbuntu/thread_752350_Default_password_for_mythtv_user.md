---
title: "Default password for mythtv user"
date: 2008-04-11
forum: Mythbuntu
---

### Post by aseriesoftubes on 2008-04-11
In a normal Mythbuntu install, is there a default password for the mythtv user? I'm not talking about the MySQL DB password, but rather the password for the actual user, created by default in a Mythbuntu installation, named mythtv. I can't find any reference to this anywhere.

Thanks,

Brent

---

### Post by laga on 2008-04-11
No, the 'mythtv' user doesn't have a password. It's not supposed to be used by anything except for the backend and mythfilldatabase.

---

### Post by aseriesoftubes on 2008-04-11
Got it, thanks. 

Out of curiosity, does the mythtv user have any purpose in a frontend-only install?

---

### Post by superm1 on 2008-04-12
Nope.  You run the frontend as a user in the "mythtv" group, and that's it.

---

### Post by bergqvistjl on 2011-06-30
> **laga said:**
> No, the 'mythtv' user doesn't have a password. It's not supposed to be used by anything except for the backend and mythfilldatabase.

Apologies for bumping, but if this is the case, why am I prompted for a password when i attempt to login as that user? (I want to run mythfilldatabase under than user) I've tried entering my own password, and also no password, but they are both incorrect.

---

### Post by azmyth on 2011-07-01
I just run mythfilldatabase as the normal user I log in as. It doesn't need a password.

---

