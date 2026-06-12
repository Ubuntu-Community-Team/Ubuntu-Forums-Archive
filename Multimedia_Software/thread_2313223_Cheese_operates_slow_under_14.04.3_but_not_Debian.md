---
title: "Cheese operates slow under 14.04.3 but not Debian"
date: 2016-02-10
forum: Multimedia Software
---

### Post by cam17 on 2016-02-10
I have noticed Cheese doesn't operate properly under Ubuntu it captures but it responds slowly even greys out. I noticed this message in the crash log.

Disassembly: => 0x7fd247cb9cd5:    Cannot access memory at address 0x7fd247cb9cd5
HookError_source_cheese:
 Traceback (most recent call last):
   File "/usr/lib/python3/dist-packages/apport/report.py", line 197, in _run_hook
     symb['add_info'](report, ui)
   File "/usr/share/apport/package-hooks/source_cheese.py", line 11, in add_info
     response = ui.information("Before continuing, please close Cheese if it is already running!\n\nCheese will now be started in debugging mode.\n\nTry to reproduce the problem you are facing\nand 'Close' Cheese.")
 AttributeError: 'NoneType' object has no attribute 'information'



However when I run the latest version of Debian on the same workstation no problems are observed. The only application installed is Open-ssh server and it the machine has been updated.

---

