---
title: "vsftpd and SSH respawning too fast, stopped"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by Mintnacho on 2013-02-22
Hi All,

I'm getting this error in dmesg 

```

[   24.499932] init: vsftpd main process ended, respawning
[   24.505215] init: vsftpd main process (1160) terminated with status 1
[   24.505239] init: vsftpd main process ended, respawning
[   24.510800] init: vsftpd main process (1163) terminated with status 1
[   24.510825] init: vsftpd main process ended, respawning
[   24.516414] init: vsftpd main process (1166) terminated with status 1
[   24.516441] init: vsftpd main process ended, respawning
[   24.522076] init: vsftpd main process (1169) terminated with status 1
[   24.522101] init: vsftpd main process ended, respawning
[   24.527505] init: vsftpd main process (1172) terminated with status 1
[   24.527531] init: vsftpd main process ended, respawning
[   24.533106] init: vsftpd main process (1175) terminated with status 1
[   24.533132] init: vsftpd respawning too fast, stopped

```

I'm not sure how to resolve this issue. ftp was running just fine 12 hours ago.

entbox@boc1:/var/log$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"

suggestions appreciated.

---

### Post by Doug S on 2013-02-22
I think, but am not sure, this issue appears when the configuration file is wrong, or even just the default, and the program can not start. I tested this theory with a different program one time, on [another thread]("http://ubuntuforums.org/showthread.php?t=2070919&highlight=respawning").

---

### Post by Mintnacho on 2013-02-22
It's giving this error for SSH and VSFTPD . I haven't touched anything with regards to ssh and vsftpd worked just fine one minute than the next ..error

---

### Post by zawmn83 on 2013-04-24
Hi

Same problem here. 
I found one issue at [https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/831907](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/831907)
But even after I comment [COLOR=#333333][FONT=Ubuntu Mono]rsa_cert_file in vsftpd.conf, the issue can't solve.

I didn't find [/FONT][/COLOR]ssl_enable=YES in my vsftpd.conf.  I think the default of this setting is NO.
I also try ssl_enable=NO, but issue not solve.

Finally, I replace vsftpd.conf file with vsftpd.con file from another working ubuntu.
It is working now.

---

### Post by Doug S on 2013-04-24
Could you post the differences between the two files? It would be good to isolate and document the actual configuration change that changed it from not working to working.

---

