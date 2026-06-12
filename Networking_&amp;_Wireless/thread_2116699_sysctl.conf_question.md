---
title: "sysctl.conf question"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by KB3MKD on 2013-02-16
Something damaged my sysctl.conf file in ubuntu server 12.10. Can somebody tell be what is in there by default?

---

### Post by schragge on 2013-02-16
My is empty (Debian wheezy), so is the */etc/sysctl.d/* directory. That is, not counting comment lines and the README.sysctl.

---

### Post by chili555 on 2013-02-16
```
chili@Think410:~$ locate sysctl.conf
[COLOR="Red"]/etc/sysctl.conf[/COLOR]
/etc/ufw/sysctl.conf
/usr/share/doc/procps/examples/sysctl.conf
/usr/share/man/man5/sysctl.conf.5.gz
```The highlighted line is what you likely want. Mine might as well be empty. Only commented lines exist which may be un-commented to invoke various options.

---

### Post by KB3MKD on 2013-02-16
> **chili555 said:**
> ```
chili@Think410:~$ locate sysctl.conf
[COLOR="Red"]/etc/sysctl.conf[/COLOR]
/etc/ufw/sysctl.conf
/usr/share/doc/procps/examples/sysctl.conf
/usr/share/man/man5/sysctl.conf.5.gz
```The highlighted line is what you likely want. Mine might as well be empty. Only commented lines exist which may be un-commented to invoke various options.

would you mind posting it for me anyway?

---

### Post by chili555 on 2013-02-16
Happy to. As it's a bit lengthy, I zipped a text document attached.

---

