---
title: "fglrx 8.26.18 working with 3D, but lib dependencies broken"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by pascal_belron on 2006-07-04
I installed the latest ATI drivers (64 bits) following the second method on [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"). Everything works great, including 3D (first time for me with this new 1900 XT). Except that I got a few dependencies problem. If I try to run fireglcontrolpanel, here is the message I get:
> fireglcontrolpanel: error while loading shared libraries: libXft.so.2: cannot op                             en shared object file: No such file or directory

Problem is that I got this shared library in /usr/lib/. Is there some sort of LD_LIBRARY_PATH I need to configure ? Mine is empty at the moment so it may be the source of the problem. Any ideas ?

---

### Post by whatever on 2006-07-04
[QUOTE=pascal_belron]Problem is that I got this shared library in /usr/lib/.[/QUOTE]
you might need the 32bit version? just guessing...

but before you waste a lot of time trying to fix this problem, you should know that
[list]
[*]the control panel is quite useless. there are no 3d options to configure there, only desktop setup and gamma settings.
[*]all settings can be changed with the **aticonfig** commandline tool.
[*]afaik the controlpanel is open source, a self-compiled version might work better.
[/list]

---

