---
title: "kernel 2.6.33 and bradcom wireless"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by ESKIMOn00b on 2010-04-12
first post at these forums so take it easy on my guys :-)

i installed the 2.6.33 mainline kernel on karmic desktop and karmic UNR both on my lenovo s10

i just bought a new SSD, i like it, im trying to LOVE it, but i need a tad bit of help

in preperation of getting the SSD i istalled the 2.6.33 kernel to my karmic desktop install (on my s10's original hard drive) and couldnt for the life of me get the restricted drivers to work for 2.6.33 kernel, if i booted into the original kernel it works fine but 2.6.33 no dice, so i thought maybe they needed to be compiled specifically for the kernel 

soooooo


i got my SSD installed UNR karmic on it and then the kernel before i enabled the drivers still no dice, so then  found a .deb for a newer broadcom driver revision and installed it, still no wireless


at this point im stuck with running TRIM scripts and wireless, or auto trim and no wifi

any ideas

update:
nm-tool, gives only my wired adapter

---

### Post by ESKIMOn00b on 2010-04-13
bump

any one else running 2.6.33 for native trim using broadcom wireless card?

---

### Post by barisurum on 2010-04-13
Make sure headers for your kernel is installed and do:

```
cd /usr/src/linux-headers-2.6.33-YOURKERNELNUMBER-generic/include/
sudo cp generated/* linux/
```

And try reinstalling bcmwl-kernel-source and modaliases packages

Worked for me.. Hope it works for you too :)

---

### Post by ESKIMOn00b on 2010-04-13
got an error in synaptic reinstalling those packages, here is the make.log file referenced in the output.....

maybe i have wrong/bad version of this kernel(2.6.33-20633-generic), is there a particular one i should use?
followed these instructions for updating the kernel 
[http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/)

DKMS make.log for bcmwl-5.10.91.9+bdcom for kernel 2.6.33-020633-generic (i686)
Tue Apr 13 14:41:04 CDT 2010
make: Entering directory `/usr/src/linux-headers-2.6.33-020633-generic'
  LD      /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_free&#8217;:
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c:702: error: implicit declaration of function &#8216;schedule&#8217;
make[1]: *** [/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.33-020633-generic'

---

### Post by ESKIMOn00b on 2010-04-13
and now wireless is broken on the kernel it was previously working on, hardware drivers show its activated

---

### Post by ESKIMOn00b on 2010-04-13
no other ideas? or any idea on how to put it back the way it was?
now i stuck completly without wireless internet

---

### Post by ESKIMOn00b on 2010-04-13
id hate to have to reinstall unr all over when i know theres an easy fix for this problem, at this point im ok with geting my wlan adapter back in the standard karmic kernel

---

### Post by barisurum on 2010-04-14
If you want to revert the changes remove the 2.6.33 kernel pieces including headers and try reinstalling bcmwl packages booting to the previous kernel.. For some reason the drivers don't build on the kernel sources but dunno why, it worked for me and I have the same kernel but I'm on lucid though..

---

### Post by zoomy942 on 2010-05-21
> **barisurum said:**
> If you want to revert the changes remove the 2.6.33 kernel pieces including headers and try reinstalling bcmwl packages booting to the previous kernel.. For some reason the drivers don't build on the kernel sources but dunno why, it worked for me and I have the same kernel but I'm on lucid though..


I have a thread i started kind of about this too.  mine still doesnt work.

[http://ubuntuforums.org/showthread.php?t=1488795]("http://ubuntuforums.org/showthread.php?t=1488795")

---

### Post by TheGnomeOfMetal on 2010-05-21
try enabling the STA driver in Hardware drivers

---

### Post by zoomy942 on 2010-05-21
> **TheGnomeOfMetal said:**
> try enabling the STA driver in Hardware drivers

i did.  it always fails out with an error code of 1.

---

### Post by fredbird67 on 2010-05-21
I don't know if this will work for you or not, but I'm running PC/OS (based on Ubuntu, BTW), which properly detected the Broadcom wireless card in our 5-year-old Dell Inspiron 6000 laptop, and I was able to get connected wirelessly with no configuration necessary.  However, I just checked Synaptic, and the latest kernel that PC/OS has in the repos I have enabled is only 2.6.31 -- hopefully it'll still automatically connect wirelessly when the next version of PC/OS comes out.  Also, PC/OS uses Xfce for its default desktop (which I personally prefer) but there is a GNOME version, too.

If you'd like to give it a whirl, their website is [http://www.pc-os.org](http://www.pc-os.org)

Just my $.02 worth,
Fred in St. Louis

---

