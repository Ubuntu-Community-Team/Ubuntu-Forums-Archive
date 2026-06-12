---
title: "installing Alsa hda-intel driver ....permission denied"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by Zecking on 2007-09-01
hello Ubuntu community,
i just installed feisty 2 days ago... new to Linux, but i LOVE it... y didn't i join earlier, i don't know... 
im very stubborn and like to learn on my own, but im stumped... sound issue delaying all other things i can lean about Ubuntu. so i come to u elite for your help.

i decided to make a clean install of alsa driver 1.0.14 but when i start installing the first file "./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install" on the tutorial from [URL="http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel"]
it begins installing...but at the end part of the install it starts saying "....permission denied"
like so

rm: cannot remove `/usr/include/sound/uda1341.h': Permission denied
rm: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
rm: cannot remove `/usr/include/sound/version.h': Permission denied
rm: cannot remove `/usr/include/sound/hwdep.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied


does that mean that the install wasn't successful?
i first thought that maybe by adding sudo to the begining of my commad line it might fix it...but same permission denial happans


btw... here is my lspci -v

zecking@Satellite-T2300:/$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 8c000000-8c0fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 8c000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 90000000-93fff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        16-bit legacy interface ports at 0001

0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0007000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0007800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 2000 [size=64]
        Capabilities: <access denied>


dont know what

---

### Post by taurus on 2007-09-01
```
**sudo** make install
```

---

### Post by Zecking on 2007-09-01
nope ...still permission denied...
here is the command line: (btw...how do i post this into its own little box like i c other ppl doing...it says code: then a box with the command lines)

zecking@Satellite-T2300:~/downloads/alsa-driver-1.0.14$ sudo make install ./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install
Password:
make: unrecognized option `--with-cards=hda-intel'
make: unrecognized option `--with-sequencer=yes'
Usage: make [options] [target] ...
Options:
  -b, -m                      Ignored for compatibility.
  -B, --always-make           Unconditionally make all targets.
  -C DIRECTORY, --directory=DIRECTORY
                              Change to DIRECTORY before doing anything.
  -d                          Print lots of debugging information.
  --debug[=FLAGS]             Print various types of debugging information.
  -e, --environment-overrides
                              Environment variables override makefiles.
  -f FILE, --file=FILE, --makefile=FILE
                              Read FILE as a makefile.
  -h, --help                  Print this message and exit.
  -i, --ignore-errors         Ignore errors from commands.
  -I DIRECTORY, --include-dir=DIRECTORY
                              Search DIRECTORY for included makefiles.
  -j [N], --jobs[=N]          Allow N jobs at once; infinite jobs with no arg.
  -k, --keep-going            Keep going when some targets can't be made.
  -l [N], --load-average[=N], --max-load[=N]
                              Don't start multiple jobs unless load is below N.
  -L, --check-symlink-times   Use the latest mtime between symlinks and target.
  -n, --just-print, --dry-run, --recon
                              Don't actually run any commands; just print them.
  -o FILE, --old-file=FILE, --assume-old=FILE
                              Consider FILE to be very old and don't remake it.
  -p, --print-data-base       Print make's internal database.
  -q, --question              Run no commands; exit status says if up to date.
  -r, --no-builtin-rules      Disable the built-in implicit rules.
  -R, --no-builtin-variables  Disable the built-in variable settings.
  -s, --silent, --quiet       Don't echo commands.
  -S, --no-keep-going, --stop
                              Turns off -k.
  -t, --touch                 Touch targets instead of remaking them.
  -v, --version               Print the version number of make and exit.
  -w, --print-directory       Print the current directory.
  --no-print-directory        Turn off -w, even if it was turned on implicitly.
  -W FILE, --what-if=FILE, --new-file=FILE, --assume-new=FILE
                              Consider FILE to be infinitely new.
  --warn-undefined-variables  Warn when an undefined variable is referenced.

This program built for i486-pc-linux-gnu
Report bugs to <bug-make@gnu.org>
make dep
make[1]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/acore'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/ioctl32'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/ioctl32'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/oss'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/oss'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/seq'
make[4]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/seq/instr'
make[4]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/seq/instr'
make[4]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/seq/oss'
make[4]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/seq/oss'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/acore/seq'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/acore'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/i2c'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/i2c/other'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/i2c/other'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/i2c'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/mpu401'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/mpu401'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/opl3'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/opl3'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/opl4'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/opl4'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/pcsp'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/pcsp'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/vx'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers/vx'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/drivers'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/ad1816a'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/ad1816a'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/ad1848'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/ad1848'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/cs423x'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/cs423x'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/es1688'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/es1688'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/gus'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/gus'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/msnd'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/msnd'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/opti9xx'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/opti9xx'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/sb'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/sb'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/wavefront'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa/wavefront'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/isa'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/synth'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/synth/emux'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/synth/emux'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/synth'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ac97'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ac97'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ali5451'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ali5451'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/asihpi'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/asihpi'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/au88x0'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/au88x0'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ca0106'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ca0106'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/cs46xx'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/cs46xx'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/echoaudio'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/echoaudio'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/emu10k1'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/emu10k1'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/hda'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/hda'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ice1712'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ice1712'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/korg1212'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/korg1212'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/mixart'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/mixart'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/nm256'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/nm256'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/pcxhr'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/pcxhr'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/pdplus'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/pdplus'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/riptide'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/riptide'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/rme9652'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/rme9652'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/trident'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/trident'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/vx222'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/vx222'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ymfpci'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci/ymfpci'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pci'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/codecs'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/codecs'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/core'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/core'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/fabrics'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/fabrics'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/soundbus'
make[4]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa/soundbus'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/aoa'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/soc'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/at91'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/at91'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/codecs'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/codecs'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/pxa'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/pxa'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/sh'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/soc/sh'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/soc'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/usb'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/usb/caiaq'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/usb/caiaq'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/usb/usx2y'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/usb/usx2y'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/usb'
make[2]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pcmcia'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/zecking/downloads/alsa-driver-1.0.14/pcmcia/vx'
make[3]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pcmcia/vx'
make[2]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14/pcmcia'
make[1]: Leaving directory `/home/zecking/downloads/alsa-driver-1.0.14'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/zecking/downloads/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 12 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
utils/link-modules /home/zecking/downloads/alsa-driver-1.0.14

ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/zecking/downloads/alsa-driver-1.0.14/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
rm: cannot remove `/usr/include/sound/uda1341.h': Permission denied
rm: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
rm: cannot remove `/usr/include/sound/version.h': Permission denied
rm: cannot remove `/usr/include/sound/hwdep.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4xxx-adda.h': Permission denied
rm: cannot remove `/usr/include/sound/es1688.h': Permission denied
rm: cannot remove `/usr/include/sound/timer.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm_params.h': Permission denied
rm: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000.h': Permission denied
rm: cannot remove `/usr/include/sound/opl3.h': Permission denied
rm: cannot remove `/usr/include/sound/tlv.h': Permission denied
rm: cannot remove `/usr/include/sound/emux_synth.h': Permission denied
rm: cannot remove `/usr/include/sound/sb.h': Permission denied
rm: cannot remove `/usr/include/sound/hdspm.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4114.h': Permission denied
rm: cannot remove `/usr/include/sound/i2c.h': Permission denied
rm: cannot remove `/usr/include/sound/opl4.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm-indirect.h': Permission denied
rm: cannot remove `/usr/include/sound/cs4231.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_midi_event.h': Permission denied
rm: cannot remove `/usr/include/sound/vx_core.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
rm: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/minors.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_virmidi.h': Permission denied
rm: cannot remove `/usr/include/sound/core.h': Permission denied
rm: cannot remove `/usr/include/sound/rawmidi.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4117.h': Permission denied
rm: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
rm: cannot remove `/usr/include/sound/gus.h': Permission denied
rm: cannot remove `/usr/include/sound/wavefront_fx.h': Permission denied
rm: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
rm: cannot remove `/usr/include/sound/mpu401.h': Permission denied
rm: cannot remove `/usr/include/sound/asequencer.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_instr.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_gf1.h': Permission denied
rm: cannot remove `/usr/include/sound/wavefront.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1_synth.h': Permission denied
rm: cannot remove `/usr/include/sound/pt2258.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
rm: cannot remove `/usr/include/sound/asoundef.h': Permission denied
rm: cannot remove `/usr/include/sound/mixer_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/trident.h': Permission denied
rm: cannot remove `/usr/include/sound/soundfont.h': Permission denied
rm: cannot remove `/usr/include/sound/cs8427.h': Permission denied
rm: cannot remove `/usr/include/sound/hdsp.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_simple.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_oss_legacy.h': Permission denied
rm: cannot remove `/usr/include/sound/snd_wavefront.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4531_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/memalloc.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
rm: cannot remove `/usr/include/sound/info.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_kernel.h': Permission denied
rm: cannot remove `/usr/include/sound/driver.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1848.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/control.h': Permission denied
rm: cannot remove `/usr/include/sound/asound.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_midi_emul.h': Permission denied
rm: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_device.h': Permission denied
rm: cannot remove `/usr/include/sound/soc.h': Permission denied
rm: cannot remove `/usr/include/sound/emux_legacy.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_iw.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm.h': Permission denied
rm: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
rm: cannot remove `/usr/include/sound/initval.h': Permission denied
rm: cannot remove `/usr/include/sound/util_mem.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/soc-dapm.h': Permission denied
rm: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/cs8403.h': Permission denied
install: cannot change owner and/or group of `/usr/include/sound': Operation not permitted
install: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
install: cannot remove `/usr/include/sound/ad1848.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_fm.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_gf1.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_iw.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_simple.h': Permission denied
install: cannot remove `/usr/include/sound/ak4114.h': Permission denied
install: cannot remove `/usr/include/sound/ak4117.h': Permission denied
install: cannot remove `/usr/include/sound/ak4531_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ak4xxx-adda.h': Permission denied
install: cannot remove `/usr/include/sound/asequencer.h': Permission denied
install: cannot remove `/usr/include/sound/asound.h': Permission denied
install: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
install: cannot remove `/usr/include/sound/asoundef.h': Permission denied
install: cannot remove `/usr/include/sound/control.h': Permission denied
install: cannot remove `/usr/include/sound/core.h': Permission denied
install: cannot remove `/usr/include/sound/cs4231.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
install: cannot remove `/usr/include/sound/cs8403.h': Permission denied
install: cannot remove `/usr/include/sound/cs8427.h': Permission denied
install: cannot remove `/usr/include/sound/driver.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1_synth.h': Permission denied
install: cannot remove `/usr/include/sound/emu8000.h': Permission denied
install: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied
install: cannot remove `/usr/include/sound/emux_legacy.h': Permission denied
install: cannot remove `/usr/include/sound/emux_synth.h': Permission denied
install: cannot remove `/usr/include/sound/es1688.h': Permission denied
install: cannot remove `/usr/include/sound/gus.h': Permission denied
install: cannot remove `/usr/include/sound/hdsp.h': Permission denied
install: cannot remove `/usr/include/sound/hdspm.h': Permission denied
install: cannot remove `/usr/include/sound/hwdep.h': Permission denied
install: cannot remove `/usr/include/sound/i2c.h': Permission denied
install: cannot remove `/usr/include/sound/info.h': Permission denied
install: cannot remove `/usr/include/sound/initval.h': Permission denied
install: cannot remove `/usr/include/sound/memalloc.h': Permission denied
install: cannot remove `/usr/include/sound/minors.h': Permission denied
install: cannot remove `/usr/include/sound/mixer_oss.h': Permission denied
install: cannot remove `/usr/include/sound/mpu401.h': Permission denied
install: cannot remove `/usr/include/sound/opl3.h': Permission denied
install: cannot remove `/usr/include/sound/opl4.h': Permission denied
install: cannot remove `/usr/include/sound/pcm-indirect.h': Permission denied
install: cannot remove `/usr/include/sound/pcm.h': Permission denied
install: cannot remove `/usr/include/sound/pcm_oss.h': Permission denied
install: cannot remove `/usr/include/sound/pcm_params.h': Permission denied
install: cannot remove `/usr/include/sound/pt2258.h': Permission denied
install: cannot remove `/usr/include/sound/rawmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sb.h': Permission denied
install: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
install: cannot remove `/usr/include/sound/seq_device.h': Permission denied
install: cannot remove `/usr/include/sound/seq_instr.h': Permission denied
install: cannot remove `/usr/include/sound/seq_kernel.h': Permission denied
install: cannot remove `/usr/include/sound/seq_midi_emul.h': Permission denied
install: cannot remove `/usr/include/sound/seq_midi_event.h': Permission denied
install: cannot remove `/usr/include/sound/seq_oss.h': Permission denied
install: cannot remove `/usr/include/sound/seq_oss_legacy.h': Permission denied
install: cannot remove `/usr/include/sound/seq_virmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
install: cannot remove `/usr/include/sound/snd_wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/soc-dapm.h': Permission denied
install: cannot remove `/usr/include/sound/soc.h': Permission denied
install: cannot remove `/usr/include/sound/soundfont.h': Permission denied
install: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
install: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
install: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
install: cannot remove `/usr/include/sound/timer.h': Permission denied
install: cannot remove `/usr/include/sound/tlv.h': Permission denied
install: cannot remove `/usr/include/sound/trident.h': Permission denied
install: cannot remove `/usr/include/sound/uda1341.h': Permission denied
install: cannot remove `/usr/include/sound/util_mem.h': Permission denied
install: cannot remove `/usr/include/sound/version.h': Permission denied
install: cannot remove `/usr/include/sound/vx_core.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront_fx.h': Permission denied
install: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1

