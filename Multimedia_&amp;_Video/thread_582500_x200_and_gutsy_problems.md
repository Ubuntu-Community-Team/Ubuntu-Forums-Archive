---
title: "x200 and gutsy problems"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by meatwad64 on 2007-10-19
I was finally able to get all my hardware to work with gutsy. The only problem is after i installed the restricted drivers after a certain period of usage X will freeze up and I have to manually power off my laptop and restart. Anyone have any ideas what I could do to fix this problem?

---

### Post by donthem on 2007-10-20
this is the xpress 200 radeon chipset your talking about?  if so i got mine to work in gusty without a problem.  could you post your lspci?

---

### Post by meatwad64 on 2007-10-20
do you mean just lspci -v?

Yes it is an xpress 200 chipset on my laptop.

---

### Post by CRuno91 on 2007-10-20
when i tried to use 7.04 i had problems with my sound, wireless, and ati x200 video chipset, when i would enable effects it would turn the screen an extremely bright white-orange so i couldn't see anything.  I'm scared to go and install gutsy now because of this.

I'm using a Gateway MT3707 which is basically the same as the more popular MT3705 if that helps anyone.

---

### Post by meatwad64 on 2007-10-21
Yes i have a mt3705. Finally wireless and sound works but it freezes up like crazy for some reason.

---

### Post by Sharpiedeluxe on 2007-10-21
I have the MT3705, with Gutsy installed. I haven't experienced any of these problems thus far. The only problem I get is that nautilus crashes every once in awhile.

---

### Post by diskotek on 2007-10-21
i have also same problem with ati x200... i still couldn2t solve it. 
which driver i have to use?? when i change the resolution from the display center, nothing changes... help!

and i also have that bright orange screen :(

---

### Post by Ehtetur on 2007-10-21
Do you have compiz-fusion working with the ATI Radeon X200? If so, did you go w/ xorg-driver-fglrx or the ati-radeon driver?
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

I had compiz-fusion and beryl working in feisty.. Completed a clean install of gutsy and just finished tweaking xorg.conf to get my monitor working properly.

Not caring too much a/b proprietary vs. open-source with the ATI video drivers, just which one works best. :|

---

### Post by diskotek on 2007-10-22
```
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7ceb92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c94050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:47 279204     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:47 279204     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c5b000-b7c65000 r-xp 00000000 03:41 260622     /lib/libgcc_s.so.1
b7c65000-b7c66000 rw-p 0000a000 03:41 260622     /lib/libgcc_s.so.1
b7c70000-b7c71000 rw-p b7c70000 00:00 0 
b7c71000-b7c73000 r-xp 00000000 03:41 260761     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c73000-b7c75000 rw-p 00001000 03:41 260761     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c75000-b7c76000 rw-p b7c75000 00:00 0 
b7c76000-b7c7a000 r-xp 00000000 03:47 4972552    /usr/lib/libXdmcp.so.6.0.0
b7c7a000-b7c7b000 rw-p 00003000 03:47 4972552    /usr/lib/libXdmcp.so.6.0.0
b7c7b000-b7c7d000 r-xp 00000000 03:47 4971084    /usr/lib/libXau.so.6.0.0
b7c7d000-b7c7e000 rw-p 00001000 03:47 4971084    /usr/lib/libXau.so.6.0.0
b7c7e000-b7dc2000 r-xp 00000000 03:41 260758     /lib/tls/i686/cmov/libc-2.6.1.so
b7dc2000-b7dc3000 r--p 00143000 03:41 260758     /lib/tls/i686/cmov/libc-2.6.1.so
b7dc3000-b7dc5000 rw-p 00144000 03:41 260758     /lib/tls/i686/cmov/libc-2.6.1.so
b7dc5000-b7dc8000 rw-p b7dc5000 00:00 0 
b7dc8000-b7deb000 r-xp 00000000 03:41 260762     /lib/tls/i686/cmov/libm-2.6.1.so
b7deb000-b7ded000 rw-p 00023000 03:41 260762     /lib/tls/i686/cmov/libm-2.6.1.so
b7ded000-b7eda000 r-xp 00000000 03:47 4972554    /usr/lib/libX11.so.6.2.0
b7eda000-b7ede000 rw-p 000ed000 03:47 4972554    /usr/lib/libX11.so.6.2.0
b7ede000-b7eeb000 r-xp 00000000 03:47 4972556    /usr/lib/libXext.so.6.4.0
b7eeb000-b7eec000 rw-p 0000d000 03:47 4972556    /usr/lib/libXext.so.6.4.0
b7eec000-b7eed000 rw-p b7eec000 00:00 0 
b7eed000-b7ef4000 r-xp 00000000 03:47 4972571    /usr/lib/libXrender.so.1.3.0
b7ef4000-b7ef5000 rw-p 00006000 03:47 4972571    /usr/lib/libXrender.so.1.3.0
b7ef5000-b7efa000 r-xp 00000000 03:47 4972619    /usr/lib/libXrandr.so.2.1.0
b7efa000-b7efb000 rw-p 00005000 03:47 4972619    /usr/lib/libXrandr.so.2.1.0
b7f04000-b7f07000 rw-p b7f04000 00:00 0 
b7f07000-b7f21000 r-xp 00000000 03:41 260623     /lib/ld-2.6.1.so
b7f21000-b7f23000 rw-p 00019000 03:41 260623     /lib/ld-2.6.1.so
bf880000-bf896000 rw-p bf880000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

i have this out while trying to make "sudo at&#305;config --initial"
i'm stuck

---

### Post by Sharpiedeluxe on 2007-11-12
Yeah, I have the same model of computer...using feisty kernel with gutsy, but still experiencing the same problems you guys are having. Any help would be wonderful :(

---

### Post by PreviousN on 2007-12-14
Try this:

"sudo apt-get install envy" in a terminal. 
Then, when its done, type "sudo envy" into a terminal. 

Then, choose "install ati driver" 
Follow the instructions. Tell it to overwrite your xorg. This installs open source ati drivers, NOT the fgrlx drivers. It works WONDERS for me. Slightly less performance but no clipping/ghosting or other problems.

---

### Post by diskotek on 2008-02-05
gutsy is working flawless with ati x200 after i install envy (nice and easy)!!!

---

