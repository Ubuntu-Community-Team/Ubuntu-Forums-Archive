---
title: "Broken Graphics after ppa driver atempted install"
date: 2010-03-09
forum: Mythbuntu
---

### Post by itlarson on 2010-03-09
Once again I have hosed myself.  I tried to install the 195 drivers,  which didn't work, and now I can't re-install the 185 drivers.  

itl@mythbox:~$ sudo apt-get install  nvidia-glx-185 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-185
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.1MB of archives.
After this operation, 51.6MB of additional disk space will be used.
(Reading database ... 173408 files and directories currently installed.)
Unpacking nvidia-glx-185 (from .../nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-195'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How can I fix this?

---

### Post by itlarson on 2010-03-09
Here's synaptic's output:

E: /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb: subprocess new pre-installation script returned error exit status 2

---

### Post by nickrout on 2010-03-09
try removing all the 195 stuff THEN install 185?

---

### Post by itlarson on 2010-03-10
I gave up and attempting a reinstall.

---

