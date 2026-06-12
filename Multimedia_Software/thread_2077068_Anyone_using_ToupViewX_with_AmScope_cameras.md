---
title: "Anyone using ToupViewX with AmScope cameras?"
date: 2012-10-27
forum: Multimedia Software
---

### Post by twgray on 2012-10-27
Has anyone successfully used ToupViewX with the Amscope cameras;  specifically, the MU300 camera? Or, has anyone been able to get an Amscope camera to work under Ubuntu with any software?

---

### Post by a06 on 2012-12-30
> **twgray said:**
> Has anyone successfully used ToupViewX with the Amscope cameras;  specifically, the MU300 camera? Or, has anyone been able to get an Amscope camera to work under Ubuntu with any software?

I just got ToupViewX running with an MU130 on Ubuntu 10.04 LTS.

My first attempt failed like so:[INDENT][FONT=Courier New]$ sudo ./ToupViewX[/FONT]
[FONT=Courier New]./ToupViewX: error while loading shared libraries: libbz2.so.1: cannot open shared object file: No such file or directory[/FONT]
[/INDENT]And ldd confirmed:[INDENT][FONT=Courier New]$ ldd ./ToupViewX[/FONT]
[FONT=Courier New]linux-gate.so.1 =>  (0xf7716000)[/FONT]
[FONT=Courier New]libbz2.so.1 => not found[/FONT]
[FONT=Courier New]libXext.so.6 => /usr/lib32/libXext.so.6 (0xf76e0000)[/FONT]
[FONT=Courier New]libX11.so.6 => /usr/lib32/libX11.so.6 (0xf75c3000)[/FONT]
<snip>
[/INDENT]What I had in place was:[INDENT][FONT=Courier New]$ cd /usr/lib32[/FONT]
[FONT=Courier New]$ ls -l libbz*[/FONT]
[FONT=Courier New]lrwxrwxrwx 1 root root    15 2011-12-28 17:51 libbz2.so.1.0 -> libbz2.so.1.0.4[/FONT]
[FONT=Courier New]-rw-r--r-- 1 root root 70076 2011-12-12 17:40 libbz2.so.1.0.4[/FONT]
[/INDENT]So I added the missing symbolic link:[INDENT][FONT=Courier New]$ sudo ln -s libbz2.so.1.0.4 libbz2.so.1[/FONT]
[/INDENT]After which ToupViewX ran fine.

Too bad it's a really degenerate version of the Windows software. And too bad you need to run it with sudo. But you can shoot some nice stills and I think I prefer using it over an eyepiece.

---

