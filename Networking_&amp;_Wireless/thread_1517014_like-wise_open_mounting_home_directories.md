---
title: "like-wise open mounting home directories"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by bllusna on 2010-06-24
I am trying to get likewise-open to recognize the home directories that are mounted from our Solaris (Solaris X86 6/09) file server. I have the home directories mounting via autofs to /home/username.  I have the lsassd.reg set to not create the home directories.  HomeDirPrefix is /home and HomeDirTemplate is %H/%U.   If the home directory is already there shouldn’t the system see it and log the user into the mounted  
directory. 



  If this is not possible, if I nfs mounted the home directories not using autofs, would the configuration above work?

---

