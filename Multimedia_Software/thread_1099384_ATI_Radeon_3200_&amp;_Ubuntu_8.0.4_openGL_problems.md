---
title: "ATI Radeon 3200 &amp; Ubuntu 8.0.4 openGL problems"
date: 2009-03-18
forum: Multimedia Software
---

### Post by DroKZ on 2009-03-18
Hello All,

Last weekend i had a major crash so i had to reinstall my whole computer.
My hardware:
Fujitsu siemens amilo
videocard: ATI Radeon 3200 (64mb)

Ubuntu 8.0.4

I also updated ubuntu to 8.10 but after that nothing worked anymore (no video, no network)

Yesterday my fgl_glxgears did give my some correct output.
The only problem is that some games give me Segmentation faults.
So i tried running fglrxinfo and here is the output:
 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7659 Release

Segmentation fault

Also glxinfo told me that direct rendering was good.

I thought that maybe downloading latest drivers from ATI should solve this problem.
The ouput after installing latest drivers, removing them and get the latest from envy (8-6 drivers) is this:
glxinfo
name of display: :0.0

fgl_glxgears 
Using GLX_SGIX_pbuffer (and doesn't even start anymore)

fglrxinfo gives no output.

Any idea what i do wrong and how i could solve this problem?
Maybe good to know that everything worked before the crash.

Thanks in advance

---

### Post by DroKZ on 2009-03-19
Problem is solved:

$ sudo apt-get update
- worked fine
$ sudo apt-get install linux-restricted-modules-generic restricted-manager
- didn't worked because there where problems with restricted-manager
$ sudo apt-get install xorg-driver-fglrx
- worked
$ sudo depmod -a 
- forgot this one :)

After this i also have done this: 
aticonfig --initial -f

reboot

Don't know which of those 2 things solved the problem but it works again
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

