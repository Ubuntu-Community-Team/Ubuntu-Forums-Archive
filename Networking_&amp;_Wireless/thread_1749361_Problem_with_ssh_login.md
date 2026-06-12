---
title: "Problem with ssh login"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by paxxus on 2011-05-04
Hi,

I have installed ubuntu 11.04 and I'm now trying to connect to existing SUSE servers on the LAN.

My home directory has a shared NFS mounted home on the SUSE servers while my home on the ubuntu machine is local.

I can log in using ssh to all the SUSE servers except one. I get:

ssh: connect to host srv3 port 22: Connection refused

If I use the IP address of srv3 directly it works. Also, before I changed the default machine name ("ubuntu") I could log into srv3.

nslookup srv3 works OK.
ping srv3 works OK.

Even if I completely delete the .ssh directory in both my ubuntu home and in my shared home on the SUSE servers I still cannot log in using the srv3 name, only direct IP address works.

I'm thinking that the login I did to srv3 before I changed the machine name for the ububtu machine must have goofed up something  :confused:

---

### Post by paxxus on 2011-05-04
Another observation: If I boot the ubuntu PC into Windows 7 then I can connect to srv3 with ssh. The IP and computer name is the same in Windows as when I boot into ubuntu.

Since the situation persists even when deleting the .ssh directory, the question is where ssh stores other state which might have become stale. Hopefully someone has an idea.

---

### Post by paxxus on 2011-05-11
OK, I found the problem - I had made a typo in the /etc/hosts file. A grep for srv3 in the /etc folder revealed my mistake.

---

