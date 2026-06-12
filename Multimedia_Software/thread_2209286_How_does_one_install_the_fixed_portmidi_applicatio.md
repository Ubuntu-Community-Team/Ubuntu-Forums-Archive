---
title: "How does one install the fixed portmidi application?"
date: 2014-03-04
forum: Multimedia Software
---

### Post by Dominicus on 2014-03-04
I have Ubuntu 12.04 LTS

I installed the application Frescobaldi, which in turn requires "portmidi" to play midi sounds.

 I get no midi output from Frescobaldi, and its forums point to a bug in the 12.04 portmidi package, which appears to have been resolved and loaded to "update":
[https://bugs.launchpad.net/ubuntu/+source/portmidi/+bug/1110326](https://bugs.launchpad.net/ubuntu/+source/portmidi/+bug/1110326)

How do I apply this fix? 

I've tried removing, reinstalling all packages related to keyword: libportmidi with no change in missing midi sounds.

---

### Post by Yellow Pasque on 2014-03-05
It's in the proposed repo. You can enable it in Updates tab:
```
software-properties-gtk
```
After you do that:
```
sudo apt-get update
sudo apt-get install portmidi
```

Once you have the package, you'll probably want to disable the proposed repo and run 'sudo apt-get update' again.

---

### Post by Dominicus on 2014-03-05
I enabled the "proposed" repo.
The portmidi was not found by name with apt-get.  I used "libportmidi0", removed, reinstalled. Audio till not working.  here's the terminal output:

```
@ubuntu:~$ sudo apt-get install portmidi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package portmidi

me@ubuntu:~$ sudo apt-get install libportmidi0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libportmidi0 is already the newest version.
libportmidi0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
me@ubuntu:~$ sudo apt-get remove libportmidi0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libportmidi-dev libportmidi0 python-pypm
0 upgraded, 0 newly installed, 3 to remove and 19 not upgraded.
After this operation, 517 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 1142519 files and directories currently installed.)
Removing libportmidi-dev ...
Removing python-pypm ...
Removing libportmidi0 ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

me@ubuntu:~$ sudo apt-get install libportmidi0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libportmidi0
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 0 B/20.7 kB of archives.
After this operation, 72.7 kB of additional disk space will be used.
Selecting previously unselected package libportmidi0.
(Reading database ... 1142479 files and directories currently installed.)
Unpacking libportmidi0 (from .../libportmidi0_1%3a200-0ubuntu1.12.04.2_i386.deb) ...
Setting up libportmidi0 (1:200-0ubuntu1.12.04.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

