---
title: "namebench-1.1.tgz installation trouble..."
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by selvavicto on 2010-02-14
i have tried to install  namebench-1.1.tgz i got the following result""
selva@selva-desktop:~$ sudo apt-get install python-tk
[sudo] password for selva: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-tk is already the newest version.
selva@selva-desktop:~$ tar xzvf namebench-1.1.tgz
tar: namebench-1.1.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
selva@selva-desktop:~$ 


i'm a new user ple help me........

---

### Post by RobsonGrangeiro on 2010-05-07
Hi,
 
First you need to download the namebench-1.xxx.tgz. You can do this in Google Code site - [http://code.google.com/p/namebench/downloads/list](http://code.google.com/p/namebench/downloads/list)
 
Now you run the untar command.

---

### Post by chili555 on 2010-05-07
Moreover, downloads go, by default, to either desktop or Downloads, depending on your Firefox version. Find out in Edit > Preferences > General > Downloads. If your downloads go to Desktop, then do:```
cd Desktop
tar xzvf etc., etc.
```In other words, change to the directory containing the file first.

---

