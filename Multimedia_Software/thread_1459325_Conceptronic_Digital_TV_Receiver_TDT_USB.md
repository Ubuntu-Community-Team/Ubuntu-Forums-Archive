---
title: "Conceptronic Digital TV Receiver TDT USB"
date: 2010-04-21
forum: Multimedia Software
---

### Post by Dark_Jack on 2010-04-21
Hello everyone!

> make[3]: *** [/tmp/v4l-dvb-39c2d2041e6e/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/tmp/v4l-dvb-39c2d2041e6e/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/tmp/v4l-dvb-39c2d2041e6e/v4l'
make: *** [all] Error 2
antonio@antonio-desktop:/tmp/v4l-dvb-39c2d2041e6e$     make install
make -C /tmp/v4l-dvb-39c2d2041e6e/v4l install
make[1]: se ingresa al directorio `/tmp/v4l-dvb-39c2d2041e6e/v4l'
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
strip: supported targets: elf64-x86-64 elf32-i386 a.out-i386-linux pei-i386 pei-x86-64 elf64-l1om elf64-little elf64-big elf32-little elf32-big plugin srec symbolsrec verilog tekhex binary ihex
make[1]: *** [media-install] Error 1
make[1]: se sale del directorio `/tmp/v4l-dvb-39c2d2041e6e/v4l'
make: *** [install] Error 2
antonio@antonio-desktop:/tmp/v4l-dvb-39c2d2041e6e$ 


Can anyone help me please?
[IMG]http://www.google.es/images/cleardot.gif[/IMG]

---

### Post by Dark_Jack on 2010-04-21
anyone? :(

---

### Post by Dark_Jack on 2010-04-22
```
/home/antonio/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/antonio/v4l-dvb/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/antonio/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/antonio/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/antonio/v4l-dvb/v4l'
make: *** [all] Error 2
antonio@antonio-desktop:~/v4l-dvb$ sudo make install
make -C /home/antonio/v4l-dvb/v4l install
make[1]: se ingresa al directorio `/home/antonio/v4l-dvb/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.32-21-generic/kernel/drivers/media/video: -e 
Removing obsolete files from /lib/modules/2.6.32-21-generic/kernel/drivers/media/dvb/cinergyT2:
 -e 
Removing obsolete files from /lib/modules/2.6.32-21-generic/kernel/drivers/media/common:
ir-common.ko 
-e 
Removing obsolete files from /lib/modules/2.6.32-21-generic/kernel/drivers/media/dvb/frontends:
 Installing kernel modules under /lib/modules/2.6.32-21-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.32-21-generic 
make -C firmware install
make[2]: Entering directory `/home/antonio/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/antonio/v4l-dvb/v4l/firmware'
make[1]: se sale del directorio `/home/antonio/v4l-dvb/v4l'
antonio@antonio-desktop:~/v4l-dvb$


```

Please, I need help!! :(

---

### Post by xc3RnbFO8P on 2010-04-23
Read this:
[http://ubuntuforums.org/showthread.php?t=1305228]("http://ubuntuforums.org/showthread.php?t=1305228")

---

### Post by Dark_Jack on 2010-04-24
Ok, thank you!

I'm trying install :P

---

### Post by Dark_Jack on 2010-04-25
does not work, can someone help me? :(

I bought a **Conceptronic USB DVB-T Digital TV Receiver** but I can not get to work on my **Ubuntu 9.10 [COLOR=Red]64 bits[/COLOR]**

Apparently, my ubuntu is detected:

```
antonio@antonio-desktop:~$ dmesg | grep -i dvb
[   11.738849] usbcore: registered new interface driver dvb_usb_af9015
``````
antonio@antonio-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 1b80:d393 Afatech** 
Bus 001 Device 002: ID 0951:1624 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
antonio@antonio-desktop:~$ dmesg|tail
[   13.592518] hda-intel: Codec #3 probe error; disabling it...
[   13.746597] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   13.746879] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   14.254537] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   14.254540] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   14.254960] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.540788] usplash:381 freeing invalid memtype ffffffffcf000000-ffffffffcfe00000
[   24.590007] eth0: no IPv6 routers present
[   62.010018] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   62.171204] usb 1-2: configuration #1 chosen from 1 choice
```I have installed the "**linux-firmware-nonfree**" and "**dvb-usb-af9015.fw**"

[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/")

The TDT is **Conceptronic** brand and product code is **CTVDIGRCU**

**Errores:**
 [URL="http://img408.imageshack.us/img408/6602/pantallazojy.png"]
[/URL]
[http://img408.imageshack.us/img408/6602/pantallazojy.png](http://img408.imageshack.us/img408/6602/pantallazojy.png)
 [http://img408.imageshack.us/img408/7796/pantallazo4ud.png](http://img408.imageshack.us/img408/7796/pantallazo4ud.png)

**PD:** Obviously, the device is connected even though the pictures say otherwise ...

```
antonio@antonio-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetadp              6528  0 
vboxnetflt             14288  0 
vboxdrv              1778380  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   277860  1 
dvb_usb_af9015         32964  0 
dvb_usb                19276  1 dvb_usb_af9015
dvb_core              104528  1 dvb_usb
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     11908  0 
iptable_filter          3872  0 
parport                40528  2 ppdev,lp
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
nvidia              10316904  36 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usb_storage            66304  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
e1000e                138544  0 
intel_agp              33040  0 
antonio@antonio-desktop:~$
```Anybody can help me, please? :(

---

