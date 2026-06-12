---
title: "upgrade 23.1 =&gt; 24"
date: 2011-03-31
forum: Mythbuntu
---

### Post by tbaca on 2011-03-31
I am presently running 10.04.2 with 23.1 via the Mythbuntu Repos. I want to upgrade to 24.  Do I just: 
[INDENT]1) backup database, 
2) run “sudo dpkg-reconfigure mythbuntu-repos” and select .24 instead of .23.1?[/INDENT]

Thanks,

---

### Post by tgm4883 on 2011-03-31
> **tbaca said:**
> I am presently running 10.04.2 with 23.1 via the Mythbuntu Repos. I want to upgrade to 24.  Do I just: 
[INDENT]1) backup database, 
2) run “sudo dpkg-reconfigure mythbuntu-repos” and select .24 instead of .23.1?[/INDENT]

Thanks,

Yep, except you will also need 

3) apt-get update
4) apt-get upgrade

---

### Post by tbaca on 2011-03-31
Thanks!

---

