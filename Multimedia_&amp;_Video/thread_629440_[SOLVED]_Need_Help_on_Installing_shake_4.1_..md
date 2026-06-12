---
title: "[SOLVED] Need Help on Installing shake 4.1 ."
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by Madj on 2007-12-02
[B]Hi i start linux 2 days ago so sorry  if i say some stupid things
So i had this problem that look like no one can solve[/B]( :

/usr/apple/shrank/shake4/bin$ tcsh shake
/usr/apple/shrank/shake4/bin/shkx.exe: [COLOR="Red"]error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64
[/COLOR]

[B]This guy Neo amiga on this forum [http://forums.cgsociety.org/showthread.php?t=401062&highlight=etch](http://forums.cgsociety.org/showthread.php?t=401062&highlight=etch) find the begining of the solution i think:
[/B]

**Neo Amiga first say and did  **:


NR_SHAKE_LOCATION = /home/neo/shake
LD_LIBRARYN32_PATH = /usr/lib:/home/neo/shake/lib:/home/neo/shake/lib/mesa
LD_LIBRARY_PATH = /usr/lib:/home/neo/shake/lib:/home/neo/shake/lib/mesa
/home/neo/shake/bin/shkx.exe: error while loading shared libraries: libXext.so.6: cannot open shared object file: No such file or directory
[B]
And  he look in the lib paths above:[/B]

deborah:/home/neo/shake/lib# ls -la | grep libXext
lrwxrwxrwx 1 root root 25 2006-09-03 19:58 libXext.so.6 -> /usr/lib/libXext.so.6.4.0

deborah:/usr/lib# ls -la | grep libXext
lrwxrwxrwx 1 root root 16 2006-09-03 19:49 libXext.so.6 -> libXext.so.6.4.0
-rw-r--r-- 1 neo neo 69992 2006-04-19 13:42 libXext.so.6.4.0

** And then he say and did:**

So the library that it complains about are clearly there. But maybe it has to be linked to some 32bit version of it or something...?
[B]
So he ve done that:[/B]

"What I have done now is that I started my old debian box and copied all the nececary libraries from it and linked them up on the AMD64 box running Debian Etch. It all looked good for a while until I got this when I tried to run it (I have added a "ldd" in the start script):

/home/neo/shake-v4.00.0607/bin/shkx.exe: /home/neo/shake-v4.00.0607/lib/libgcc_s.so.1: version `GCC_3.3' not found (required by /home/neo/shake-v4.00.0607/lib/libstdc++.so.5)
linux-gate.so.1 => (0xffffe000)
libnrui_lx.so => /home/neo/shake-v4.00.0607/lib/libnrui_lx.so (0xf7b86000)
libnrcc_lx.so => /home/neo/shake-v4.00.0607/lib/libnrcc_lx.so (0xf7936000)
libnrau_lx.so => /home/neo/shake-v4.00.0607/lib/libnrau_lx.so (0xf7918000)
libnrfx_lx.so => /home/neo/shake-v4.00.0607/lib/libnrfx_lx.so (0xf7227000)
libnredl_lx.so => /home/neo/shake-v4.00.0607/lib/libnredl_lx.so (0xf721f000)
libnrvh_lx.so => /home/neo/shake-v4.00.0607/lib/libnrvh_lx.so (0xf7212000)
libnrio_lx.so => /home/neo/shake-v4.00.0607/lib/libnrio_lx.so (0xf71ae000)
libnrgl_lx.so => /home/neo/shake-v4.00.0607/lib/libnrgl_lx.so (0xf718a000)
libnrux_lx.so => /home/neo/shake-v4.00.0607/lib/libnrux_lx.so (0xf7130000)
libnrjl_lx.so => /home/neo/shake-v4.00.0607/lib/libnrjl_lx.so (0xf7112000)
libnrtl_lx.so => /home/neo/shake-v4.00.0607/lib/libnrtl_lx.so (0xf70d7000)
libnrzl_lx.so => /home/neo/shake-v4.00.0607/lib/libnrzl_lx.so (0xf70c9000)
libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7039000)
libXext.so.6 => /home/neo/shake-v4.00.0607/lib/libXext.so.6 (0xf702b000)
libX11.so.6 => /home/neo/shake-v4.00.0607/lib/libX11.so.6 (0xf6f60000)
libpthread.so.0 => /lib32/libpthread.so.0 (0xf6f4f000)
libdl.so.2 => /lib32/libdl.so.2 (0xf6f4b000)
libstdc++.so.5 => /home/neo/shake-v4.00.0607/lib/libstdc++.so.5 (0xf6e91000)
libm.so.6 => /lib32/libm.so.6 (0xf6e6d000)
libgcc_s.so.1 => /home/neo/shake-v4.00.0607/lib/libgcc_s.so.1 (0xf6e64000)
libc.so.6 => /lib32/libc.so.6 (0xf6d39000)
libXt.so.6 => /home/neo/shake-v4.00.0607/lib/libXt.so.6 (0xf6cea000)
libXi.so.6 => /home/neo/shake-v4.00.0607/lib/libXi.so.6 (0xf6ce2000)
libz.so.1 => /home/neo/shake-v4.00.0607/lib/libz.so.1 (0xf6cce000)
libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf650a000)
libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6508000)
/lib/ld-linux.so.2 (0xf7f79000)
libSM.so.6 => /home/neo/shake-v4.00.0607/lib/libSM.so.6 (0xf64ff000)
libICE.so.6 => /home/neo/shake-v4.00.0607/lib/libICE.so.6 (0xf64e8000)
/home/neo/shake-v4.00.0607/bin/shkx.exe: /home/neo/shake-v4.00.0607/lib/libgcc_s.so.1: version `GCC_3.3' not found (required by /home/neo/shake-v4.00.0607/lib/libstdc++.so.5)

So all libraries links up just fine now. I also installed gcc3.3 thinking that it woud solve the problem, but it didn't. =( Have I missed something else?

Many many thanks for all help.""
[COLOR="Red"][B]
Can someone translate for us what command  he ve done to arrive to this point,please?[/B][/COLOR]

---

