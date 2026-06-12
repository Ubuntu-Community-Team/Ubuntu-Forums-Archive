---
title: "Segmentation Fault while launching network-admin"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by cdaver on 2010-03-10
Hi All,

I have just installed Ubuntu and am trying to get networking and file sharing to work.

Here is the output from uname -a

*****
Linux Ares 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
*****

Here is the output from running 'sudo network-admin'

****
cdaver@Ares:~$ sudo network-admin
Segmentation fault
cdaver@Ares:~$ network-admin
Segmentation fault
cdaver@Ares:~$ 
****

Please help me figure this out. 
I have done the following
reinstalled gnome-network-admin,
installed policy kit, 
installed and set up samba, 
enabled sharing on ~/share.

Machine does show up under smb://workgroup/
Machine does NOT show up under network:///

I just cant get network-admin to launch.
Please Help...

Thanks,
cdaver

---

