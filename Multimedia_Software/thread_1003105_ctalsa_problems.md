---
title: "ctalsa problems"
date: 2008-12-05
forum: Multimedia Software
---

### Post by dido__15 on 2008-12-05
Good Evening,

I've reached a bit of a brick wall with the installation of drivers for my X-Fi. I know these are problematic, but i followed amtam's guide to the letter (it's by far the best how-to i've read lately,) and the drivers have installed fine, so (apparently) has the ctalsa module. I'm running Ubuntu Studio 64-bit and the card is an X-Fi Fatal1ty Xtreme Gamer.

lspci -v gives the following output (relevant to the X-Fi)

```
06:01.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 002c
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at ec00 [size=32]
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel modules: ctalsa

```

I may be wrong but this suggests to me that the ctalsa module is installed. It also shows drivers available for ctalsa in the restricted driver manager. However, upon clicking activate in the driver manager nothing at all happens, it prompts for password and then just stays deactivated. I then moved on to trying to insert the module.

modprobe ctalsa gives the following:

```
dido@dido-pc:~$ sudo modprobe ctalsa
WARNING: Error inserting emupia (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and strangely enough when trying to start ctsound it gives exactly the same output

```
dido@dido-pc:~$ sudo /etc/init.d/ctsound start
Starting ctsound: Loading X-Fi Drv - Please Wait...WARNING: Error inserting emupia (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.27-10-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

If anyone could shed any light on what any of this means or how to solve the problem it would be greatly appreciated.

Many Thanks in advance,

Dido.

---

### Post by dido__15 on 2008-12-06
Ok so by removing ctalsa from the blacklist (please try not to laugh) it is now only the ctalsa module causing problems and not the other dependent modules. As such I am now even more confused. dmesg is also giving me a far more detailed output for the problem:

```
[   60.418217] ctalsa: no symbol version for bytes_to_order
[   60.418227] ctalsa: Unknown symbol bytes_to_order
[   60.418587] ctalsa: no symbol version for get_ossrv
[   60.418588] ctalsa: Unknown symbol get_ossrv
[   60.419153] ctalsa: no symbol version for heap_alloc
[   60.419154] ctalsa: Unknown symbol heap_alloc
[   60.419344] ctalsa: no symbol version for ioctl_dispatch
[   60.419345] ctalsa: Unknown symbol ioctl_dispatch
[   60.419394] ctalsa: no symbol version for heap_free
[   60.419395] ctalsa: Unknown symbol heap_free
[   76.941904] ctalsa: no symbol version for bytes_to_order
[   76.941911] ctalsa: Unknown symbol bytes_to_order
[   76.942270] ctalsa: no symbol version for get_ossrv
[   76.942271] ctalsa: Unknown symbol get_ossrv
[   76.942821] ctalsa: no symbol version for heap_alloc
[   76.942822] ctalsa: Unknown symbol heap_alloc
[   76.943007] ctalsa: no symbol version for ioctl_dispatch
[   76.943008] ctalsa: Unknown symbol ioctl_dispatch
[   76.943056] ctalsa: no symbol version for heap_free
[   76.943057] ctalsa: Unknown symbol heap_free

```

Any ideas? I'm beginning to pull my hair out.

Dido.



EDIT:: that dmesg output shows the error caused by two consecutive modprobe ctalsa commands

---

