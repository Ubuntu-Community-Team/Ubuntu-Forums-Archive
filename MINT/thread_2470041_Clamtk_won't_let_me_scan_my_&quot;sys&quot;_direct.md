---
title: "Clamtk won't let me scan my &quot;sys&quot; directory"
date: 2021-12-18
forum: MINT
---

### Post by mintyfresh77 on 2021-12-18
Hi. I'm using linux mint 20 and i tried using clamtk to scan my "sys" directory, but it wont let me. How can I solve that problem. Thank you.

---

### Post by deadflowr on 2021-12-18
*Thread moved to **MINT***

---

### Post by The Cog on 2021-12-18
I don't think you should be scanning /sys. It's not real files in there, it's a view of in-memory system settings, represented as files so you can see (and maybe change) internal system settings on the fly. This is true of /sys, /proc and /dev. ("files" in /dev are device driver interfaces).
[https://www.geeksforgeeks.org/linux-directory-structure/](https://www.geeksforgeeks.org/linux-directory-structure/)

---

### Post by ActionParsnip on 2021-12-18
You don't need to. /sys is an interface to the kernel. Specifically, it provides a filesystem-like view of information and configuration settings that the kernel provides, much like /proc. Writing to these files may or may not write to the actual device, depending on the setting you're changing. It isn't only for managing devices, though that's a common use case.

---

### Post by mintyfresh77 on 2021-12-21
Thanks for the help

---

### Post by mintyfresh77 on 2021-12-21
Hi. I'm still scanning my system with clamtk, and some files from the timeshift directory came up. Is it possible that there is something wrong in timeshift, or is that a "red herring'?

---

### Post by yancek on 2021-12-23
It's likely to be a falso positive but if you're paranoid about it, you might try another antivirus software program to see what it says.

---

