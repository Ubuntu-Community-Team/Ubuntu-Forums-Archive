---
title: "ubuntu 9.10 tftp server"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by jimp180 on 2010-01-04
is it possible to get the tftp server that comes with ubuntu 9.10 (I think it is tftp-hpa) to start with the -c option (or whatever option is needed to start the server so it will allow file creation)? if so where and how do I do this? if not is there a different server I should install that will allow me to use the file creation mode?

I tried to change the "/etc/default/ tftpd-hpa" file to read "```
#Defaults for tftpd-hpa
RUN_DAEMON="no"
OPTIONS="-l -s -c /var/lib/tftpboot"
``` (just added the "-c" in the OPTIONS line) but that dosen't seem to work.

Thanks

---

### Post by shairozan on 2010-01-04
One thing you might look at doing is creating a new entry for it in the local section of the startup sequence. 

If you look at the /etc/ directory you will see a document called rc.local

If you edit that file and add the commands you want to run at startup before exit 0 the system will execute them as root. If you need them to run as another user, you could see if it can execute sudo -u <user name> < command > Since it's already root, it shouldn't need a password. Haven't tested it, but it's worth a shot. 

This way you can make sure it'll start accordingly. Also, if this is not a server environment, but rather a desktop, you can add a new entry for it in the system -> preferences -> startup applications menu.

---

### Post by azzid on 2010-03-09
```
#Defaults for tftpd-hpa
RUN_DAEMON="no"
OPTIONS="-l -c -s /var/lib/tftpboot"
```

Should work better. The -s is what takes the supplied path as an argument.

---

