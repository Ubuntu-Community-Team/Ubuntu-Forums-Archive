---
title: "gtkpod error"
date: 2008-12-26
forum: Multimedia Software
---

### Post by wbrokow1 on 2008-12-26
I get this error when I load programs:

```


woody@woody-desktop:~$ sudo apt-get install gtkpod-aac
[sudo] password for woody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtkpod-aac is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.1) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone have any idea what the problem is?
acpid seems to fail.
WHat is that?
Any help is appreciated
Thanks

---

