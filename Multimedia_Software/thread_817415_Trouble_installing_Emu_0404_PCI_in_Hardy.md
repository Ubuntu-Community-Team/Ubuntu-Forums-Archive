---
title: "Trouble installing Emu 0404 PCI in Hardy"
date: 2008-06-03
forum: Multimedia Software
---

### Post by lil0tik on 2008-06-03
Hey All -

I've been having a terrible time trying to getmy Emu 0404 to work on a fresh install of Xubuntu 8.04.  I know a lot has already been written on this in the forums, and I've been scouring the 'nets looking for answers...  Please help.

Ok, I've installed the alsa 1.0.16 drivers, libs, firmware, and utils from source, as instructed at [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga) and installed firmware (before utils).  No major errors were thrown in the process; at least it appeared to complete w/o a problem.

No luck.  Doesn't even recognize the card,  Am I missing something?

Output of cat /proc/asound/cards

> lil0tik@xxx:~$ cat /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 0 with AD1888 at 0xfeb00000, irq 19


Output of lspci -nn

> lil0tik@xxx:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:13.2 USB Controller [0c03]: ATI Technologies Inc EHCI USB Controller [1002:4345] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 17)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Unknown device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
01:07.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)
 

Output of dmesg | grep emu

> lil0tik@xxx:~$ dmesg | grep emu
[   19.071821] input: Macintosh mouse button emulation as /devices/virtual/input
/input0
[   42.910457] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Speci
al config.
[   42.910550] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_H
ANA_ID=0x7f
[   42.910556] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filen
ame emu/emu0404.fw testing
[   46.374715] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:684: firmware size=
0xd67c
[   51.780488] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:893: emu1010: Loadi
ng Hana Firmware file failed, reg=0x7f
[  974.388998] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Speci
al config.
[  974.389101] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_H
ANA_ID=0x7f
[  974.389107] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filen
ame emu/emu0404.fw testing
[  974.397680] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:684: firmware size=
0xd67c
[  979.863087] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/buil
d/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:893: emu1010: Loadi
ng Hana Firmware file failed, reg=0x7f


Any help?

---

### Post by zajaro on 2009-02-24
so far as I know there is two different version of the emu 0404 pci, you can tell one from the other by running lspci -nn. the model that works is the one that has identifier [1102:0008]. the other ( the [1102:0004]) is  not working right now.
maybe there's a problem with the firmware or something,... I don't know exactly,... there's another thread in this forum where you can read the whole issue.
best regards.
almost forgot,.. you seem to own the 0004 version the one that doesn't work yet.
just like me;).

---

