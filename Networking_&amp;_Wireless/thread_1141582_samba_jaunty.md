---
title: "samba jaunty"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by milanvora on 2009-04-28
I had samba running fine under 8.1
I upgraded to jaunty on my desktop.
I re-ran all steps under ubuntugeek (howto samba)
Now when i try to connect my latop (windows) to access my shares on my desktop, it doesn't work

any ideas what am i doing wrong ?

---

### Post by inobe on 2009-04-28
welcome

did you take the option to keep your current smb setup during the upgrade ?

also is smb service running ?

---

### Post by milanvora on 2009-04-29
no i asked it to reset it while doing the upgrade, thinking it was anyhow easy to setup
what do you mena by smb running? 
the samba daemon is running

---

### Post by inobe on 2009-04-30
did you backup your smb.conf first ?


if yes simply do

```
cp /etc/samba/smb.conf.backup /etc/samba/smb.conf
```

---

### Post by albinootje on 2009-04-30
> **milanvora said:**
>  I re-ran all steps under ubuntugeek (howto samba)


Can you point out the link for the howto ? Was it this one or another ?
[http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html](http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html)

---

