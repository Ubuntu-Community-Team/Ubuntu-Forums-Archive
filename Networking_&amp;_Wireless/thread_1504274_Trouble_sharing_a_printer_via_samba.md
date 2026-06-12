---
title: "Trouble sharing a printer via samba"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by frigginacky on 2010-06-07
I'm trying to share a printer on a box running 10.04 with another box running Win 7 Pro.  So far, the windows box can see the printer, but when I try to print to it but nothing actually prints, and then spoolsv.exe starts hogging a whole CPU core. Here's my (probably very wrong) smb.conf:

```
[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

load printers = yes
printing = CUPS
printcap name = CUPS

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no
    use client driver = yes


```

Can anyone tell me what to fix?

---

### Post by frigginacky on 2010-06-09
I just started over using the default smb.conf and now everything seems to work.

---

