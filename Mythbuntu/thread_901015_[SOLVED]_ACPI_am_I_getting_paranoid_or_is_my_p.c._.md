---
title: "[SOLVED] ACPI am I getting paranoid or is my p.c. against me?"
date: 2008-08-26
forum: Mythbuntu
---

### Post by Andrew U.K. on 2008-08-26
Hi All,

I'm having trouble with the ACPI.

I'm following the   www.  /help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake

page and all goes well until i hit this bit,

[I]To give mythtv user the permissions we need
[/I]
$ sudo visudo

*Add the following line to the end, making sure it is the only entry for mythtv- if another entry for mythtv exists, replace it with this one:*

    
  %mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown

How on earth do I edit this file. I understand that this file gives access and that's why it won't give dummies like me a break. When I follow the instructions above it makes a temporary file that I cannot open. 

Oh, I better let you know mythtv is my only dabble with linux so far, so please keep it simple.

Many thanks in advance,
Andrew.

---

### Post by stevanbt on 2008-08-26
Hi,
I'm not at my MythBox at the moment, but from memory you need to open a terminal session and type ```
sudo visudo
```.  This should open the file as a temp file and allow you to edit it.  At the bottom of the editor are commands (save, exit etc), when you exit and save the file the editor will copy the temp file over the original.

Sorry I can't be more exact as it's a while since I did this to my MythBox.

Thanks, Steve.

---

### Post by Andrew U.K. on 2008-08-27
Being completely new I didn't understand that vi was an editor, using its own commands and interface.
To change this file, google vi you should get a good how to for using vi.

---

