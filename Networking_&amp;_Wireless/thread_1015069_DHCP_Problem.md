---
title: "DHCP Problem"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by aalekso on 2008-12-18
I'm trying to install DHCP server. I tried with the command line, but I'm new so it's too complicated for me! :) When I try to instal GDHCPD it gives me an error:

alekso@alekso:~$ sudo apt-get install gdhcpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gadmin-dhcpd
The following NEW packages will be installed:
  gadmin-dhcpd gdhcpd
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 83.3kB of archives.
After this operation, 348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe gadmin-dhcpd 0.4.4-1 [79.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe gdhcpd 0.4.4-1 [3428B]
Fetched 83.3kB in 3s (24.1kB/s)      
Selecting previously deselected package gadmin-dhcpd.
(Reading database ... 123150 files and directories currently installed.)
Unpacking gadmin-dhcpd (from .../gadmin-dhcpd_0.4.4-1_i386.deb) ...
Selecting previously deselected package gdhcpd.
Unpacking gdhcpd (from .../gdhcpd_0.4.4-1_all.deb) ...
Processing triggers for man-db ...
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gadmin-dhcpd (0.4.4-1) ...

Setting up gdhcpd (0.4.4-1) ...
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have no idea what it is!

Thanks in advance

---

### Post by cariboo on 2008-12-18
HAve a look at this [bug]("http://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389"), there is a workaround in the bug report.

Jim

---

### Post by aalekso on 2008-12-18
thanks. That worked! :guitar:

---

