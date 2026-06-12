---
title: "problems installing icecast2 via cli"
date: 2011-07-17
forum: Multimedia Software
---

### Post by chris1497 on 2011-07-17
I have been trying to get icecast up and running for a while now.  I am attempting to remove all earlier vestiges of it and reinstall it from the beginning.  I uninstalled it from the ubuntu software center and then manually deleted the folder: /etc/icecast2/

This is the output of  sudo apt-get install icecast2

```
sudo apt-get install icecast2 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ices2
The following NEW packages will be installed:
  icecast2
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/223 kB of archives.
After this operation, 786 kB of additional disk space will be used.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package icecast2.
(Reading database ... 166349 files and directories currently installed.)
Unpacking icecast2 (from .../icecast2_2.3.2-6ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Setting up icecast2 (2.3.2-6ubuntu1) ...
chmod: cannot access `/etc/icecast2/icecast.xml': No such file or directory
dpkg: error processing icecast2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 icecast2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

