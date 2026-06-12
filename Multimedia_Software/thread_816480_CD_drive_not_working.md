---
title: "CD drive not working"
date: 2008-06-02
forum: Multimedia Software
---

### Post by Just-trevor on 2008-06-02
CDs or DVDs don't show up
sometimes the drive doesn't open back up so i can get the CD back out,
It says there is it failed because there is probably no cd in the drive when I select it in Places
I don't know what the CD drive is and i forget the code to find it...
how do i install it on my computer

I used it to download ubuntu, so it should be functional
thanks in advancef

---

### Post by Prospero2006 on 2008-06-02
Try this:

dmesg | grep cd

That should tell you the device name.

Have you tried
```

sudo eject

```

to force eject?

---

### Post by Just-trevor on 2008-06-03
```
root@Trevor2:/home/trevor-max# dmesg | grep cd
[   24.624934] system 00:02: iomem range 0xcd800-0xcffff has been reserved
[   27.962217] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.465842] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   28.466250] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   28.466277] ohci_hcd 0000:00:02.0: irq 17, io mem 0xea004000
[   28.625242] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   28.625269] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   28.625288] ohci_hcd 0000:00:02.1: irq 18, io mem 0xea005000
[   28.785191] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   28.785224] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   28.785261] ehci_hcd 0000:00:02.2: debug port 1
[   28.785278] ehci_hcd 0000:00:02.2: irq 16, io mem 0xea000000
[   28.796532] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.533902]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   71.983536]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   93.433177]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[  114.882825]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[  160.878868]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  206.802987]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  252.727116]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  298.651248]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  923.064366] usb 3-4: new high speed USB device using ehci_hcd and address 2
[ 3426.902407] usb 3-4: new high speed USB device using ehci_hcd and address 3
[15572.666043] ehci_hcd 0000:00:02.2: remove, state 4
[15572.666281] ehci_hcd 0000:00:02.2: USB bus 3 deregistered
[41370.170982] usb 2-2: new full speed USB device using ohci_hcd and address 2
[88198.094363] usb 2-2: new full speed USB device using ohci_hcd and address 3
[89863.110771] usb 2-2: new full speed USB device using ohci_hcd and address 4
root@Trevor2:/home/trevor-max# 

```


Sudo eject got :

```
root@Trevor2:/home/trevor-max# sudo eject
eject: tried to use `/dev/hdc' as device name but it is no block device
eject: unable to find or open device for: `cdrom'

```

I'm pretty sure i have one...

Do I need a driver?
i don't think any wires came loose cuz i haven't really opened up my tower for a while...

---

### Post by logos34 on 2008-06-03
I had a problem too when I did a fresh install of 8.04 (with separate /home).

It seems that Hardy botched the block-device links in /dev so that no cd/dvds mounted, and got fstab cdrom line wrong. (i.e. 'scd0' for 'hdc')

> I don't know what the CD drive is and i forget the code to find it...

One helpful command is  

sudo lshw -C disk

(*look under 'logical name' for cdrom drive designation)

I had to add symlinks in /dev:

