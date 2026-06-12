---
title: "OSS not compiling snd module"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by madubuntuer on 2006-08-13
I installed thelinux-source package and setup the symbolic link to where i extracted the archive but i get the following errors
src/sndshield.c:1131: error: syntax error before ‘)’ token
src/sndshield.c: In function ‘udi_spin_unlock’:
src/sndshield.c:1137: error: ‘spinlock_t’ undeclared (first use in this function)
src/sndshield.c:1137: error: syntax error before ‘)’ token
src/sndshield.c: At top level:
src/sndshield.c:1820: error: variable ‘__this_module’ has initializer but incomplete type
src/sndshield.c:1822: error: unknown field ‘name’ specified in initializer
src/sndshield.c:1822: warning: excess elements in struct initializer
src/sndshield.c:1822: warning: (near initialization for ‘__this_module’)
src/sndshield.c:1822: error: unknown field ‘init’ specified in initializer
src/sndshield.c:1822: warning: excess elements in struct initializer
src/sndshield.c:1822: warning: (near initialization for ‘__this_module’)
Compile failed with -I/usr/src/linux-2.6.15-23-amd64-generic/include

**** Failed to compile the sndshield module ****

/lib/modules/2.6.15-23-amd64-generic/build/include /lib/modules/2.6.15-23-amd64-generic/source/include /usr/src/linux-2.6.15-23-amd64-generic/include
No sndshield module available.
OSS/Linux kernel module not available. Cannot continue.
root@ubuntu:/home/s#

also i'm sure it's correct 

root@ubuntu:/home/s# uname -r
2.6.15-23-amd64-generic

---

