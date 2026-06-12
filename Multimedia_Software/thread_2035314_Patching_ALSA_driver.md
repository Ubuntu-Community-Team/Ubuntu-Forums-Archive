---
title: "Patching ALSA driver"
date: 2012-07-30
forum: Multimedia Software
---

### Post by antou on 2012-07-30
Hello,

I am trying to find a way to patch ALSA to get an external USB sound card to work. 
There's a file I need to edit : [**usbaudio.c**]("http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/sound/usb/usbaudio.c") , which is said to be located at linux/sound/usb/usbaudio.c.
My problem here is that I don't know where to find this location :confused: ! I looked in the Alsa-driver sources but I could only find usbaudio.h, which is obviously not what I'm looking for.

I guess there's something I missed about ALSA, if someone can point me to the right direction it would be really appreciated :) .

Some more info :
I'm actually trying to activate the optical IN (S/PDIF in) of my USB sound card : Sweex SC016, using a CM6206 chip which was known for having compatibility issues with anything else than Windows. AFAIK, only the S/PDIF out was patched in Alsa.
Also, I posted this message here because Ubuntu has a large community, and my problem is mainly related to ALSA, but I actually intend to use my device on Angstrom running ALSA 10.0.24.2

---

### Post by antou on 2012-07-31
Lil' bump !:biggrin:

---

### Post by antou on 2012-08-02
Last Bump !
I really can't figure out how to get to these files, damn ! :(

---

### Post by brainwash on 2012-08-02
> Renamed usbaudio.c to card.c because this is what it actually does now.

[http://git.alsa-project.org/?p=alsa-kernel.git;a=commit;h=e5779998bf8b70e48a6cc208c8b61b33bd6117ea](http://git.alsa-project.org/?p=alsa-kernel.git;a=commit;h=e5779998bf8b70e48a6cc208c8b61b33bd6117ea)

---

### Post by AnotherMuggle on 2012-08-02
> **brainwash said:**
> [http://git.alsa-project.org/?p=alsa-kernel.git;a=commit;h=e5779998bf8b70e48a6cc208c8b61b33bd6117ea](http://git.alsa-project.org/?p=alsa-kernel.git;a=commit;h=e5779998bf8b70e48a6cc208c8b61b33bd6117ea)

Notice the comment:
"Renamed usbaudio.c to card.c because this is what it actually does now."

---

### Post by antou on 2012-08-03
Hello,
Thanks for the pointers :) . 
I did fiund what I was looking for, but it was actually located in **quirks.c** ; I guess they moved that as well when renaming the file.

I guess now I'll try to update this thread as I'm stepping forward in the resolution of my problem ; you never know, it might help someone else later. :)

