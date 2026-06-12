---
title: "&quot;sudo lshw -C Network&quot; does not return a response"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by RyanRivera on 2010-08-09
I have been attempting to diagnose wireless adapter problems for a little bit now. When I submit "sudo lshw -C network" in the terminal command line and execute, there is no result. It simply jumps lines as if processed, but no "DISABLE, ENABLE, etc" came up. Any ideas on what I am doing wrong? Thank you for your time.

EDIT: It does ask for password verification once the line is entered, but no status of any sort is displayed.

---

### Post by Iowan on 2010-08-10
My system takes a few (several) seconds before it returns results... but it does eventually spit out information. You could try with just **sudo lshw** to see if that returns anything... anything at all.

---

