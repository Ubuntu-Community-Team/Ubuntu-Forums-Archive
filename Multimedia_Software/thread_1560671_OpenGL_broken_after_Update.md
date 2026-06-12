---
title: "OpenGL broken after Update"
date: 2010-08-25
forum: Multimedia Software
---

### Post by Nebukadnezar II. on 2010-08-25
Hi all,

After updating my system from 2.6.32-22 to 2.6.32-24 kernel image on Ubuntu Lucid 10.4, my OpenGL broke down, so that every opengl program gives the following error:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
```That is quite a usual problem after updating the kernel, and until today, it always worked for me to reinstall a up-to-date fglrx driver(I'm running an ATI HD 5870 graphics card) from the ATI website. This time, neither installing the driver from ATI nor installing fglrx via apt-get did work. In fact, after installing fglrx, modprobe fglrx still cannot find the module, the system now only runs in low-graphics mode. 
UPDATE: Now, I finally made it to the stage, where normal graphics mode with normal resolution is run, but with super-poor graphics performance. I actually have no idea what I did change, apart from rebooting from a system with gdm switched off.

Now, after some research, I found one interesting thing: in kern.log. During boot, these lines appear:
```
Aug 25 10:10:04 UStudioMachine kernel: [   17.896416] p54pci 0000:06:08.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 25 10:10:04 UStudioMachine kernel: [   17.896458] p54pci 0000:06:08.0: firmware: requesting isl3886pci
Aug 25 10:10:04 UStudioMachine kernel: [   17.928376] hda_codec: ALC889: BIOS auto-probing.
Aug 25 10:10:04 UStudioMachine kernel: [   17.929868] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
Aug 25 10:10:04 UStudioMachine kernel: [   17.938703] Console: switching to colour frame buffer device 80x30
Aug 25 10:10:04 UStudioMachine kernel: [   17.940293] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 25 10:10:04 UStudioMachine kernel: [   17.940339] HDA Intel 0000:01:00.1: setting latency timer to 64
Aug 25 10:10:04 UStudioMachine kernel: [   17.960454] p54pci 0000:06:08.0: Cannot find firmware (isl3886pci)
Aug 25 10:10:04 UStudioMachine kernel: [   17.960579] p54pci 0000:06:08.0: firmware: requesting isl3886
Aug 25 10:10:04 UStudioMachine kernel: [   17.961729] p54pci 0000:06:08.0: PCI INT A disabled
Aug 25 10:10:04 UStudioMachine kernel: [   17.961748] p54pci: probe of 0000:06:08.0 failed with error -2
```This seems to me like a PCI device with a failing firmware or something like this. Could that be my graphics card? 
Anyways, even if this PCI error is not related to my graphics card, does anyone have an idea to solve my problem another way? I already did everything you can find here:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012)
but none of the solutions posted there worked for me.

Any ideas? 
Thanks in advance,

Nebukadnezar II.

---

### Post by Nebukadnezar II. on 2010-08-29
Uhm. It's sort of no good solution, but I got it to work fine after reinstalling the system from scratch. 
So, if anyone ever stumbles upon the same prob, apparently there is no good solution that a normal mortal one can find...

Greetings
Laertes

---

