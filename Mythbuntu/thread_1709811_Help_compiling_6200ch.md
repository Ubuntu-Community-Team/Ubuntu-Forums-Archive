---
title: "Help compiling 6200ch"
date: 2011-03-18
forum: Mythbuntu
---

### Post by yonkiman on 2011-03-18
I've got a fresh install of Mythbuntu 10.10 64 bit, and I'm trying to get the 6200ch channel changer running.  I'm trying to compile the code from  [http://www.mythtv.org/wiki/6200ch](http://www.mythtv.org/wiki/6200ch) but it's not working and I can't figure out what is wrong.  I installed it a few months ago on 9.10 and didn't have any problem - not sure what's up.

Whether I compile it with "cc -std=gnu99 -o 6200ch 6200ch.c -lavc1394 -lrom1394 -lraw1394", or just using the makefile (make), it instantly compiles (no errors or status output at all) and generates the 6200ch executable.

But when I try to run it, I get:

```
~/code/6200ch$ 6200ch
/usr/local/bin/6200ch: line 1: syntax error near unexpected token `newline'
/usr/local/bin/6200ch: line 1: `<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">'

```

Don't know how useful this would be, but I ran the compiler with -v and got this (may be missing the first part because I couldn't redirect output to a file using ">dump.txt"):
[HTML] /usr/lib/gcc/x86_64-linux-gnu/4.4.5/cc1 -quiet -v 6200ch.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase 6200ch.c -mtune=generic -auxbase 6200ch -std=gnu99 -version -fstack-protector -o /tmp/ccmkBpJk.s
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/include-fixed
 /usr/include
End of search list.
GNU C (Ubuntu/Linaro 4.4.4-14ubuntu5) version 4.4.5 (x86_64-linux-gnu)
	compiled by GNU C version 4.4.5, GMP version 4.3.2, MPFR version 3.0.0-p3.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 735b16ccef1a2bfd839f020cdb4a5e95
COLLECT_GCC_OPTIONS='-v' '-std=gnu99' '-o' '6200ch' '-mtune=generic'
 as -V -Qy -o /tmp/ccYZeB3s.o /tmp/ccmkBpJk.s
GNU assembler version 2.20.51 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.20.51-system.20100908
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../:/lib/:/usr/lib/:/usr/lib/x86_64-linux-gnu/
COLLECT_GCC_OPTIONS='-v' '-std=gnu99' '-o' '6200ch' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/collect2 --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu -dynamic-linker /lib64/ld-linux-x86-64.so.2 -o 6200ch -z relro /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.4.5/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../.. -L/usr/lib/x86_64-linux-gnu /tmp/ccYZeB3s.o -lavc1394 -lrom1394 -lraw1394 -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.4.5/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crtn.o[/HTML]

What am I doing wrong?  Can I get a pre-compiled version from somewhere?

Cheers.

---

