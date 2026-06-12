---
title: "screen segmentation fault"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by el_sordo on 2010-09-30
Anyone running into a segfault when running screen/byobu? I upgraded to Maverick from Lucid. Excerpt from 'strace screen' (last few lines):

open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Segmentation fault (core dumped)

---

### Post by el_sordo on 2010-10-06
I found that it segfaults when the nis daemon is not running. Starting nis makes screen and byobu run fine.

---

### Post by el_sordo on 2010-10-07
OK...maybe I'll submit a bug report. kern.log show's this:

[  165.779197] screen[2059]: segfault at bfdfefdf ip 00615398 sp bfdf36ec error 6 in libnss_files-2.12.1.so[613000+a000]

Again...this is resolved by starting NIS.

---

### Post by cariboo on 2010-10-07
I use screen here with out NIS.

---

