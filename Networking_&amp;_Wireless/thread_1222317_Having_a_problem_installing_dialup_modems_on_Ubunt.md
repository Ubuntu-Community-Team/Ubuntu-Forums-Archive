---
title: "Having a problem installing dialup modems on Ubuntu Hardy..."
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by Zaiken on 2009-07-24
Im new to Ubuntu and i cant figure out what to do about my modems, they wont install no matter what i try. I read the forum posts and got one working on Xubuntu, but the Ubuntu computer i need them on wont work with either. this is the output of my attempt to install the pctel(the other one I wont even get into right now)
```
checking for running kernel version...2.6.24
checking for ptserial...ptserial-2.6.c
checking for gcc...4.2.4
checking for kernel gcc version...4.2.4
searching for kernel includes...found at /lib/modules/2.6.24-24-generic/build/include
checking for autoconf.h.../lib/modules/2.6.24-24-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in utsrelease.h...t.c:1:19: error: stdio.h: No such file or directory
t.c: In function ‘main’:
t.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
./configure: line 477: ./t: No such file or directory
rm: cannot remove `./t': No such file or directory
** error
could not determine a proper UTS_RELEASE
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

```my lspci

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:09.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:0a.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6105M [Rhine-III] (rev 96)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

``` it worked fine on Xubuntu hardy, so i dont see what the problem is on Ubuntu.

---

### Post by Zaiken on 2009-07-27
Nervermind, I figured it out. Turns out I needed some dev packages, unfortunately I downloaded them in the process of installing something else, otherwise I would list them for anyone else with this problem.

---

