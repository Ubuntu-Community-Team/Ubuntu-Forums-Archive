---
title: "Ubuntu/Windows mixed environment, one user repository"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by hansheijmans on 2012-12-07
Hello all,

I am running a couple of machines equipped with Ubuntu 12.10, of which one is a combined Samba and NFS file server. I am also running a couple of Windows 7 machines which connect to the Samba file shares (when access is needed) on the machine mentioned above.

On all machines, both Ubuntu and Windows, I have created the same users which represent the members of my family, but I had to create the users on all machines separately.

Would it be possible to maintain one user repository (like LDAP) on e.g. the Samba/NFS machine to which users on this machine and all other machines can authenticate with? I know there are solutions like Kerberos and so on but I don't have any experience setting it up.

As the Samba/NFS machine is not really a server but also used as workstation, the machine gets powered off from time to time, can users still log in on the other Ubuntu and Windows machines with cached credentials when the LDAP server is down?

Any suggestions?

Thanks for your help!

Note: I'm not using Active Directory on either of the Windows machines and I don't plan to use it.

---

### Post by hansheijmans on 2012-12-18
Anyone?

---

### Post by hansheijmans on 2013-04-29
Guess Google is my best friend...:(

---

### Post by SenileToad on 2013-04-29
Ha, I know how you feel. My first thread ever was never responded to! :O

---

