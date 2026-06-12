---
title: "No Sound after update kernal followed Comprehensive Sound Problem Solutions Guide"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by MasterColdSoul on 2007-02-17
I followed the guide and get to:

ALSA driver Compilation

I get this error

 tty_struct’ has no member named ‘atomic_write’ 
&#9474; /usr/src/modules/alsa-driver/drivers/serialmidi.c:322: error: ‘struct  
&#9474; tty_struct’ has no member named ‘atomic_write’  
&#9474; /usr/src/modules/alsa-driver/drivers/serialmidi.c:339: error: ‘struct  
&#9474; tty_struct’ has no member named ‘atomic_write’ 
&#9474; make[6]: *** [/usr/src/modules/alsa-driver/drivers/serialmidi.o] Error 1 
&#9474; make[5]: *** [/usr/src/modules/alsa-driver/drivers] Error 2
&#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2 
&#9474; make[3]: *** [modules] Error 2 
&#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic' 
&#9474; make[2]: *** [compile] Error 2 
&#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'  
&#9474; make[1]: *** [build-stamp] Error 2      
&#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'              
&#9474; make: *** [kdist_image] Error 2   

anyone know how to fix the tty_struct’ has no member named ‘atomic_write’ ?

Thanks.

---

### Post by MasterColdSoul on 2007-02-18
Any ideas?

---

### Post by soan on 2007-02-20
Hey I got the same problem. Can someone help?

---

### Post by soan on 2007-02-20
Indeed I found a solution:

You need to edit the file and change lines:

suggested fix, change 'atomic_write' -> 'atomic_write_lock' in lines
317, 322, 339

---