---

### Post by taurus on 2007-09-01
```
./configure --with-cards=hda-intel --with-sequencer=yes
make 
sudo make install
```

---

### Post by Zecking on 2007-09-01
wow... ty dude... now i know when i c a    ;   i'll know to do a seperate command... ty

---

### Post by Zecking on 2007-09-01
ok.. i did the first 2 steps ... i extracted and installed the alsa-driver package and the alsa-lib package but on the 2nd command of the 3rd package i need to install... i get some more errors...
1st command in package
zecking@Satellite-T2300:~$ cd /home/zecking/downloads/alsa-utils-1.0.14
zecking@Satellite-T2300:~/downloads/alsa-utils-1.0.14$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands

2nd command package
zecking@Satellite-T2300:~/downloads/alsa-utils-1.0.14$ make
Making all in include
make[1]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
make  all-am
make[2]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
make[2]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
make[1]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
Making all in alsactl
make[1]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
        then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
        then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/alsaconf'
Making all in po
make[2]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/alsaconf'
make: *** [all-recursive] Error 1
zecking@Satellite-T2300:~/downloads/alsa-utils-1.0.14$ 
 

3rd command has errors aswell

is there another way to install the alsa driver or do i have to keep slamming my head on this way til i get it right?

---

### Post by Zecking on 2007-09-01
this is the make install command... errors


