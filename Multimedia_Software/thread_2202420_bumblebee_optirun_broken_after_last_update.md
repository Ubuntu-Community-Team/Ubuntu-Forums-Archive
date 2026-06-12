---
title: "bumblebee optirun broken after last update"
date: 2014-01-29
forum: Multimedia Software
---

### Post by alexkarnaukhov on 2014-01-29
Hello,

Bumblebee appears to be broken after my last system update.
Trying to run glxgears under optirun gives black window for several seconds, and then glxgear crashes.

Here is strange output:
> 
alexkarnaukhov@alexkarnaukhov-Aspire-3830TG:~$ optirun glxgears 
pci id for fd 6: 8086:0116, driver i965
pci id for fd 8: 8086:0116, driver i965
pci id for fd 16: 8086:0116, driver i965
alexkarnaukhov@alexkarnaukhov-Aspire-3830TG:~$


I`d never got this "pci..." messages before.

Does anyone can help me?

My system is Ubuntu 13.10 x64, Acer Aspire 3830TG with GT540M discrete video.

---

### Post by mehrdad_v on 2014-01-29
Hi,

I have the same problem here:
Neither primusrun nor optirun works after the last update:

```
mehrdad@KubuntuXPS:~$ primusrun glxgears 
pci id for fd 6: 8086:0116, driver i965
pci id for fd 8: 8086:0116, driver i965
pci id for fd 16: 8086:0116, driver i965
Segmentation fault (core dumped)
```

here is backtrace output:

```
mehrdad@KubuntuXPS:~$ optirun gdb -batch -ex r -ex bt glxgears
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
pci id for fd 10: 8086:0116, driver i965
pci id for fd 12: 8086:0116, driver i965
[New Thread 0x7ffff03c6700 (LWP 2932)]
[New Thread 0x7fffefbc5700 (LWP 2933)]
pci id for fd 20: 8086:0116, driver i965

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7ffff03c6700 (LWP 2932)]
0x00007ffff1b96ac5 in ?? () from /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
#0  0x00007ffff1b96ac5 in ?? () from /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
#1  0x00007ffff195e880 in ?? () from /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
#2  0x00007ffff7bbd205 in ?? () from /usr/lib/x86_64-linux-gnu/primus/libGL.so.1
#3  0x00007ffff6f7ff6e in start_thread (arg=0x7ffff03c6700) at pthread_create.c:311
#4  0x00007ffff728f9cd in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:113
```

I would really appreciate your help to resolve this issue.

Thanks,

Mehrdad

---

### Post by alexkarnaukhov on 2014-01-29
Ok, now I dont feeling so lonely)

---

### Post by than2 on 2014-01-29
Same here. 
*optirun glxhead* gives me 
```

ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x15f9720
  Window:      0x2a00002
  Context:     0x1609800
  GL_VERSION:  1.4 (3.0 Mesa 10.1.0-devel)
  GL_VENDOR:   Intel Open Source Technology Center
  GL_RENDERER: Mesa DRI Intel(R) Sandybridge Mobile 

```
and runs ok but with Intel media graphics


*optirun -b primus glxheads *gives me
```

pci id for fd 6: 8086:0116, driver i965
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
pci id for fd 8: 8086:0116, driver i965
Name: :0
  Display:     0x181f100
  Window:      0x2e00002
  Context:     0x1849b30
  GL_VERSION:  4.4.0 NVIDIA 331.38
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce GT 555M/PCIe/SSE2
pci id for fd 16: 8086:0116, driver i965

```
and crashes.

My system:
Lenovo Y570
GeForce GT 555M
Mint 16 x64 (Ubuntu 13.10 x64 gives me the same result)

---

### Post by ArchangeGabriel on 2014-01-31
I suppose all of you have mesa-10.1-devel&#8239;?

If so, you need to add PRIMUS_UPLOAD=1 in front of your command, this is an issue in current mesa-devel.

---

### Post by mehrdad_v on 2014-01-31
> **ArchangeGabriel said:**
> you need to add PRIMUS_UPLOAD=1 in front of your command.

Hey ArchangeGabriel,

Thanks for the solution, it worked for me.

---

### Post by alexkarnaukhov on 2014-02-01
> **ArchangeGabriel said:**
> I suppose all of you have mesa-10.1-devel&#8239;?

If so, you need to add PRIMUS_UPLOAD=1 in front of your command, this is an issue in current mesa-devel.

Thanks very, very much!

---

