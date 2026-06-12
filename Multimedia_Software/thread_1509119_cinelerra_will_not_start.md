---
title: "cinelerra will not start"
date: 2010-06-13
forum: Multimedia Software
---

### Post by goneskiing on 2010-06-13
running on lucid - installed cinelerra and adjusted memory and symlinked 

laptop:~$ sudo sysctl -p
kernel.shmmax = 0x7ffffff
laptop:~$ sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2

it only flashes the startup screen and then dies - here is terminal output:


Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on gio 25 mar 2010, 23.45.24, UTC

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
signal_entry: got SIGSEGV my pid=7656 execution table size=2:
    mwindow.C: create_objects: 1306
    mwindow.C: create_objects: 1309
signal_entry: lock table size=0
BC_Signals::dump_buffers: buffer table size=0
BC_Signals::delete_temps: deleting 0 temp files
SigHandler::signal_handler total files=0
Aborted

---

