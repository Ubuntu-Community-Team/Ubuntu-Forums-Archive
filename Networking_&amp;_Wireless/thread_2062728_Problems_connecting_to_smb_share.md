---
title: "Problems connecting to smb share"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by JaySeeJC on 2012-09-25
Having trouble connecting to my network drive at school. Tech support here refuses to help so i turn to the ubuntu community and possible someone attending my school.
```

sudo mount -t cifs -o user=SHERNETXP\\champjon,password=MYPASSWORD //oa-homer-xp2/champjon /mnt/sheridan
mount: wrong fs type, bad option, bad superblock on //oa-homer-xp2/champjon,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```I can access this share typing it into dolphin, so i know the address and my credentials aren't wrong. The windows and mac instructions can be found here: [http://goo.gl/OHkxi](http://goo.gl/OHkxi)

---

### Post by AMSlider on 2012-09-25
Have you looked in /var/log/syslog or run "dmesg"?

---

### Post by alarme on 2012-09-25
You need package smbfs (includes cifs-utils) installed to go

---

### Post by JaySeeJC on 2012-09-25
> **AMSlider said:**
> Have you looked in /var/log/syslog or run "dmesg"?
Yes I have checked my dmsg. It tells me the exact same thing the mount command's telling me. 

> **alarme said:**
> You need package smbfs (includes cifs-utils) installed to go
Thanks for the advice. Unfortunately i won't be back at school til thursday, so i'll post back here when i get it working (or not) then.

---

