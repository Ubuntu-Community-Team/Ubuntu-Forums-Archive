---
title: "Problem purging nvidia-glx"
date: 2008-05-08
forum: Multimedia Software
---

### Post by rich257 on 2008-05-08
I am trying to purge the nvidia-glx packages so I can re-install nvidia-glx-new, but there are problems removing nvidia-glx-legacy.  Are these a problem?  How can I fix them?

```
$ sudo aptitude purge ~nnvidia-glx
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  nvidia-glx-legacy{p} nvidia-glx-new{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 15.6MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 155670 files and directories currently installed.)
Removing nvidia-glx-legacy ...
Purging configuration files for nvidia-glx-legacy ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-legacy'
  found `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing nvidia-glx-legacy (--purge):
 subprocess post-removal script returned error exit status 2
Removing nvidia-glx-new ...
Purging configuration files for nvidia-glx-new ...
dpkg - warning: while removing nvidia-glx-new, directory `/usr/lib/tls' not empty so not removed.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-glx-legacy
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  
```

---

### Post by talisfang on 2008-05-08
Try EnvyNg or Envy. EnvyNG for hardy heron. This program does everything about video card drivers. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