zecking@Satellite-T2300:~/downloads/alsa-utils-1.0.14$ make install
Making install in include
make[1]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
make[2]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
make[1]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/include'
Making install in alsactl
make[1]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/alsactl'
make[2]: Entering directory `/home/zecking/downloads/alsa-utils-1.0.14/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
/usr/bin/install: cannot remove `/usr/sbin/alsactl': Permission denied
make[2]: *** [install-sbinPROGRAMS] Error 1
make[2]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/alsactl'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/zecking/downloads/alsa-utils-1.0.14/alsactl'
make: *** [install-recursive] Error 1

---

### Post by taurus on 2007-09-01
Have you looked at my Post #4?  

Didn't you want to include other options during the ./configure and PLEASE use sudo when you want to install it, **sudo** make install?  However, if there is an error message either in ./configure or make (in this case it's make), then no need to go further because it will not work.  You need to fix the problem first before you can process to the next step.

---

### Post by Zecking on 2007-09-02
yes i am doing sudo to make install ... but i cant get past make without any errors... i am following this guild: [http://alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://alsa-project.org/main/index.php/Matrix:Module-hda-intel) 
i did skip this step : cp /downloads/alsa-* .
                Make a directory to store the alsa source code in:

                        cd /usr/src
                        mkdir alsa
                        cd alsa
     ------------>     cp /downloads/alsa-* .
because it doesnt work for me...but i think its not important cos it only wants you to copy something... right?


i get stuck on this part 

Now unzip and install the alsa-driver package: make

       bunzip2 alsa-driver-xxx
       tar -xf alsa-driver-xxx
       cd alsa-driver-xxx
       ./configure --with-cards=hda-intel --with-sequencer=yes
-->    make 
       sudo make install



it shows errors like i said b4...
i reinstalled Feisty and same problem... in uninstalled ubuntu and installed freespire...but same problem and i like ubuntu more...so i came home

i also tryed this guild: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
i did this step on this guild: Getting the ALSA drivers from a *fresh* kernel
but like he warned it might erase my desktop-ubuntu file... i clean reinstalled ubuntu then and went on to his other steps...

on this part: ALSA driver Compilation
 i get to the end of of them steps and at the blue screen where it tells you what % its done it stops and tells me there are errors and cant finish... i checked its commands and it gets errors on the make part... just like i was getting when i was doing the install manually.

has anyone ran into this problem? what do i do.. if i must i will use ubuntu with out sound... thats how much i like it...but comeon theres gotta be someone with a fix.... 

ty

---

