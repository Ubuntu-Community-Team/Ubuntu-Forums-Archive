---
title: "Catalyst x86_64 driver for Radeon 4850 install failing"
date: 2011-05-02
forum: Multimedia Software
---

### Post by adder_smr on 2011-05-02
I realize that Canonical is not responsible for the Catalyst driver, but I can't seem to operate outside of the Ubuntu Classic (no effects) mode for 64 bit Natty, and I was curius if anyone else had encountered or resolved this.

 When I upgraded from 10.10 (I was using the fglrx package), xorg would immediately crash. I was able to reach the gdm screen only using recovery mode. I uninstalled the fglrx package, and now I can boot into Ubuntu Classic (no effects) mode only (no other desktop will work) using the open-source driver at no greater than 1280x1024.

 When I try to re-install the catalyst driver using aptitude or Administration->Additional Drivers, the installation fails:

[I](jockey.log: WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx)
[/I]

Similarly, package generation from the AMD page fails:
[I]Installation complete.
*** glibc detected *** ./setup.data/bin/x86_64/setup: double free or corruption (fasttop): 0x000000000259f630 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a8f)[0x7f8dca984a8f]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x73)[0x7f8dca9888e3]
./setup.data/bin/x86_64/setup[0x40a6b5]
./setup.data/bin/x86_64/setup[0x4128fb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xff)[0x7f8dca92aeff]
[/I]


 Is this a known issue? Has anyone else encountered this?

---

### Post by hansioux on 2011-05-03
hi, same problem here with Radeon HD 4670

Fresh install of Natty.  I tried to build a ubuntu package, and gets the same error

```
Installation complete.
*** glibc detected *** ./setup.data/bin/x86_64/setup: double free or corruption (fasttop): 0x00000000023c7690 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a8f)[0x7f1fc8785a8f]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x73)[0x7f1fc87898e3]
./setup.data/bin/x86_64/setup[0x40a6b5]
./setup.data/bin/x86_64/setup[0x4128fb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xff)[0x7f1fc872beff]
./setup.data/bin/x86_64/setup[0x40382a]
======= Memory map: ========
....

```Despite the "Installation complete message, the temp folder is deleted with no deb.  

I tried installing, but besides installing the ati control front-end, i don't think the driver works either.

---

### Post by Yellow Pasque on 2011-05-03
I can't reproduce the same issue. Make sure you have all of the prerequisite packages suggested here: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

### Post by adder_smr on 2011-05-03
Ok, I'll run through that page tonight. Thanks for the link.

---

### Post by adder_smr on 2011-05-04
Ok, so the results last night were that I was successfully able to remove my radeon driver, build the Catalyst driver, install it, and gnerate an xorg.conf file. But Xorg still didn't launch properly, with or without the xorg.conf file, with one monitor or two. I didn't know where to get good log info why that was the case, but when I just doing something like "startx" from the command line (after cntrl+alt+f1 to get to another session), I see that fglrx gets a segmentation fault.
 So again, I can only get a gnome session in failsafe graphics mode after choosing the recovery mode option in grub.

 Any more ideas on information to gather or things to try?

---

### Post by adder_smr on 2011-05-05
Turns out I was missing the DKMS error message that was popping up when installing the .deb files. Using the "option 1" install, it never even gets past the error above. There must be something about either the 64 bit driver or my build config that is breaking this. The 32-bit live CD works fine, so I may just have to uninstall and go to 32 bit.

---

