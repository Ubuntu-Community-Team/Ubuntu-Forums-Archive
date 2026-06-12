---
title: "diskless clients fail to boot until dhcp3-server is restarted"
date: 2009-11-11
forum: Mythbuntu
---

### Post by rlowery on 2009-11-11
When my Karmic (and Intrepid) Mythbuntu server is freshly booted, diskless clients fail to boot until I have restarted dhcp3-server.

I suspect some sort of service start ordering issue, but nothing that starts after dhcp3-server appears to be an issue.

myth-backend:/etc/rc5.d$ ls
README            S19mysql              S23ntp           S91apache2
S01policykit      S20nbd-server         S25bluetooth     S99acpi-support
S10sysklogd       S20nfs-kernel-server  S40dhcp3-server  S99grub-common
S11klogd          S20openbsd-inetd      S50cups          S99laptop-mode
S16ssh            S20samba              S50rsync         S99ondemand
S17mysql-ndb-mgm  S20sysstat            S50saned         S99rc.local
S18mysql-ndb      S20tftpd-hpa          S70dns-clean
S19lirc           S21aumix              S70pppd-dns

Suggestions appreciated

Thanks

-Rob

---

