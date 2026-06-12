---
title: "No Sound: Following Comp. Sound Problem Solutions Guide with this error"
date: 2011-02-05
forum: Multimedia Software
---

### Post by rosatimr on 2011-02-05
I went through and followed the Comprehensive Sound Problem Solutions Guide and could not get modules to load.  Here is a couple outputs with my final error at the end.

```
michael@michael-desktop:~$ aplay -l
aplay: device_list:235: no soundcards found...
michael@michael-desktop:~$ 

```
```
michael@michael-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at e0200000 (32-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 2410 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e0326100 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
    Subsystem: Intel Corporation Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at e0300000 (32-bit, non-prefetchable) [size=128K]
    Memory at e0324000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 20e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 20c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 20a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at e0325c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Intel Corporation Device 2504
    Flags: fast devsel, IRQ 22
    Memory at e0320000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f8000000-f81fffff
    Prefetchable memory behind bridge: 00000000f8200000-00000000f83fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: e0100000-e01fffff
    Prefetchable memory behind bridge: 00000000f8400000-00000000f85fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f8600000-f87fffff
    Prefetchable memory behind bridge: 00000000f8800000-00000000f89fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f8a00000-f8bfffff
    Prefetchable memory behind bridge: 00000000f8c00000-00000000f8dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: f8e00000-f8ffffff
    Prefetchable memory behind bridge: 00000000f9000000-00000000f91fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 2080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 2060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 2040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at e0325800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
    Memory behind bridge: e0000000-e00fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
    I/O ports at 2408 [size=8]
    I/O ports at 241c [size=4]
    I/O ports at 2400 [size=8]
    I/O ports at 2418 [size=4]
    I/O ports at 2020 [size=32]
    Memory at e0325000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Intel Corporation Device 514d
    Flags: medium devsel, IRQ 10
    Memory at e0326000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 2000 [size=32]
    Kernel modules: i2c-i801

02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 1018 [size=8]
    I/O ports at 1024 [size=4]
    I/O ports at 1010 [size=8]
    I/O ports at 1020 [size=4]
    I/O ports at 1000 [size=16]
    Memory at e0100000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: pata_marvell
    Kernel modules: pata_marvell

06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Linksys Device 0013
    Flags: bus master, fast devsel, latency 32, IRQ 21
    Memory at e0004000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
    Subsystem: Intel Corporation Device 514d
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at e0006000 (32-bit, non-prefetchable) [size=2K]
    Memory at e0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

michael@michael-desktop:~$ 
```Then I started the ALSA Driver Compilation Section on the Solutions Guide.  Here is the log from the module assistant

I didn't know how to copy all of the code, so here is the end of it with the error:
```

In file included from include/linux/pci.h:58,                               
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,   
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:      
 &#9474; /usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error:        
 &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory   
 &#9474; compilation terminated.                                                     
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1        
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                   
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'       
 &#9474; make[2]: *** [compile] Error 2                                              
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make[1]: *** [build-stamp] Error 2                                          
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make: *** [kdist_image] Error 2                                             
 &#9474;                                                                             
 &#9474;                                   <Ok>   
```
Thanks in advance for any help!

---

### Post by Jose Catre-Vandis on 2011-02-05
Sounds like its a mess (excuse the pun!)

You can recover alsa with this command:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

---

### Post by rosatimr on 2011-02-05
Thanks for that.  Now do I just start over?

---

### Post by rosatimr on 2011-02-05
I get this when I try to reload alsa

```
michael@michael-desktop:~$ sudo alsa force-reload
[sudo] password for michael: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-hda-intel snd-hda-codec snd-seq snd-hwdep snd-pcm snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-hda-intel snd-hda-codec snd-seq snd-hwdep snd-pcm snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
```

---

### Post by Jose Catre-Vandis on 2011-02-06
Try running the command again and ensure you reboot. I had messed up so much similarly, I had to give it three goes before it worked again!

