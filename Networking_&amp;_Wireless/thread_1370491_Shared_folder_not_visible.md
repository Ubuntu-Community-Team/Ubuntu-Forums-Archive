---
title: "Shared folder not visible"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by DeadMetal on 2010-01-02
Hi,

I have two computers running Ubuntu 9.10, both have one shared folder. These were set up via Nautilus.

On computer 1 I can see and use the shared folder of computer 2 just fine.

On computer 2 I can NOT see the shared folder of computer 1 anymore since recently. I has worked in the past.

Some more information: the name of computer 1 is "daniel", the share name is "gedeeld". So the address of the shared folder of computer 1 would be smb://daniel/gedeeld/
Opening this address in Nautilus works fine on computer 1 (that shares the folder), but results in an error on computer 2.

**Error: failed to mount Windows share. Please select another viewer and try again.**

What could be the cause, and how can I fix this?

---

### Post by DeadMetal on 2010-01-02
Solved: both my computer and phone appear to have the same hostname. Therefore accessing the share from the other computer fails, but when I replace the computer name with the pc's IP-adress, it works fine.

---

