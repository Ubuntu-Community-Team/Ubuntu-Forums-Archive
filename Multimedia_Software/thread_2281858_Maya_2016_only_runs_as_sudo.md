---
title: "Maya 2016 only runs as sudo?"
date: 2015-06-10
forum: Multimedia Software
---

### Post by r.lubken on 2015-06-10
[COLOR=#000000][FONT=FrutigerNextW04-Regular]I installed Maya 2016 and it only runs when using sudo (root).[/FONT][/COLOR]
[COLOR=#000000][FONT=FrutigerNextW04-Regular]We are using Ubuntu 14.04 x64. This is the error I get when running as a normal user:[/FONT][/COLOR]

> [COLOR=#000000][FONT=FrutigerNextW04-Regular]terminate called after throwing an instance of 'avro::Exception'
what(): Cannot open file: Permission denied
Stack trace:
/lib/x86_64-linux-gnu/libc.so.6(+0x36d40) [0x7fd155579d40]
gsignal
abort
__gnu_cxx::__verbose_terminate_handler()
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x5e836) [0x7fd155ff5836]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x5e863) [0x7fd155ff5863]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x5eaa2) [0x7fd155ff5aa2]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x1ab3e2) [0x7fd1544e23e2]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x1af11a) [0x7fd1544e611a]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x13676d) [0x7fd15446d76d]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x13236a) [0x7fd15446936a]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x13242c) [0x7fd15446942c]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x12cb17) [0x7fd154463b17]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x129ed2) [0x7fd154460ed2]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0xe38b1) [0x7fd15441a8b1]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x13a636) [0x7fd154471636]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x13a259) [0x7fd154471259]
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/lib/libMC3.so.8(+0x139e99) [0x7fd154470e99]
CMLFacade::Initialize(CMLWaypoint*, wchar_t const*, wchar_t const*, wchar_t const*, int, unsigned int, long long, long long, MC3_MODE, wchar_t const*)
TCIPClient::initialize()
TCIPClient::TCIPClient()
TCIPClient::theOne()
TbaseApp::cipReportStartup()
TbaseApp::initGeneral()
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/bin/maya.bin() [0x415a52]
Tapplication::start()
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/bin/maya.bin() [0x40e6ff]
main
__libc_start_main
/mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/bin/maya.bin() [0x40debd][/FONT][/COLOR]
[COLOR=#000000][FONT=FrutigerNextW04-Regular]Segmentation fault (core dumped)[/FONT][/COLOR]

This is what I get when running maya in debug (gdb) mode:
> Starting program: /mnt/maitre-d/linux/maya/autodesk2016/maya2016-x64/bin/maya.bin -prompt
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7fffc3a40700 (LWP 26457)]
[New Thread 0x7fffc3a2f700 (LWP 26458)]
[New Thread 0x7fffc362e700 (LWP 26459)]
[New Thread 0x7fffc322d700 (LWP 26460)]
[New Thread 0x7fffc2e2c700 (LWP 26461)]
[New Thread 0x7fffc2a2b700 (LWP 26462)]
[New Thread 0x7fffc262a700 (LWP 26463)]
[New Thread 0x7fffc2229700 (LWP 26464)]
[New Thread 0x7fffc1e28700 (LWP 26465)]
[New Thread 0x7fffc1a27700 (LWP 26466)]
[New Thread 0x7fffc1626700 (LWP 26467)]
[New Thread 0x7fffc1225700 (LWP 26468)]
MAYA_DEBUG_NO_SIGNAL_HANDLERS is set.


[New Thread 0x7fff93bf4700 (LWP 26469)]
[New Thread 0x7fff92bb7700 (LWP 26470)]
terminate called after throwing an instance of 'avro::Exception'
  what():  Cannot open file: Permission denied


Program received signal SIGABRT, Aborted.
0x00007fffe30dccc9 in __GI_raise (sig=sig@entry=6) at ../nptl/sysdeps/unix/sysv/linux/raise.c:56
56	../nptl/sysdeps/unix/sysv/linux/raise.c: No such file or directory.


[COLOR=#000000][FONT=FrutigerNextW04-Regular]Any ideas?[/FONT][/COLOR]

---

### Post by TheFu on 2015-06-10
If you ever run with sudo, you may have written files as root into places that root has no business writing files. This is a common problem when people run many GUI programs as root.  In fact, if they do it on a fresh userid, they can prevent many gnome applications from working - ever - with their normal userid.

So, find all the files in your $HOME that are owned by root and have your normal userid become the owner. Then try running it again, post the results, if there are any issues. Please.

Oh - and if the external storage with the program on it isn't on a normal Linux file system, that could be an issue too. Trying to run Linux programs from FAT32, vFAT or NTFS is a bad idea.

---

### Post by r.lubken on 2015-06-11
You are my hero! I did a "chown" all command in my $HOME directory and everything is fixed.

---

### Post by Bucky Ball on 2015-06-11
Please mark as solved using the second link in my signature. Thanks.

---

### Post by TheFu on 2015-06-11
> **r.lubken said:**
> You are my hero! I did a "chown" all command in my $HOME directory and everything is fixed.

Running many (most?) GUI programs with sudo is a bad, bad, bad idea.

---

### Post by Bucky Ball on 2015-06-11
> **TheFu said:**
> Running many (most?) GUI programs with sudo is a bad, bad, bad idea.

Yep. Probably any rather than many or most. There are other theories, but after staff discussion some time ago, we more or less agreed gksudo is probably still the best practice.

```
gksudo <application_name>
```

i.e.

```
gksudo nautilus
```

---

