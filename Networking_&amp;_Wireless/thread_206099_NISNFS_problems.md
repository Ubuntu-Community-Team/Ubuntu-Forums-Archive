---
title: "NIS/NFS problems"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by pclancy on 2006-06-29
I'm setting up a server and 10 clients, and I'm having quite a few problems.  On both the server and the clients I'm getting the HAL inilitization error and an error talking about dbus.  Most noticable the computer has been slowed down so much that it takes 20 minutes to open firefox.  I keep getting this error: ```
YPBINDPROC_DOMAIN: Domain not bound
```

I've been using an O'Reilly book that goes over how to set up NIS, the NIS howto ([http://www.linux-nis.org/nis-howto/HOWTO/)](http://www.linux-nis.org/nis-howto/HOWTO/)), and the NFS howto ([http://nfs.sourceforge.net/nfs-howto/)](http://nfs.sourceforge.net/nfs-howto/)).

Is there a good Ubuntu howto on NIS/NFS implenations?  I wasn't sure exactly what was happening with the NIS package in the Ubuntu repository, so I complied from source.

I'd greatly appreciate any assistance.

Thanks.

---

### Post by pclancy on 2006-06-29
I read in a thread about the "YPBINDPROC_DOMAIN: Domain not bound" error that it was caused by a firewall.  We don't have a firewall running inbetween the computers in the network, so could it be an internal software firewall on the machines?

---

### Post by froggay on 2006-09-12
i have the same problem on ubuntu 6.06 sparc server

i used this howto [https://help.ubuntu.com/community/SettingUpNISHowTo]("https://help.ubuntu.com/community/SettingUpNISHowTo")

i'v already used this howto for install nis server/client on ubuntu 4.10 X86 and it worked fine

so .. if someone have an idea

---

### Post by vtripolitakis on 2006-11-26
As I've posted on another thread, firefox and openoffice 2.0 on nis users simply freeze. On the other hand they run smoothly on local users.

Any ideas ?

---

### Post by tsokar on 2006-11-28
just move the .openoffice.org2 directory to a local disk, and make a symlink to your nis account home (works only if you always use the same computer)

---

