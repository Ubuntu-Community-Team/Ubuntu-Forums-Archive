---
title: "Unable to install likewise-open Ubuntu 12.04"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by AnUbunter on 2012-09-12
New to ubuntu and not sure what im doing! :P

I cant install likewise, heres what happens when i try to


jason@jason-ThinkPad-X220-Tablet:~$ sudo apt-get install likewise-openReading package lists... Done
Building dependency tree       
Reading state information... Done
likewise-open is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up likewise-open (6.1.0.406-0ubuntu5) ...
Error: /usr/sbin/lwsmd --start-as-daemon returned 1 (aborting this script)


dpkg: error processing likewise-open (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 likewise-open
E: Sub-process /usr/bin/dpkg returned an error code (1)




pretty sure its not installed properly, how should i reinstall it properly?

---

### Post by chili555 on 2012-09-12
I'd probably try either:```
sudo apt-get install --reinstall likewise-open
```Or, even better, because the package is evidently not made correctly:```
sudo apt-get remove --purge likewise-open
```I know nothing about this package so I am guessing a bit.

---

