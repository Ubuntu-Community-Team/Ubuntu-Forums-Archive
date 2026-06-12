---
title: "Ubuntu equivalence for chkconfig"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by clawes on 2006-06-06
For RPM distros, I use the ***chkconfig*** command to  enable/disble  automatic startup of daemons for various runlevels.E.g. 
#chkconfig dhcpd on
#chkconfig --level 35 named off

What the Ubuntu equivalent command?

---

### Post by lao_V on 2006-06-06
try update-rc.d

---

### Post by nkhansen on 2006-06-06
You rename and/or chmod -x the various in /etc/rc_.d

Or you use BUM (Boot-up-Manager).

If a "smart" CLI-tool exists for managing this, I don't know about (still pretty likely, though :-))

---

### Post by motin on 2007-02-25
> **clawes said:**
> For RPM distros, I use the ***chkconfig*** command to  enable/disble  automatic startup of daemons for various runlevels.E.g. 
#chkconfig dhcpd on
#chkconfig --level 35 named off

What the Ubuntu equivalent command?

Here is some good tips: [http://ubuntuforums.org/showthread.php?t=20583](http://ubuntuforums.org/showthread.php?t=20583)

Haven't found a drop-in replacement though... summarized here: [http://ubuntuforums.org/showthread.p...00#post2212100](http://ubuntuforums.org/showthread.p...00#post2212100)

---

