---
title: "Latest ati driver, Bad ALLOC error"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by flapane on 2006-06-05
[   47.566965] [fglrx] Maximum main memory to use for locked dma buffers: 921 MBytes.
[   47.567065] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[   47.586633] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[   49.228703] [fglrx] total      GART = 67108864
[   49.228708] [fglrx] free       GART = 51118080
[   49.228710] [fglrx] max single GART = 51118080
[   49.228712] [fglrx] total      LFB  = 126808064
[   49.228714] [fglrx] free       LFB  = 116322304
[   49.228716] [fglrx] max single LFB  = 116322304
[   49.228718] [fglrx] total      Inv  = 134217728
[   49.228719] [fglrx] free       Inv  = 134217728
[   49.228721] [fglrx] max single Inv  = 134217728
[   49.228722] [fglrx] total      TIM  = 0
[   49.665146] NET: Registered protocol family 10
[   49.665226] lo: Disabled Privacy Extensions
[   49.665325] IPv6 over IPv4 tunneling driver
[   56.316179] eth0: no IPv6 routers present
flapane@a64:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
flapane@a64:~$ glxgears
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  21
  Current serial number in output stream:  23
flapane@a64:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  21
  Current serial number in output stream:  22
flapane@a64:~$

---

### Post by PsycoEwok on 2006-06-07
I'm also getting these same exact errors whenever I try to run glxinfo and glxgears. Can someone please provide some insight?

---

### Post by flapane on 2006-06-07
i only needed to reinstall the driver using "generate specific packages for distribution"

---

### Post by syounkim on 2006-10-13
I have the same problem. Any suggestions?

---

### Post by Kropotkin on 2006-11-07
I'm seeing it here too with Intel 915 graphics. X has been up for several days, then all of a sudden displayed this message when I tried to run vlc.

---

