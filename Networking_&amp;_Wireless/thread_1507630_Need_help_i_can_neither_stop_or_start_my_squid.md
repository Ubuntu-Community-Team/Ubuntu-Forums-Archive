---
title: "Need help: i can neither stop or start my squid"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by metabee on 2010-06-11
i wanna make my ubuntu  *server *10.04 pc as [COLOR=Lime]**proxy server**[/COLOR].......
When i was install the packet ( squid actually), and there is no problem........
here the syntax:
```
root@metabee:~# apt-get install squid
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  logcheck-database resolvconf
The following NEW packages will be installed:
  squid
0 upgraded, 1 newly installed, 0 to remove and 43 not upgraded.
Need to get 0B/766kB of archives.
After this operation, 1,937kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package squid.
(Reading database ... 56979 files and directories currently installed.)
Unpacking squid (from .../squid_2.7.STABLE7-1ubuntu12_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up squid (2.7.STABLE7-1ubuntu12) ...


```But the prob was appear, when i wanna restart my **squid** :confused::confused:
```
root@metabee:~# /etc/init.d/squid restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service squid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart squid
squid start/running, process 2781
root@metabee:~# ^C
root@metabee:~# service squid restart
squid start/running, process 2796
root@metabee:~# service squid restart
squid start/running, process 2809
root@metabee:~# stop squid
squid stop/waiting
root@metabee:~# grep | squid
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
root@metabee:~# grep| squid
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
2010/06/12 07:57:49| Squid is already running!  Process ID 2818
root@metabee:~# stop squid
stop: Unknown instance:

```Please help me to resolve this..........[IMG]http://www.kaskus.us/images/smilies/mewek.gif[/IMG]
i'am really sorry if [COLOR=#000000]my conversation[/COLOR] is bad........... I'am from Indonesia):P........doesn't have a good **english**........

---

### Post by vaxius on 2010-06-13
I confirm. This makes squid useless to me.

Edit: I had failed to define one of my acl names. Fixed it and problem went away.

---

### Post by mehturt on 2010-08-09
[https://bugs.launchpad.net/ubuntu/+source/squid/+bug/573853](https://bugs.launchpad.net/ubuntu/+source/squid/+bug/573853)

---

### Post by gendit on 2011-08-11
i can't either to start or stop my squid....the status is stop and waiting...what configuration did you change??

---

### Post by mehturt on 2011-08-11
the bug report says the problem has been fixed, what version of squid are you using?

---

