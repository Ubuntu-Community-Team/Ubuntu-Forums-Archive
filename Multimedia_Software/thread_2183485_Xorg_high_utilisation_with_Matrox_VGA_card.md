---
title: "Xorg high utilisation with Matrox VGA card"
date: 2013-10-25
forum: Multimedia Software
---

### Post by liviusbr on 2013-10-25
Hi all,

I've noticed that my fresh installed server Dell goes totally crazy on CPU utilisation on Xorg process. (>80%) without any application running on display.
My video card has the following details :

[TABLE="class: node-unclaimed, width: 100%"]
[TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]VGA compatible controller[/TD]
[/TR]
                 [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]MGA G200eW WPCM450[/TD]
[/TR]
                 [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Matrox Electronics Systems Ltd.[/TD]
[/TR]
[/TABLE]


I am running Ubuntu 12.04.


Any idea on how can I tackle this ?


Thanks!

---

### Post by ibjsb4 on 2013-10-25
I have found Matrox to be linux friendly and work fine with the default drivers supplied by ubuntu software center.  There is a optional matrox package that I do not use, but may be usable by you.

 [http://manpages.ubuntu.com/manpages/precise/man1/matroxset.1.html](http://manpages.ubuntu.com/manpages/precise/man1/matroxset.1.html)

I don't think it will help your problem though.

I wonder if its compiz causing your high load.

Open a terminal and enter:

```
top
```

You are running a desktop, right?

Give you any clues?

---

### Post by mullot01 on 2014-06-06
Hi,
I have a similar problem after installed  ubuntu 14.04 with the same video card.
Display is very slow and high cpu uilisation for xorg :

[FONT=courier new]/usr/lib/nux/unity_support_test -p  
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.3[/FONT]

[FONT=courier new]Not software rendered:      no 
Not blacklisted:            yes 
GLX fbconfig:               yes 
GLX texture from pixmap:    yes 
GL npot or rect textures:   yes 
GL vertex program:          yes 
GL fragment program:        yes 
GL vertex buffer object:    yes 
GL framebuffer object:      yes 
GL version is 1.4+:         yes 

Unity 3D supported:         no 

dmesg | pastebinit
[http://paste.ubuntu.com/7601247/](http://paste.ubuntu.com/7601247/)

lspci -nnk | grep -iA3 vga 
06:03.0 VGA compatible controller [0300]: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 [102b:0532] (rev 0a)
    Subsystem: Dell Device [1028:02a6]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c50] (rev 04)
    Subsystem: Intel Corporation Device [8086:8086]
[/FONT]
I have no problem with my old ubuntu 10.04.

---

