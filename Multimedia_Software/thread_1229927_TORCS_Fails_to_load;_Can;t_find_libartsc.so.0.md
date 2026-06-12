---
title: "TORCS Fails to load; Can;t find libartsc.so.0"
date: 2009-08-02
forum: Multimedia Software
---

### Post by medic3 on 2009-08-02
Hello,

I'm an old UNIX geek but this is my first foray into Linux.  I'm running Ubuntu 9.04.  This box is going into my media room so I wanted to load a driving game for the kids, Torcs 1.3.1.  After working through several installation issues with missing libraries, I finally got it to install. However it won't load.  When I start it from the shell using the debug option (-d), I get the following messages:[I]

GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) Starting program: /usr/local/games/torcs/lib/torcs-bin -l /home/medic3/.torcs -L /usr/local/games/torcs/lib -D /usr/local/games/torcs/share
/usr/local/games/torcs/lib/torcs-bin: error while loading shared libraries:** libartsc.so.0: cannot open shared object file: No such file or directory**

Program exited with code 0177.
(gdb) No stack.
(gdb) quit

Is there another package that I need to load.  Trying to find out more info on the Internet only led me to RPM MPLAYER packages.

Medic3
[/I]

---

