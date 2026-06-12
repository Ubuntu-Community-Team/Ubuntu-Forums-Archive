---
title: "Xgl [beryl] segfaults on me MAJORLY!!! PLEASE HELP"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2007-02-02
Here is all the info that I was able to gather
#0 0xb7a0401e in xglxDPMSSet () from /usr/lib/xorg/modules/xgl/libxglx.so 
(gdb) bt full 
#0 0xb7a0401e in xglxDPMSSet () from /usr/lib/xorg/modules/xgl/libxglx.so 
No symbol table info available. 
#1 0x0810881e in XFixesCursorInit () 
No symbol table info available. 
#2 0x08091567 in ProcGrabPointer () 
No symbol table info available. 
#3 0x08096500 in DeactivatePointerGrab () 
No symbol table info available. 
#4 0x08090fec in ProcUngrabPointer () 
No symbol table info available. 
#5 0x08089b9f in Dispatch () 
No symbol table info available. 
#6 0x0809ab59 in main () 
No symbol table info available.

It doesn't have a trigger.. I'm SURE... it just happens randomly.. Doesn't matter what app I have running it just happens all the while and it's VERY VERY ANNOYING
I'd apprecaite if someone could really try and help me out here

I'm using an ATI card x1400 256 mb on Inspiron 9400 running Beryl 0.2.0

---

### Post by MoLE on 2007-02-13
Please post xorg.cong as an attachment so we can have a look at it.  Does glxgears run?
```
mole@ubuntu:~$ glxgears -printfps
```

---