Also just check you have an etc/modprobe.d/alsa-base.conf file in place

Here is the contents of the installed file if its missing

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by rosatimr on 2011-02-06
Just ran this again with this result

```
michael@michael-desktop:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for michael:
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-25-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-25-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.35-25-generic
  linux-sound-base
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/35.9MB of archives. After unpacking 0B will be used.
Preconfiguring packages ...             
(Reading database ... 145412 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-25-generic 2.6.35-25.44 (using .../linux-image-2.6.35-25-generic_2.6.35-25.44_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Preparing to replace alsa-base 1.0.23+dfsg-1ubuntu4 (using .../alsa-base_1.0.23+dfsg-1ubuntu4_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.23-2ubuntu3.4 (using .../alsa-utils_1.0.23-2ubuntu3.4_amd64.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.23-1ubuntu2.1 (using .../libasound2_1.0.23-1ubuntu2.1_amd64.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.23+dfsg-1ubuntu4 (using .../linux-sound-base_1.0.23+dfsg-1ubuntu4_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.35-25.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.35-25.44 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Setting up libasound2 (1.0.23-1ubuntu2.1) ...
Setting up linux-sound-base (1.0.23+dfsg-1ubuntu4) ...
Setting up alsa-base (1.0.23+dfsg-1ubuntu4) ...
Setting up alsa-utils (1.0.23-2ubuntu3.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                        
michael@michael-desktop:~$ 
```I rebooted.  I made sure the /etc/modprobe.d/alsa-base.comf file was present and exactly as posted.  Just for giggles I tried the reload command again and got the same output.

```
michael@michael-desktop:~$ aplay -l
aplay: device_list:235: no soundcards found...
michael@michael-desktop:~$ sudo alsa force-reload[sudo] password for michael: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-hda-intel snd-seq snd-hda-codec snd-hwdep snd-pcm snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-hda-intel snd-seq snd-hda-codec snd-hwdep snd-pcm snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
```I have been searching for a fix for this for days and cant get anywhere.  Some where along the way I read to run this command (I didn't know if this helps any)

```
michael@michael-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
michael@michael-desktop:~$ 

```It may be worth mentioning that I am having trouble getting my sound to work in Windows as well.  This is my desktop and I dual boot Ubuntu 10.10 and Windows XP.  I have installed the drivers for the sound in XP and installs with errors and wont work. 

What should I do?

---

### Post by rosatimr on 2011-02-06
I figured out the reload command issue.  Along the line I created a file that didn't belong. Its gone and here is the new output

```
michael@michael-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

---

### Post by rosatimr on 2011-02-07
Any other suggestions, before I just put a new sound card in?  I hate giving up.

---

### Post by Jose Catre-Vandis on 2011-02-07
> **rosatimr said:**
> I figured out the reload command issue.  Along the line I created a file that didn't belong. Its gone and here is the new output

```
michael@michael-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

So do you get anything with aplay -l after this? Sound modules apprear to be loading OK.

However as you also appear to be having hardware problems (or you have just been unlucky with Windows and Ubuntu!) try a different sound card....

---

### Post by rosatimr on 2011-02-07
```
michael@michael-desktop:~$ sudo alsa force-reload
[sudo] password for michael: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
michael@michael-desktop:~$ aplay -l
aplay: device_list:235: no soundcards found...
michael@michael-desktop:~$ 

```

I guess I will try a different card.  I think I have an old one lying around.

---

### Post by rosatimr on 2011-02-09
Just wanted to put some closure to this thread.  Since I couldn't get my onboard sound to work in Ubuntu or Windows (even with the proper drivers in Windows), I chalked it up to a hardware malfunction.  I installed an old sound card that I had lying around and have no issues.  My sound is working in both OS's.  Thanks Jose for your effort.

---

### Post by Jose Catre-Vandis on 2011-02-09
:)

---

