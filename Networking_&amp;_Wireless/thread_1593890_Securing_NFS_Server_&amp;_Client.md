---
title: "Securing NFS Server &amp; Client"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Armand-Pahner on 2010-10-11
Hello. I have been using ubuntu off and on for nearly a year. Today I decided to ditch samba and try NFS for the first time. After a rough hour I finally got it working but since it does not as for a username & password like samba I was wondering if there was any tips to making sure it is as secure as possible without using SSH. 

my /etc/exports file is setup like this:

/media/disk 192.168.1.155(rw,secure,root_squash) username(rw,fsid=0,secure,no_subtree_check,async)


My /etc/hosts.deny has this:

portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL

And my /etc/hosts.allow has this:

portmap: 192.168.1.155
lockd: 192.168.1.155
rquotad: 192.168.1.155
mountd: 192.168.1.155
statd: 192.168.1.155

Am I missing anything else?

---