/dev/**cdrom** --> /dev/hdc

/dev/**dvd** --> /dev/hdc

Then I restarted VLC and under drive '/dev/dvd' worked properly

---

### Post by mc4man on 2008-06-04
post the results of  sudo lshw -C disk
and from  /etc/udev/rules.d - the contents of 70-persistent-cd rules.
ultimately it's 70-persistent-cd rules that determines your links in /dev and in the long run it's best to square things up there. (if needed)

side note; if you want to grep your cdrom use ```
CD-ROM
``` caps matter

---

### Post by logos34 on 2008-06-04
> **mc4man said:**
> post the results of  sudo lshw -C disk
and from  /etc/udev/rules.d - the contents of 70-persistent-cd rules.
ultimately it's 70-persistent-cd rules that determines your links in /dev and in the long run it's best to square things up there. (if needed)

side note; if you want to grep your cdrom use ```
CD-ROM
``` caps matter

Interesting. 

Mine:

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# ASUS_DRW-1608P2 (pci-0000:00:0d.0-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-ide-1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-ide-1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-ide-1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-ide-1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DRW-1608P2 (pci-0000:00:0d.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"

So that's why when I boot the -17 and -18 kernels (where the libata storage driver seems to kick in and see the ide cd/dvd drive as a scsi) the symlinks change in /dev, pointing to 'scd0' (instead of ide 'hdx') and addng a '1' on the end (cdrom1, dvd1, etc)

---

### Post by mc4man on 2008-06-04
@logos34
If for some reason you haven't figured the solution out or for others with similar see here - piece of cake
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

side note; when you replace a drive the links for the new drive can also be assigned 1 up (prior drive links reserved for possible re install) - also worth fixing if that happens to occur

---

### Post by Just-trevor on 2008-06-04
thanks
the link on the last post did it
appreciate the help
thanks again!

---

### Post by MichaelDance on 2009-12-18
> **Prospero2006 said:**
> Try this:

dmesg | grep cd

That should tell you the device name.

Have you tried
```

sudo eject

```to force eject?
 
I Tried dmesg | grep cd and got this:
```
[    1.833115] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.833170] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.833193] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.833200] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.833301] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.837249] ehci_hcd 0000:00:1d.7: debug port 1
[    1.837263] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.837291] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0d44000
[    1.852033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.852431] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.852471] uhci_hcd: USB Universal Host Controller Interface driver
[    1.852519] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.852532] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.852540] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.852612] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.852653] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.853034] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.853048] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.853055] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.853138] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.853190] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.853548] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.853562] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.853569] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.853643] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.853695] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.854049] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.854063] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.854070] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.854141] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.854193] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[65717.493340] usb 1-4: new high speed USB device using ehci_hcd and address 2
[119238.673145] ehci_hcd 0000:00:1d.7: PME# disabled
[119239.914357] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[119239.914436] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[119239.914510] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[119239.914583] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[119239.914657] ehci_hcd 0000:00:1d.7: PME# disabled
[119239.914666] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[119239.918567] ehci_hcd 0000:00:1d.7: debug port 1
[119239.918579] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[119280.196863] ehci_hcd 0000:00:1d.7: PME# disabled
[119281.641326] ehci_hcd 0000:00:1d.7: PME# disabled
[119282.391139] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[119282.391200] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[119282.391257] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[119282.391314] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[119282.391371] ehci_hcd 0000:00:1d.7: PME# disabled
[119282.391381] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[139885.716919] ehci_hcd 0000:00:1d.7: PME# disabled
[139887.161240] ehci_hcd 0000:00:1d.7: PME# disabled
[139887.911696] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[139887.911760] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[139887.911818] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[139887.911876] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[139887.911935] ehci_hcd 0000:00:1d.7: PME# disabled
[139887.911945] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[143560.276921] ehci_hcd 0000:00:1d.7: PME# disabled
[143561.721260] ehci_hcd 0000:00:1d.7: PME# disabled
[143562.471345] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[143562.471407] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[143562.471466] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[143562.471525] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[143562.471583] ehci_hcd 0000:00:1d.7: PME# disabled
[143562.471592] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[143598.528922] ehci_hcd 0000:00:1d.7: PME# disabled
[143599.973266] ehci_hcd 0000:00:1d.7: PME# disabled
[143600.723367] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[143600.723431] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[143600.723490] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[143600.723547] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[143600.723607] ehci_hcd 0000:00:1d.7: PME# disabled
[143600.723616] ehci_hcd 0000:00:1d.7: setting latency timer to 64

```
any help?

---

### Post by MichaelDance on 2009-12-18
> **logos34 said:**
> Interesting. 

Mine:



So that's why when I boot the -17 and -18 kernels (where the libata storage driver seems to kick in and see the ide cd/dvd drive as a scsi) the symlinks change in /dev, pointing to 'scd0' (instead of ide 'hdx') and addng a '1' on the end (cdrom1, dvd1, etc)

Mines:
```
michael@michael-laptop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD1200BEVS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXE408HJ2686
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ba6fc60a

```

---

### Post by MichaelDance on 2009-12-18
> **Prospero2006 said:**
> Try this:

dmesg | grep cd

That should tell you the device name.

Have you tried
```

sudo eject

```to force eject?

I got this when i tried it:
```
michael@michael-laptop:~$ sudo eject
eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'

```

---

### Post by alex_o on 2010-09-18
> **mc4man said:**
> post the results of  sudo lshw -C disk
and from  /etc/udev/rules.d - the contents of 70-persistent-cd rules.
ultimately it's 70-persistent-cd rules that determines your links in /dev and in the long run it's best to square things up there. (if needed)

side note; if you want to grep your cdrom use ```
CD-ROM
``` caps matter

or use grep -i cd-rom to find both cd-rom and CD-ROM :p

---

