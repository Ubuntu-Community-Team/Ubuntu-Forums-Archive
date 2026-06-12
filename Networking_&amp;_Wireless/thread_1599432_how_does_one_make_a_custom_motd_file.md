---
title: "how does one make a custom motd file?"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Muster Mark on 2010-10-17
Hi,

so I am setting up my computer as an ssh server and wanted to customise the motd file, but the thing gets overwritten every time by the default message (why do they call it message of the day if you can't put a message there?).  After some searching around it seems that I could install the update-motd package to do this, but the description says it has been integrated into pam_motd in the libpam-modules.  I have the package libpam-modules installed, but can't figure out how to do this.  Any how-to's out there?

Thanks a million.

EDIT: For the record, nowhere on my file system is there a motd.tail file, for some reason.

---

### Post by btindie on 2010-10-17
You have to create /etc/motd.tail and put what ever you want in there... Also take a look in /etc/update-motd.d/ to see how motd is built.

SSH also supports it's own [login banner]("http://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html")

---

