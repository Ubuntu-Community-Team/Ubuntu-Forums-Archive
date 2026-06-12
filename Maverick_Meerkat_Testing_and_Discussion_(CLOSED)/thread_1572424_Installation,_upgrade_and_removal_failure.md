---
title: "Installation, upgrade and removal failure"
date: 2010-09-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Katsu!! on 2010-09-11
I tried to open progress quest this morning and got a message saying child process not found, so I decided to try and reinstall. I get this:

$ sudo apt-get install pq
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pq is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba-common (2:3.5.4~dfsg-1ubuntu4) ...
/var/lib/dpkg/info/samba-common.postinst: 97: ucf: not found
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.5.4~dfsg-1ubuntu4); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin; however:
  Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 samba-common
 samba-common-bin
 samba
sh: /usr/sbin/localepurge: not found
E: Problem executing scripts DPkg::Post-Invoke 'if [ -x /usr/sbin/localepurge ] && [ $(ps w -p $PPID | grep -c remove) != 1 ]; then /usr/sbin/localepurge; else exit 0; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 


So I have two questions, why does my terminal not show the Josh@josh-laptop or whatever it used to show at the beginning of each line.

And what the hell is wrong. I tried following some steps to sort samba out and it un-installs fine, but then it wont re-install without giving me the error.

Edit: I'm running maverick >.<

---

### Post by andrewthomas on 2010-09-14
If you are running maverick, then you should post your questions in the maverick forum.

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

try

```
sudo apt-get update && sudo apt-get upgrade
```

and post the error message if you get one

---

### Post by Katsu!! on 2010-09-14
I got samba errors, lots of them, anyway, ended up re-installing cause the whole system went down, turns out something with localepurge was upsetting my system, not long done a backup before updating to 10.10 so I just re-installed 10.04

---

