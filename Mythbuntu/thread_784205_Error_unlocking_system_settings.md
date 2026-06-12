---
title: "Error unlocking system settings?"
date: 2008-05-06
forum: Mythbuntu
---

### Post by morikaweb on 2008-05-06
I'm having a problem were if I go into a system CP like "System Services" or "Shared Folders" and try to unlock it so I can change the settings it gives me an error. 

The exact error is "Could not Authenticate". I'm assuming this is a problem with gksu but how do I fix it?

---

### Post by max69 on 2008-05-06
Hello,
yes I had the same problem. I think you have to install policykit and policykit-gnome and you should be fine.
```
sudo apt-get install policykit policykit-gnome
```

---

### Post by morikaweb on 2008-05-06
Thanks, that worked like a charm.

---

### Post by superm1 on 2008-05-06
Whoops.  Can someone file a bug against mythbuntu-meta?   We can correct this for the 8.04.1 update.

---

### Post by max69 on 2008-05-09
OK, I have filed a bug report. You can confirm it.
[https://bugs.launchpad.net/mythbuntu/+bug/228646]("https://bugs.launchpad.net/mythbuntu/+bug/228646")

---

