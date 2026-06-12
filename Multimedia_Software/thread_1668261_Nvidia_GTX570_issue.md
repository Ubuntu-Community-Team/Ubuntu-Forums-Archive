---
title: "Nvidia GTX570 issue"
date: 2011-01-16
forum: Multimedia Software
---

### Post by creiss on 2011-01-16
Hello all, 

and help pretty please. I am going nuts over this issue. I am running

```

PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff

```

(read: GTX 570 Nvidia) and doing the nvidia prop closed source driver. In contrast to the open source driver solution this one set the screen resolution right. I am even running compiz-fusion with nice effects, but I seem to be lacking total 2d acceleration. A transparent terminal that I move around has some vertical flickering, same goes for video playback (vlc). Overlays, like Sxipper for Firefox does not render the page darker but pitch black. 

I am not sure if this matters, but 
```

root@icarus:~# cat /proc/mtrr 
reg00: base=0x000000000 (    0MB), size= 8192MB, count=1: write-back
reg01: base=0x200000000 ( 8192MB), size= 4096MB, count=1: write-back
reg02: base=0x300000000 (12288MB), size= 1024MB, count=1: write-back
reg03: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg04: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable

```

there are uncacheable items in the mtrr. glxgears run smooth at ~14k fps. There is however, no mentioning of mtrr in the bios, not sure if i can (re-)set it there.

I am chewing on this problem for days now. I even switched from an ATI Card (HD5770) to NVIDIA (GTX 570) in hope of a solution.

I have uploaded all relevant files here: [http://stuff.demonlord.de/ubuntu/ ]("http://stuff.demonlord.de/ubuntu/")


ANY help is oh-so-glady accepted.

Help. Pretty please.

---

### Post by creiss on 2011-01-16
No one, really? Aww.

---

### Post by cchhrriiss121212 on 2011-01-16
Have you tried disabling compiz?

---

### Post by tjones00 on 2011-01-16
A quick google of "ubuntu what is mtrr" produced the following.

[http://ubuntuforums.org/showthread.php?t=115104](http://ubuntuforums.org/showthread.php?t=115104)
[http://hawknotes.blogspot.com/2010/05/ubuntu-1004-fixing-mtrr-errors.html](http://hawknotes.blogspot.com/2010/05/ubuntu-1004-fixing-mtrr-errors.html)

Apparently mtrr has nothing to do with the graphics card but is an error with your BIOS in reporting the proper amount of memory for the system. This is probably why swapping graphics cards didn't fix the issue.

1st) I'd try flashing your bios to a more recent version or just reflashing the same version if it's already the most recent. You don't want to keep using a possibly corrupt bios. Also use an air-dusted to clean the sockets and connections and re-seat the ram. You might also want to run 2 cycles (~2hrs) of memtest 86+ on the ram.

2nd) exchange/RMA the motherboard if you still can and the flash didn't work. It might be a hardware fault and you don't want to keep a borked board.

3rd) If that doesn't work try the persistent kernel mtrr assignment via recovery console ensuring that the mtrr is blank/doesn't exists before you set it. (the first link)

---

