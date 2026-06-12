---
title: "permission denied !"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by rob42 on 2009-01-29
Hello All
me again - 
ok am still working on installing the rt73drivers and an now attempting to use the gui installer from Kiefer Rodriguez
I have it going to 65% when it hits the following

> Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory


then I get

> All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

Current status: 25 updates [-1].
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
make: *** No rule to make target `install'. Stop.
sudo: ifconfigwlan0: command not found
FATAL: Module rt2570 not found.
Traceback (most recent call last):
  File "rt73install.py", line 126, in start_install
    modprobe = file("rt73-blacklist.temp", 'a')
IOError: [Errno 13] Permission denied: 'rt73-blacklist.temp'


Can someone Please give me some pointers.
Many thanks

Rob

---

