---
title: "Kernel problem installing DVB-T"
date: 2008-09-30
forum: Multimedia Software
---

### Post by oli_ on 2008-09-30
Hi,
before this (Ubuntu+Gnome) i had Kubuntu running with which this worked just fine.
I have the Terratec Cinergy T USB XXS DVB-T stick which worked perfectly with this installation guide: [http://users.piuha.net/martti/comp/ubuntu/en/terratecxxs.html](http://users.piuha.net/martti/comp/ubuntu/en/terratecxxs.html)

now i have a fresh ubuntu system and when it comes to:
Building and installing the driver » make
it returns:
```
oli@Oli:~/v4l-dvb$ make
make -C /home/oli/v4l-dvb/v4l 
make[1]: Betrete Verzeichnis '/home/oli/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.24
You appear to have loadable modules turned off in your kernel.  You can
not compile the v4l-dvb drivers, as modules, and use them with a kernel
that has modules disabled.

If you want to compile these drivers into your kernel, you should
use 'make kernel-links' to link the source for these drivers into
your kernel tree.  Then configure and compile the kernel.
make[1]: Verlasse Verzeichnis '/home/oli/v4l-dvb/v4l'
make[1]: Betrete Verzeichnis '/home/oli/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.24
You appear to have loadable modules turned off in your kernel.  You can
not compile the v4l-dvb drivers, as modules, and use them with a kernel
that has modules disabled.

If you want to compile these drivers into your kernel, you should
use 'make kernel-links' to link the source for these drivers into
your kernel tree.  Then configure and compile the kernel.
make[1]: *** Keine Regel vorhanden, um das Target ».myconfig«, 
  benötigt von »config-compat.h«, zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/home/oli/v4l-dvb/v4l'
make: *** [all] Fehler 2
```

i tried 'make kernel-links' as suggested which worked fine at first but then failed at sudo make install:
```
oli@Oli:~/v4l-dvb$ make kernel-links
make -C /home/oli/v4l-dvb/v4l kernel-links
make[1]: Betrete Verzeichnis '/home/oli/v4l-dvb/v4l'
cd ..;	v4l/scripts/makelinks.sh /home/oli
patching /home/oli...
mkdir: created directory `/home/oli/drivers'
mkdir: created directory `/home/oli/drivers/media'
mkdir: created directory `/home/oli/drivers/media/radio'
mkdir: created directory `/home/oli/drivers/media/video'
mkdir: created directory `/home/oli/drivers/media/video/et61x251'
mkdir: created directory `/home/oli/drivers/media/video/au0828'
mkdir: created directory `/home/oli/drivers/media/video/sn9c102'
mkdir: created directory `/home/oli/drivers/media/video/ivtv'
mkdir: created directory `/home/oli/drivers/media/video/saa7134'
mkdir: created directory `/home/oli/drivers/media/video/gspca'
mkdir: created directory `/home/oli/drivers/media/video/cx88'
mkdir: created directory `/home/oli/drivers/media/video/zc0301'
mkdir: created directory `/home/oli/drivers/media/video/pwc'
mkdir: created directory `/home/oli/drivers/media/video/pvrusb2'
mkdir: created directory `/home/oli/drivers/media/video/bt8xx'
mkdir: created directory `/home/oli/drivers/media/video/usbvision'
mkdir: created directory `/home/oli/drivers/media/video/cx23885'
mkdir: created directory `/home/oli/drivers/media/video/cpia2'
mkdir: created directory `/home/oli/drivers/media/video/cx25840'
mkdir: created directory `/home/oli/drivers/media/video/cx18'
mkdir: created directory `/home/oli/drivers/media/video/em28xx'
mkdir: created directory `/home/oli/drivers/media/video/uvc'
mkdir: created directory `/home/oli/drivers/media/video/usbvideo'
mkdir: created directory `/home/oli/drivers/media/video/ovcamchip'
mkdir: created directory `/home/oli/drivers/media/common'
mkdir: created directory `/home/oli/drivers/media/common/tuners'
mkdir: created directory `/home/oli/drivers/media/dvb'
mkdir: created directory `/home/oli/drivers/media/dvb/frontends'
mkdir: created directory `/home/oli/drivers/media/dvb/ttpci'
mkdir: created directory `/home/oli/drivers/media/dvb/siano'
mkdir: created directory `/home/oli/drivers/media/dvb/b2c2'
mkdir: created directory `/home/oli/drivers/media/dvb/dvb-usb'
mkdir: created directory `/home/oli/drivers/media/dvb/bt8xx'
mkdir: created directory `/home/oli/drivers/media/dvb/ttusb-dec'
mkdir: created directory `/home/oli/drivers/media/dvb/dvb-core'
mkdir: created directory `/home/oli/drivers/media/dvb/cinergyT2'
mkdir: created directory `/home/oli/drivers/media/dvb/dm1105'
mkdir: created directory `/home/oli/drivers/media/dvb/ttusb-budget'
mkdir: created directory `/home/oli/drivers/media/dvb/pluto2'
mkdir: created directory `/home/oli/include'
mkdir: created directory `/home/oli/include/media'
mkdir: created directory `/home/oli/include/asm-arm'
mkdir: created directory `/home/oli/include/asm-arm/arch-pxa'
mkdir: created directory `/home/oli/include/linux'
mkdir: created directory `/home/oli/include/linux/dvb'
mkdir: created directory `/home/oli/include/sound'
mkdir: created directory `/home/oli/Documentation'
mkdir: created directory `/home/oli/Documentation/video4linux'
mkdir: created directory `/home/oli/Documentation/video4linux/cx88'
mkdir: created directory `/home/oli/Documentation/video4linux/bttv'
mkdir: created directory `/home/oli/Documentation/video4linux/cx2341x'
mkdir: created directory `/home/oli/Documentation/dvb'
make[1]: Verlasse Verzeichnis '/home/oli/v4l-dvb/v4l'
oli@Oli:~/v4l-dvb$ sudo make install
make -C /home/oli/v4l-dvb/v4l install
make[1]: Betrete Verzeichnis '/home/oli/v4l-dvb/v4l'
Stripping debug info from files
Usage: strip <option(s)> in-file(s)
 Removes symbols and sections from files
 The options are:
  -I --input-target=<bfdname>      Assume input file is in format <bfdname>
  -O --output-target=<bfdname>     Create an output file in format <bfdname>
  -F --target=<bfdname>            Set both input and output format to <bfdname>
  -p --preserve-dates              Copy modified/access timestamps to the output
  -R --remove-section=<name>       Remove section <name> from the output
  -s --strip-all                   Remove all symbol and relocation information
  -g -S -d --strip-debug           Remove all debugging symbols & sections
     --strip-unneeded              Remove all symbols not needed by relocations
     --only-keep-debug             Strip everything but the debug information
  -N --strip-symbol=<name>         Do not copy symbol <name>
  -K --keep-symbol=<name>          Do not strip symbol <name>
     --keep-file-symbols           Do not strip file symbol(s)
  -w --wildcard                    Permit wildcard in symbol comparison
  -x --discard-all                 Remove all non-global symbols
  -X --discard-locals              Remove any compiler-generated symbols
  -v --verbose                     List all object files modified
  -V --version                     Display this program's version number
  -h --help                        Display this output
     --info                        List object formats & architectures supported
  -o <file>                        Place stripped output into <file>
strip: supported targets: elf64-x86-64 elf32-i386 a.out-i386-linux efi-app-ia32 efi-app-x86_64 elf64-little elf64-big elf32-little elf32-big srec symbolsrec tekhex binary ihex
make[1]: *** [media-install] Fehler 1
make[1]: Verlasse Verzeichnis '/home/oli/v4l-dvb/v4l'
make: *** [install] Fehler 2
```

how can i convince my kernel to load modules? :x

---

