---
title: "Arpwatch installation/permission problems"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by billykendall on 2013-06-20
Hey guys...I just installed Arpwatch from the repositories. Upon completion of the install I ran 'sudo gedit /etc/arpwatch.conf' and simply ran with 'eth0 -m root' as the only option. Now when I fire off '/etc/init.d/arpwatch restart' I get the following error:

Starting Ethernet/FDDI station monitor daemon: (creating /var/lib/arpwatch/eth0.dat) /etc/init.d/arpwatch: 55: /etc/init.d/arpwatch: cannot create /var/lib/arpwatch/eth0.dat: Permission denied

Anyone have any clues on what might be going wrong here?

EDIT: adding system info: Lubuntu 13.04

Thanks!

-BK

---

### Post by kspen on 2013-07-19
check the permissions in the /var/lib/arpwatch/ or just try to create the file with the required permissions in the directory

---

