---
title: "uShare error after upgrade to Ubuntu 11.10"
date: 2011-10-16
forum: Multimedia Software
---

### Post by BigTobster on 2011-10-16
Getting the following error after new upgrade. uShare was fine before but I had to uninstall it for a bit and now I have problems :(.


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ushare is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ushare (1.1a-0ubuntu6) ...
/etc/ushare.conf: 22: Drive/Media/Videos: not found
dpkg: error processing ushare (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 ushare
E: Sub-process /usr/bin/dpkg returned an error code (1)[/QUOTE]
```

Googling has told me that only reformating fixes it which seems a bit drastic. Other methods such as doing "-f install" don't seem to work but it may be that I am doing it wrong - I am a little bit of a n00b with Ubuntu. 

Any ideas? I think I need to take it off "cleanly" and then replace but how to put that in practice I'm not sure - without reformatting. 

Thanks in advance

---

