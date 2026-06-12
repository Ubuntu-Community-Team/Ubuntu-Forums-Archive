---
title: "ssh disconnect"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by u_kapaley256 on 2010-07-21
Hi,
     This relates to a fedora 13 system at work but i use kubuntu personally so i am posting over here.
     i installed openssh-server which asked me to create the dsa and rsa keys which i did.after that i tried to ssh from another system which gave me the man-in-the-middle attack so i cleared up the known_hosts file.now it disconnects just after authenticating.what could be wrong ?
Thanks
Udayan

---

### Post by u_kapaley256 on 2010-07-21
simply added the target hosts to the /etc/hosts.allow file 
did'nt need to do this when i installed the openssh-server on ubuntu !!
Any explanations/discussions would be welcome.....

---