So, here's the piece of code that's interesting me :
```
/* quirks.c */
 383 static int snd_usb_cm6206_boot_quirk(struct usb_device *dev)
 384 {
 385         int err, reg;
 386         int val[] = {0x200c, 0x300[COLOR="Red"]5[/COLOR], 0xf800, 0x143f, 0x0000, 0x3000};
 387 
 388         for (reg = 0; reg < ARRAY_SIZE(val); reg++) {
 389                 err = snd_usb_cm106_write_int_reg(dev, reg, val[reg]);
 390                 if (err < 0)
 391                         return err;
 392         }
 393 
 394         return err;
 395 }
```
According to the CM6206 datasheet, I just have to modify the value of register 1 to 0x3005 (in the file, it's originally 0x3000) to enable S/PDIF loopback and S/PDIF IN Mix.
So basically I have to re-compile ALSA and it should boot the device the way I want it to.

What I did so far :
[LIST]
[*]I got the source of the **kernel** I'm using in my Angstrom ([linux-2.6.32.59]("http://www.kernel.org/pub/linux/kernel/v2.6/longterm/v2.6.32/linux-2.6.32.59.tar.bz2")) ;
[*]**Compiled it** using the following steps : make config (I let everything default there) ; make dep ; make clean ; make bzImage ;
[*]**Configured ALSA** using : ./configure --with-cards=usb-audio --with-sequencer=yes --with-card-options=all --with-kernel=../linux-2.6.32.59
[*]I'm currently **trying to make ALSA** but encounter errors.
[/LIST]
Here's the end of the output :
```

make[1]: Entering directory `/home/root/linux'
  CC [M]  /home/root/alsa-driver-1.0.25/acore/memory_wrapper.o
In file included from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:19:
/home/root/alsa-driver-1.0.25/include/adriver.h:293:1: [COLOR="darkorange"]warning: "GFP_DMA32" redefined[/COLOR]
In file included from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/root/alsa-driver-1.0.25/include/adriver.h:63,
                 from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:19:
include/linux/gfp.h:116:1: [COLOR="DarkOrange"]warning: this is the location of the previous definition[/COLOR]
In file included from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:19:
/home/root/alsa-driver-1.0.25/include/adriver.h:752: [COLOR="Red"]error: static declaration of 'jiffies_to_msecs' follows non-static declaration[/COLOR]
include/linux/jiffies.h:296: [COLOR="red"]error: previous declaration of 'jiffies_to_msecs' was here[/COLOR]
/home/root/alsa-driver-1.0.25/include/adriver.h:771: [COLOR="red"]error: static declaration of 'msecs_to_jiffies' follows non-static declaration[/COLOR]
include/linux/jiffies.h:298: [COLOR="red"]error: previous declaration of 'msecs_to_jiffies' was here[/COLOR]
In file included from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:19:
/home/root/alsa-driver-1.0.25/include/adriver.h:1541:1: [COLOR="darkorange"]warning: "page_to_pfn" redefined[/COLOR]
In file included from /home/root/linux/arch/arm/include/asm/memory.h:310,
                 from /home/root/linux/arch/arm/include/asm/page.h:201,
                 from include/linux/mmzone.h:20,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/root/alsa-driver-1.0.25/include/adriver.h:63,
                 from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:19:
include/asm-generic/memory_model.h:72:1: [COLOR="darkorange"]warning: this is the location of the previous definition[/COLOR]
In file included from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:20:
include/linux/mm.h:273: [COLOR="Red"]error: conflicting types for 'snd_compat_vmalloc_to_page'[/COLOR]
/home/root/alsa-driver-1.0.25/include/adriver.h:673: [COLOR="red"]error: previous declaration of 'snd_compat_vmalloc_to_page' was here[/COLOR]
In file included from /home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:20:
include/linux/mm.h: In function 'lowmem_page_address':
include/linux/mm.h:596: [COLOR="red"]error: implicit declaration of function 'page_to_pfn'[/COLOR]
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c: In function 'snd_compat_vmalloc_to_page':
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:38: [COLOR="red"]error: implicit declaration of function 'VMALLOC_VMADDR'[/COLOR]
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:40: [COLOR="red"]error: 'init_mm' undeclared (first use in this function)[/COLOR]
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:40: [COLOR="red"]error: (Each undeclared identifier is reported only once[/COLOR]
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:40: [COLOR="red"]error: for each function it appears in.)[/COLOR]
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:44: [COLOR="red"]error: implicit declaration of function 'pte_offset'[/COLOR]
/home/root/alsa-driver-1.0.25/acore/memory_wrapper.c:44: [COLOR="DarkOrange"]warning: assignment makes pointer from integer without a cast[/COLOR]
make[3]: *** [/home/root/alsa-driver-1.0.25/acore/memory_wrapper.o] Error 1
make[2]: *** [/home/root/alsa-driver-1.0.25/acore] Error 2
make[1]: *** [_module_/home/root/alsa-driver-1.0.25] Error 2
make[1]: Leaving directory `/home/root/linux'
make: *** [compile] Error 2

```
Someone discussed about the same errors here : [http://forum.nas-central.org/viewtopic.php?f=26&t=2941&start=45](http://forum.nas-central.org/viewtopic.php?f=26&t=2941&start=45) but did not find the solution. I've tried a few #defines and this kind of stuff, but it didn't help.

If anyone is familiar with kernel+ALSA compiling (which is absolutely not my case), I'll be glad to read his ideas :) !

edit: btw, I'm not sure this thread is in the right section. If someone feels like moving it, go ahead ;) .

---

### Post by antou on 2012-08-07
Up, I still can't figure out these errors =/ .

Edit : okay I decided to try and compile Alsa on my main Xubuntu first, to see how the card is detected.
I managed to compile alsa from source using the script found here : [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577).
After the first step (downloading the files with sudo ./Alsa-Upgrade-1.0.25-3.sh -d), I modified /opt/Alsa-1.0.25/alsa-driver-1.0.25/sound/usb/quirks.c as described above.

I'm now going to make a few tests in order to see whether my usb card is working or not. ;)

---

### Post by antou on 2012-08-08
Turns out it works : I can hear th sound from S/PDIF in through the Headphones plug of the USB card. But I can't find a way to bring that audio to the PC, I guess I do need a driver for that.

---

