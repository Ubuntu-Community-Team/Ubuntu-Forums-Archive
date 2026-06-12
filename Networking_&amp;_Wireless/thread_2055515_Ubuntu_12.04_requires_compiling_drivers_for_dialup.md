---
title: "Ubuntu 12.04 requires compiling drivers for dialup modem?"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by dotish on 2012-09-09
It seems Ubuntu 12.04 LTS (precise pangolin) lacks dialup modem support. I am desperate trying and trying with two possible modems internal PCI and/or USB: no way!!
- lspci sees my internal PCI modem
- scanModem sees the PCI modem too but hsfmodem drivers required and no precompiled binaries for kernel 3.2.0_23_generic_pae_ubuntu_i386 in linuxant.com
- wvdial doesn't see any modem, asks to use setserial to assign port but I can't find its tty
- gnome-ppp doesn't find any modem

I guess modem drivers have to be compiled and installed, hence I downloaded hsfmodem-7.68.00.12full.tar.gz, expanded and ran: sudo make install but it seems headers are missing and kernel tree is not properly set.

I have an intel machine, with internet access under win2000 only (dialup).
I would appreciate help on the subject:
1) is it necessary to compile and install drivers for hsfmodem?
2) do I have to find and download a generic kernel source?

I've bought this brand new Ubuntu 12.04 LTS CD from canonical store but What a let down!! Network Manager doesn't allow dialup modem!
I wouldn't be attempting to switch to Linux if I could afford ADSL!!!

Any help very welcome. Regards.

---

### Post by dotish on 2012-09-22
As I've found out YES, it does!! The way I've managed to get my internal PCI Conexant softmodem recognized and able to connect is by following, step by step, the instructions given by Ganton in this thread [http://ubuntuforums.org/showthread.php?t=1903439](http://ubuntuforums.org/showthread.php?t=1903439) 
I have to sort out the auto-disconnects after a while though...

---

