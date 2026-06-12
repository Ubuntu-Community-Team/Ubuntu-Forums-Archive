---
title: "No-IP Installation Issues"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by aaroncam2 on 2011-03-13
After using apt to install noip2, the installer hangs up when trying to create the .conf file. I've already tried creating the directory and .conf file prior to installation and it still doesn't work. Any Ideas?

```
aaron@aaron-netbook:~$ sudo apt-get install noip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  noip2
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/85.8kB of archives.
After this operation, 266kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package noip2.
(Reading database ... 154141 files and directories currently installed.)
Unpacking noip2 (from .../noip2_2.1.9-3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up noip2 (2.1.9-3) ...

Auto configuration for Linux client of no-ip.com.

You have entered an incorrect username
	-or-
an incorrect password for this username.
 * Creating a read-write copy of the noip2 configuration...                     cp: cannot stat `/var/lib/noip2/noip2.conf': No such file or directory
                                                                         [fail]
 * Starting No-IP.com dynamic address update noip2                              Can't locate configuration file /var/lib/noip2/noip2.conf. (Try -c). Ending!

                                                               
```

---

