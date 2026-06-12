---
title: "Jack Audio and C programming - Trouble getting started!"
date: 2013-08-23
forum: Multimedia Software
---

### Post by valveirs on 2013-08-23
Greetings,

Has anyone succeeded in compiling under Ubuntu a simple c program that successfully links with the Jack libraries?
(I have tried under both Ubuntu 12.04 and 13.04 without success.)

I am trying to compile the metro.c example file that comew with the Jack source in the example_clients folder.  And even though my Jack libraries are where they are supposed to be, the linker can't find the needed entry points.

For example, when I try to compile metro.c, I get lots of underfined references.
 gcc -o metronome `pkg-config --cflags--libs jack` metro.c 
/tmp/ccBP95ml.o: In function`process_silence':
metro.c:(.text+0x46): undefinedreference to `jack_port_get_buffer'
/tmp/ccBP95ml.o: In function`process_audio':
metro.c:(.text+0x89): undefinedreference to `jack_port_get_buffer' 
etc.
 
$ pkg-config --cflags --libs jack
returns the following paths
-I/usr/local/include  -L/usr/local/lib -ljack -lpthread -lrt  

One possibly odd thing is that my usr/local/lib folder has multiple links to jack files.  Here is the directory listing:

drwxr-xr-x 2 root root    4096 Aug 22 19:45 jack
-rwxr-xr-x 1 root root     937 Aug 22 19:45 libjack.la
-rwxr-xr-x 1 root root     973 Aug 22 19:45 libjackserver.la
lrwxrwxrwx 1 root root      23 Aug 22 19:45 libjackserver.so -> libjackserver.so.0.0.28
lrwxrwxrwx 1 root root      23 Aug 22 19:45 libjackserver.so.0 -> libjackserver.so.0.0.28
-rwxr-xr-x 1 root root  438058 Aug 22 19:45 libjackserver.so.0.0.28
lrwxrwxrwx 1 root root      17 Aug 22 19:45 libjack.so -> libjack.so.0.0.28
lrwxrwxrwx 1 root root      17 Aug 22 19:45 libjack.so.0 -> libjack.so.0.0.28
-rwxr-xr-x 1 root root  212674 Aug 22 19:45 libjack.so.0.0.28
-rw-r--r-- 1 root root  621792 Apr 10 19:37 libportaudio.a
-rwxr-xr-x 1 root root    1005 Apr 10 19:37 libportaudio.la
lrwxrwxrwx 1 root root      21 Apr 10 19:37 libportaudio.so -> libportaudio.so.2.0.0
lrwxrwxrwx 1 root root      21 Apr 10 19:37 libportaudio.so.2 -> libportaudio.so.2.0.0
-rwxr-xr-x 1 root root  488410 Apr 10 19:37 libportaudio.so.2.0.0 

If anyone has a simple working c program and is willing to share their directory structure, perhaps I can get this working.

Thanks,
Val

---

