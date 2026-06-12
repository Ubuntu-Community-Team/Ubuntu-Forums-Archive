---
title: "Zogis Real Angel 220 TV Turner Card"
date: 2012-01-09
forum: Multimedia Software
---

### Post by Darkhaund on 2012-01-09
Hello everyone. I have tried several times in the past to make a switch from Windows to linux. For one reason or another I endup giving up and going back to widnows. I have finally decided to get a "new" computer just for me to be more patient and learn linux. I decided to try ubuntu this time, since Kubunto gave me a buch or errors.

One of the first things I need help with, is how to properly setup my Zogis Real Angel 220 TV Turner Card.
The card is obviously plugged in, and I have downloaded and installed TVTime. When I launch TVTime it shows a black window for a few seconds and then it shuts down.

I am a NEW linux/ubuntu user and I would appreciate all the help.

Thank you in advance

---

### Post by MartyBuntu on 2012-01-09
maybe this can help you...

[http://ubuntuforums.org/showthread.php?t=931949](http://ubuntuforums.org/showthread.php?t=931949)

---

### Post by Darkhaund on 2012-01-10
I read the post you suggested and i am lost.. any help??

---

### Post by Darkhaund on 2012-01-10
I apologize for the bump, but i would greatly apprcaite any help on this matter.

---

### Post by Darkhaund on 2012-01-11
When I open TVTime i see the progarm window for like about 1 second with a blue screen, then it dissapeear.. i dont know what else do to.

---

### Post by Darkhaund on 2012-01-13
I tried asking for help on the multimedia section and all i got was reference to other threads. I have spent time since reading all of those links and i am STILL LOST and without a clue as to what  to do. I really need help ugys.

I am a rookie in linux and I am liking Ubuntu so far. I would GREATLY appreciate if somone cave give me a "walkthrough" AS TO how to properly setup my video capture card. Please don't tell me to read this or look at that. I have read wikis, other posts etc etc etc and I think my problem is I am new to linux and my understanding of compiling and the way things work is what is giving me a hard time.

On TVTime the window opens and about .5 seconds lates it goes blue and shuts down.

My TV video capture card is a Zogis Real Angel 220 with FM

Thank you in advance.

---

### Post by MG&amp;TL on 2012-01-13
You've come to the right place. :)

Can you link to your old thread please?

(I have no idea what to do, but others will, and they need that information)

---

### Post by Darkhaund on 2012-01-13
Much appreciated!

This is my old post

[http://ubuntuforums.org/showthread.php?t=1906726](http://ubuntuforums.org/showthread.php?t=1906726)


Some of the stuff i have read mentions sudo this, sudo that, make a modporde.conf others suggest a totally different thing. I would REALLY APPRECIATE help. I am sure once I get this done I will be able to figure out things on my own much easier.

I have tried MythTV, TVTime and nothing works.
I also fear that if I do something wrong I will crash my entire system and thus giving up on my linux attempt. I have some files that some wikis and guides suggsted i made and now I can even delete them!!! saa7134, saa7134.conf, options.d etc etc etc 

Thanks

---

### Post by MG&amp;TL on 2012-01-13
As mentioned, I have no idea, but since you will be tackling a command-line, I would suggest knowing a few tips and tricks to make your life easier.

[linuxcommand.org]("linuxcommand.org")


You don't need to read all of it (especially not the scripting stuff), but a rudimentary knowledge is helpful.

---

### Post by Darkhaund on 2012-01-13
Thank you, I will start reading that and I hope helps comes along the way. I REALLY need that video capture card to work, since I use it to record some stuff that my wife needs.

---

### Post by anewguy on 2012-01-13
I don't have a video capture card, but I can tell you what I think all the stuff in the old threads were saying:

- open a terminal window

- type:

gksudo gedit /etc/modprobe.d/options

This will probably bring up a blank file.

Add this line to that blank file:

card=5

Use the "Save" function of the editor to save the file.

- exit the terminal window

- reboot

EDIT:  check dmesg now

Test your video now.

If that doesn't work, edit the file again and change the 5 to a 6 and save the file and reboot again.

EDIT:  check dmesg now

Test your video now.

If that doesn't work, edit the file again and change the 6 to 88 and save the file and reboot again.

EDIT:  check dmesg now

Test your video now.

Post back with the results.

Dave ;)

---

### Post by anewguy on 2012-01-13
BTW - PLEASE do not create duplicate threads.  This is an exact duplicate of your previous thread: [http://ubuntuforums.org/showthread.php?p=11604218#post11604218]("http://ubuntuforums.org/showthread.php?p=11604218#post11604218")

I'll be asking a moderator to merge the threads.

---

### Post by Darkhaund on 2012-01-13
> **anewguy said:**
> BTW - PLEASE do not create duplicate threads.  This is an exact duplicate of your previous thread: [http://ubuntuforums.org/showthread.php?p=11604218#post11604218](http://ubuntuforums.org/showthread.php?p=11604218#post11604218)

I'll be asking a moderator to merge the threads.


Thank you, but i was getting NO HELP on that forum.
Ok, so far I made the options file with card=5

What am i supposed to see on dmesg? What am i looking for?

---

### Post by lisati on 2012-01-13
*Threads merged and moved to **Multimedia & Video**.*

---

### Post by Darkhaund on 2012-01-13
Still nothing.. any help?

---

### Post by MG&amp;TL on 2012-01-14
Well, open a terminal and type:

```
dmesg
```

Then paste output in code tags. There will be rather a lot. I would grep it, but I don't know what I'm looking for.

---

### Post by Darkhaund on 2012-01-14
I changed the card value to 5, 6 and 88 and I still get the same result

I open TVTtime and after .5 seconds the window goes blue and then it shuts down.

I would appreciate some help

Here is my code

```
[    1.331243] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.331597] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.331604] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.331692] mousedev: PS/2 mouse device common for all mice
[    1.331760] rtc_cmos 00:03: RTC can wake from S4
[    1.331832] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.331853] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.331914] device-mapper: uevent: version 1.0.3
[    1.331953] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.331958] cpuidle: using governor ladder
[    1.331959] cpuidle: using governor menu
[    1.331961] EFI Variables Facility v0.08 2004-May-17
[    1.332117] TCP cubic registered
[    1.332187] NET: Registered protocol family 10
[    1.332482] NET: Registered protocol family 17
[    1.332491] Registering the dns_resolver key type
[    1.332551] PM: Hibernation image not present or could not be loaded.
[    1.332558] registered taskstats version 1
[    1.339962] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.355057]   Magic number: 12:430:860
[    1.355153] rtc_cmos 00:03: setting system clock to 2012-01-15 00:52:56 UTC (1326588776)
[    1.355167] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor (4 cpu cores) (version 2.20.00)
[    1.355195] powernow-k8:    0 : pstate 0 (3400 MHz)
[    1.355196] powernow-k8:    1 : pstate 1 (2700 MHz)
[    1.355197] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.355198] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.355758] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.355761] EDD information not available.
[    1.356998] Freeing unused kernel memory: 984k freed
[    1.357197] Write protecting the kernel read-only data: 10240k
[    1.357359] Freeing unused kernel memory: 16k freed
[    1.360581] Freeing unused kernel memory: 1396k freed
[    1.371974] udevd[127]: starting version 173
[    1.389954] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.389989] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.390043] r8169 0000:02:00.0: setting latency timer to 64
[    1.390090] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.390401] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000c1e000, 00:25:11:14:ea:57, XID 1c4000c0 IRQ 43
[    1.393975] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.393999] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.394041] r8169 0000:03:00.0: setting latency timer to 64
[    1.394082] r8169 0000:03:00.0: irq 44 for MSI/MSI-X
[    1.394403] r8169 0000:03:00.0: eth1: RTL8168c/8111c at 0xffffc90000c78000, 00:25:11:14:ea:58, XID 1c4000c0 IRQ 44
[    1.400445] ahci 0000:00:11.0: version 3.0
[    1.400476] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.400609] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.400612] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.402234] scsi0 : ahci
[    1.403455] scsi1 : ahci
[    1.404083] scsi2 : ahci
[    1.404677] scsi3 : ahci
[    1.405354] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22
[    1.405358] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22
[    1.405361] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22
[    1.405363] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22
[    1.406185] scsi4 : pata_atiixp
[    1.406235] scsi5 : pata_atiixp
[    1.406619] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.406621] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.411143] Floppy drive(s): fd0 is 1.44M
[    1.427819] FDC 0 is a post-1991 82077
[    1.568514] ata5.00: ATA-7: ST3400832AS, 3.03, max UDMA/133
[    1.568516] ata5.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.568522] ata5.00: limited to UDMA/33 due to 40-wire cable
[    1.584497] ata5.00: configured for UDMA/33
[    1.684031] Refined TSC clocksource calibration: 3400.119 MHz.
[    1.684041] Switching to clocksource tsc
[    1.724045] ata3: SATA link down (SStatus 0 SControl 300)
[    1.724076] ata2: SATA link down (SStatus 0 SControl 300)
[    1.732039] ata4: SATA link down (SStatus 0 SControl 300)
[    1.732078] ata1: SATA link down (SStatus 0 SControl 300)
[    1.739725] scsi 4:0:0:0: Direct-Access     ATA      ST3400832AS      3.03 PQ: 0 ANSI: 5
[    1.739828] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    1.739851] sd 4:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    1.739952] sd 4:0:0:0: [sda] Write Protect is off
[    1.739954] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.739977] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.760530] ata6.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    1.760534] ata6.01: limited to UDMA/33 due to 40-wire cable
[    1.785211]  sda: sda1 sda2 < sda5 >
[    1.785453] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.792396] ata6.01: configured for UDMA/33
[    1.794151] scsi 5:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    1.796875] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.796877] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.796949] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    1.796992] sr 5:0:1:0: Attached scsi generic sg1 type 5
[    2.079488] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.079491] EXT4-fs (sda1): write access will be enabled during recovery
[    2.128033] usb 5-3: new full speed USB device number 2 using ohci_hcd
[    2.309239] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input2
[    2.309335] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3/input0
[    2.317254] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/input/input3
[    2.317326] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3/input1
[    2.317335] usbcore: registered new interface driver usbhid
[    2.317337] usbhid: USB HID core driver
[    2.568025] usb 6-2: new low speed USB device number 2 using ohci_hcd
[    2.747342] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input4
[    2.747467] generic-usb 0003:045E:0750.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Wired Keyboard 600] on usb-0000:00:13.1-2/input0
[    2.757206] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input5
[    2.757262] generic-usb 0003:045E:0750.0004: input,hidraw3: USB HID v1.11 Device [Microsoft Wired Keyboard 600] on usb-0000:00:13.1-2/input1
[    3.020018] usb 3-2: new full speed USB device number 2 using ohci_hcd
[    3.206172] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.3/input/input6
[    3.206230] generic-usb 0003:046D:0A0C.0005: input,hidraw4: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:12.0-2/input3
[    3.739480] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.739488] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9313907
[    3.754821] EXT4-fs (sda1): 1 orphan inode deleted
[    3.754824] EXT4-fs (sda1): recovery complete
[    4.057964] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.037474] udevd[415]: starting version 173
[   15.164255] Adding 8386556k swap on /dev/sda5.  Priority:-1 extents:1 across:8386556k 
[   15.241037] type=1400 audit(1326588790.382:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=475 comm="apparmor_parser"
[   15.241089] type=1400 audit(1326588790.382:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=462 comm="apparmor_parser"
[   15.241106] type=1400 audit(1326588790.382:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=560 comm="apparmor_parser"
[   15.241364] type=1400 audit(1326588790.382:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=475 comm="apparmor_parser"
[   15.241419] type=1400 audit(1326588790.382:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=462 comm="apparmor_parser"
[   15.241440] type=1400 audit(1326588790.382:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=560 comm="apparmor_parser"
[   15.241567] type=1400 audit(1326588790.382:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=475 comm="apparmor_parser"
[   15.241610] type=1400 audit(1326588790.382:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=462 comm="apparmor_parser"
[   15.241651] type=1400 audit(1326588790.382:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=560 comm="apparmor_parser"
[   15.244872] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.245152] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   15.245214] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   15.245400] MCE: In-kernel MCE decoding enabled.
[   15.245818] EDAC MC: Ver: 2.1.0
[   15.245884] lp: driver loaded but no devices found
[   15.246397] AMD64 EDAC driver v3.4.0
[   15.247068] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.247071] Disabling lock debugging due to kernel taint
[   15.248711] wmi: Mapper loaded
[   15.250969] EDAC amd64: DRAM ECC disabled.
[   15.250978] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   15.250979]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   15.250980]  (Note that use of the override may cause unknown side effects.)
[   15.263872] cfg80211: Calling CRDA to update world regulatory domain
[   15.264010] Linux video capture interface: v2.00
[   15.271617] IR NEC protocol handler initialized
[   15.272403] ath5k 0000:04:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.272461] ath5k 0000:04:06.0: registered as 'phy0'
[   15.275084] IR RC5(x) protocol handler initialized
[   15.285992] IR RC6 protocol handler initialized
[   15.290597] saa7134: Unknown parameter `oss'
[   15.297438] IR JVC protocol handler initialized
[   15.299913] IR Sony protocol handler initialized
[   15.307724] lirc_dev: IR Remote Control driver registered, major 250 
[   15.308162] IR LIRC bridge handler initialized
[   15.312134] cfg80211: World regulatory domain updated:
[   15.312137] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.312139] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.312140] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.312142] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.312143] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.312145] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.314354] [fglrx] Maximum main memory to use for locked dma buffers: 7768 MBytes.
[   15.314504] [fglrx]   vendor: 1002 device: 94b3 count: 1
[   15.314940] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   15.314953] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.314957] pci 0000:01:00.0: setting latency timer to 64
[   15.315150] [fglrx] Kernel PAT support is enabled
[   15.315164] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[   15.319693] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   15.337172] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/input/input7
[   15.337257] usbcore: registered new interface driver uvcvideo
[   15.337259] USB Video Class driver (v1.1.0)
[   15.774064] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.776143] ath: EEPROM regdomain: 0x809c
[   15.776144] ath: EEPROM indicates we should expect a country code
[   15.776146] ath: doing EEPROM country->regdmn map search
[   15.776147] ath: country maps to regdmn code: 0x52
[   15.776148] ath: Country alpha2 being used: CN
[   15.776149] ath: Regpair used: 0x52
[   15.776151] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.776153] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776154] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.776156] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776157] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.776159] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776161] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.776162] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776164] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.776165] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776167] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.776168] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776170] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.776171] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776173] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.776174] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776176] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.776177] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776179] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.776180] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776182] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.776183] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.776185] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.776186] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.776188] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.776219] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.776221] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776223] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.776224] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776226] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.776228] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776229] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.776231] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776232] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.776234] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776235] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.776237] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776238] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.776240] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776241] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.776243] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776244] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.776246] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776247] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.776249] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776250] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.776252] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776253] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.776255] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776256] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.776258] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.776260] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.776261] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.778042] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.778397] ath5k phy0: Atheros AR2417 chip found (MAC: 0xf0, PHY: 0x70)
[   15.778409] cfg80211: Calling CRDA for country: CN
[   15.782570] saa7134: Unknown parameter `oss'
[   15.784009] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.784011] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784013] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.784015] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784016] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.784017] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784019] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.784020] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784022] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.784023] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784024] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.784026] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784027] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.784029] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784030] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.784032] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784033] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.784034] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784036] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.784037] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784038] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.784040] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784041] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.784043] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784044] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.784046] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.784047] cfg80211: Disabling freq 2484 MHz
[   15.784050] cfg80211: Regulatory domain changed to country: CN
[   15.784051] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.784053] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   15.784054] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   15.818360] hda_codec: ALC888: BIOS auto-probing.
[   15.829678] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   15.829838] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.829910] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   15.829932] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.850971] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   15.851071] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input9
[   16.077988] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.151860] type=1400 audit(1326588791.290:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1048 comm="apparmor_parser"
[   16.230436] init: failsafe main process (995) killed by TERM signal
[   16.230669] init: apport pre-start process (1091) terminated with status 1
[   16.234780] init: apport post-stop process (1116) terminated with status 1
[   16.240074] init: Failed to spawn mysql main process: unable to execute: No such file or directory
[   16.250400] r8169 0000:02:00.0: eth0: link down
[   16.251208] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.256295] r8169 0000:03:00.0: eth1: link down
[   16.257027] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.267323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.344091] 2:3:1: cannot get freq at ep 0x86
[   16.344241] set volume quirk for QuickCam E3500
[   16.369799] usbcore: registered new interface driver snd-usb-audio
[   16.374346] Bluetooth: Core ver 2.16
[   16.374368] NET: Registered protocol family 31
[   16.374370] Bluetooth: HCI device and connection manager initialized
[   16.374372] Bluetooth: HCI socket layer initialized
[   16.374373] Bluetooth: L2CAP socket layer initialized
[   16.374410] Bluetooth: SCO socket layer initialized
[   16.375586] Bluetooth: RFCOMM TTY layer initialized
[   16.375589] Bluetooth: RFCOMM socket layer initialized
[   16.375590] Bluetooth: RFCOMM ver 1.11
[   16.377799] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.377801] Bluetooth: BNEP filters: protocol multicast
[   16.762645] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   17.215233] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   17.215236] vesafb: scrolling: redraw
[   17.215238] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   17.217940] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90013200000, using 5824k, total 5824k
[   17.218161] Console: switching to colour frame buffer device 175x65
[   17.218182] fb0: VESA VGA frame buffer device
[   17.223419] init: mythtv-backend main process (1310) terminated with status 127
[   17.223437] init: mythtv-backend main process ended, respawning
[   17.225359] init: mythtv-backend main process (1321) terminated with status 127
[   17.225375] init: mythtv-backend main process ended, respawning
[   17.227157] init: mythtv-backend main process (1324) terminated with status 127
[   17.227173] init: mythtv-backend respawning too fast, stopped
[   17.231496] init: plymouth-splash main process (1312) terminated with status 1
[   17.237522] ppdev: user-space parallel port driver
[   17.437218] fglrx_pci 0000:01:00.0: irq 46 for MSI/MSI-X
[   17.437643] [fglrx] Firegl kernel thread PID: 1351
[   17.437677] [fglrx] Firegl kernel thread PID: 1352
[   17.437710] [fglrx] Firegl kernel thread PID: 1353
[   17.437875] [fglrx] IRQ 46 Enabled
[   18.345040] [fglrx] Gart USWC size:1280 M.
[   18.345043] [fglrx] Gart cacheable size:508 M.
[   18.345047] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.345049] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[   18.345050] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   18.919608] wlan0: authenticate with 98:2c:be:8a:d4:3a (try 1)
[   18.921492] wlan0: authenticated
[   18.921607] wlan0: associate with 98:2c:be:8a:d4:3a (try 1)
[   18.924497] wlan0: RX AssocResp from 98:2c:be:8a:d4:3a (capab=0x411 status=0 aid=1)
[   18.924500] wlan0: associated
[   18.925609] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.925676] cfg80211: Calling CRDA for country: US
[   18.927978] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.927981] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.927982] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.927984] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.927985] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.927987] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.927988] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.927990] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.927991] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.927993] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.927994] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.927996] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.927997] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.927999] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.928015] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.928017] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.928018] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.928020] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.928021] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.928023] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.928024] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.928026] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   18.928027] cfg80211: Disabling freq 2467 MHz
[   18.928030] cfg80211: Disabling freq 2472 MHz
[   18.928032] cfg80211: Disabling freq 2484 MHz
[   18.928036] cfg80211: Regulatory domain changed to country: US
[   18.928039] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.928043] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   18.928046] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   18.928050] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.928053] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.928057] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.928060] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   20.197051] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.960007] wlan0: no IPv6 routers present
[   31.428169] 2:3:1: cannot set freq 16000 to ep 0x86
[   32.428191] 2:3:1: cannot set freq 16000 to ep 0x86
[   33.432089] 2:3:1: cannot set freq 16000 to ep 0x86
[   34.432116] 2:3:1: cannot set freq 16000 to ep 0x86
[   35.432142] 2:3:1: cannot set freq 16000 to ep 0x86
[   36.432042] 2:3:1: cannot set freq 16000 to ep 0x86
[   37.432069] 2:3:1: cannot set freq 16000 to ep 0x86
[   38.432099] 2:3:1: cannot set freq 16000 to ep 0x86
[   39.432123] 2:3:1: cannot set freq 16000 to ep 0x86
[   40.432150] 2:3:1: cannot set freq 16000 to ep 0x86
[   41.432049] 2:3:1: cannot set freq 16000 to ep 0x86
[   42.432075] 2:3:1: cannot set freq 16000 to ep 0x86
[   43.432102] 2:3:1: cannot set freq 16000 to ep 0x86
[   44.432128] 2:3:1: cannot set freq 16000 to ep 0x86
[   45.432159] 2:3:1: cannot set freq 16000 to ep 0x86
[   46.432058] 2:3:1: cannot set freq 16000 to ep 0x86
[   47.432083] 2:3:1: cannot set freq 16000 to ep 0x86
[   48.432119] 2:3:1: cannot set freq 16000 to ep 0x86
[   49.432147] 2:3:1: cannot set freq 16000 to ep 0x86
[   50.432173] 2:3:1: cannot set freq 16000 to ep 0x86
[   59.580031] usb 1-1: reset high speed USB device number 2 using ehci_hcd
[   59.826878] snd-usb-audio 1-1:1.2: no reset_resume for driver snd-usb-audio?
[   59.826881] snd-usb-audio 1-1:1.3: no reset_resume for driver snd-usb-audio?
```

---

### Post by littlepeon on 2012-01-14
hello there,
be patient, we are trying to help you, but few (if any) of us have that tuner card, so you are experiencing the pains of going a path less traveled....
k, most are asking you to run dmesg to find out the chipset used by that card(as many different chipsets are used and require different  ways to make the driver work in linux....once we get the chipset name, we can get the hardware working and you can use any software program to use it...
k, if google is correct, it seems that your tuner card uses this chipset:  ```
Philips saa7134, Philips saa7130
``` 
and the output of /sbin/lspci should give you: ```
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

k now, google-ing revealed that someone asked about getting this card working on linuxquestions.org and this was what they found out:
> I got lucky, after only doing a few hundred tests, "modprobe saa7134 card=3 tuner=0" worked. Many other tuner numbers worked too with card=3. Video and audio quality is good.
This is strange -- the video output doesn't appear on the 'Television' output -- but instead appears on 'Composite2' output. You can only tune channels by using 'Input Configuration', switching to a blue-screen 'Television' and then switching back to 'Composite' to view it.
There is no /dev/tuner.

so using their input of "modprobe saa7134 card=3 tuner=0" should get your hardware working, which should get any software program to use it...where you are going to run into problems is that most linux tuner software looks at /dev/tuner for a tv-card....so others will have to direct you on how to get around that obstacle.

have fun---
google and this forum are your friends
-Peon

---

### Post by Darkhaund on 2012-01-15
Thank you for your response. But Like I said, you are dealing with a totall noob in me. I am sure you gave me the answer in your reply.. "i cant understand" what you are trying to say.

Do i need to make another file?
Do i just need to make a options file with "card=3"

Im lost

Thanks

---

### Post by anewguy on 2012-01-15
To do that command:

- open a terminal window

- type:

sudo modprobe saa7134 card=3 tuner=0 <press enter>

- close the terminal window

Please note the following with the above:

- this is the same as:[LIST]
[*]putting card=3 tuner=0 in the config file where I had you trying the card= statements
[*]and[*]sudo modprobe saa7134
[/LIST]

The modprobe is only until the next boot.  We can make it permanent and make the card and tuner statements permanent once you have tested.

The rest of what littlepeon is telling you is that you may have to change the input tuner device in the software you run in order to find the device.

Dave ;)

---

### Post by Darkhaund on 2012-01-16
Hello

Did jut what you said and i got this error

[sudo] password for darkhaund: 
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting saa7134 (/lib/modules/3.0.0-14-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134
darkhaund@darkbox-ubuntu:~$

---

### Post by Darkhaund on 2012-01-17
Bump?

Any help on this would be appreciated

---

### Post by anewguy on 2012-01-17
Did you dmesg like it says and check the tail end to see what kind of error got posted when it tried to load the saa7134 module?

I would have no clue without seeing what's in the log.

Dave ;)

---

### Post by Darkhaund on 2012-01-17
> **anewguy said:**
> Did you dmesg like it says and check the tail end to see what kind of error got posted when it tried to load the saa7134 module?

I would have no clue without seeing what's in the log.

Dave ;)

I posted my dmesg log a few posts above
What do you mean dmesg like it says?

Do i just type dmesg in the terminal or do i type dmesg and something else?

Ty

---

### Post by anewguy on 2012-01-17
> Hello

Did jut what you said and i got this error

[sudo] password for darkhaund:
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting saa7134 (/lib/modules/3.0.0-14-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134
darkhaund@darkbox-ubuntu:~$

Your last attempt - as I've quoted - says on the first FATAL message to see dmesg for specifics.  You need to understand - dmesg will contain different messages if something else failed, so I can't just go off of what you posted before.

So, try the modprobe again, and follow it immediately with the last couple of pages from dmesg (enclose in code tags using the pound button on the tool bar).

---

### Post by Darkhaund on 2012-01-17
Did this

```
 darkhaund@darkbox-ubuntu:~$ sudo modprobe saa7134 card=3 tuner=0
[sudo] password for darkhaund: 
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting saa7134 (/lib/modules/3.0.0-14-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134

```

And dmesg appears to be cut... this is the only thing i got

```
 [    1.192075] hub 5-0:1.0: USB hub found
[    1.192080] hub 5-0:1.0: 3 ports detected
[    1.192207] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.192217] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.192237] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.192251] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7fb000
[    1.252078] hub 6-0:1.0: USB hub found
[    1.252083] hub 6-0:1.0: 3 ports detected
[    1.252208] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.252219] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.252241] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.252254] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe7fa000
[    1.312031] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.312077] hub 7-0:1.0: USB hub found
[    1.312082] hub 7-0:1.0: 2 ports detected
[    1.312146] uhci_hcd: USB Universal Host Controller Interface driver
[    1.312193] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.312535] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.312540] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.312629] mousedev: PS/2 mouse device common for all mice
[    1.312697] rtc_cmos 00:03: RTC can wake from S4
[    1.312768] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.312790] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.312851] device-mapper: uevent: version 1.0.3
[    1.312890] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.312896] cpuidle: using governor ladder
[    1.312897] cpuidle: using governor menu
[    1.312898] EFI Variables Facility v0.08 2004-May-17
[    1.313039] TCP cubic registered
[    1.313109] NET: Registered protocol family 10
[    1.313403] NET: Registered protocol family 17
[    1.313413] Registering the dns_resolver key type
[    1.313471] PM: Hibernation image not present or could not be loaded.
[    1.313478] registered taskstats version 1
[    1.336110]   Magic number: 12:400:500
[    1.336205] rtc_cmos 00:03: setting system clock to 2012-01-17 21:29:53 UTC (1326835793)
[    1.336220] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor (4 cpu cores) (version 2.20.00)
[    1.336248] powernow-k8:    0 : pstate 0 (3400 MHz)
[    1.336249] powernow-k8:    1 : pstate 1 (2700 MHz)
[    1.336250] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.336251] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.336808] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.336810] EDD information not available.
[    1.337894] Freeing unused kernel memory: 984k freed
[    1.338094] Write protecting the kernel read-only data: 10240k
[    1.338252] Freeing unused kernel memory: 16k freed
[    1.341473] Freeing unused kernel memory: 1396k freed
[    1.352770] udevd[127]: starting version 173
[    1.367193] ahci 0000:00:11.0: version 3.0
[    1.367226] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.367340] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.367343] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.367853] scsi0 : ahci
[    1.367958] scsi1 : ahci
[    1.368217] scsi2 : ahci
[    1.368284] scsi3 : ahci
[    1.368366] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22
[    1.368369] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22
[    1.368371] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22
[    1.368374] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22
[    1.375645] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.375674] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.375724] r8169 0000:02:00.0: setting latency timer to 64
[    1.375769] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.376206] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000c78000, 00:25:11:14:ea:57, XID 1c4000c0 IRQ 43
[    1.379169] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.379196] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.379241] r8169 0000:03:00.0: setting latency timer to 64
[    1.379287] r8169 0000:03:00.0: irq 44 for MSI/MSI-X
[    1.379602] r8169 0000:03:00.0: eth1: RTL8168c/8111c at 0xffffc90000c7a000, 00:25:11:14:ea:58, XID 1c4000c0 IRQ 44
[    1.381035] scsi4 : pata_atiixp
[    1.381345] scsi5 : pata_atiixp
[    1.381756] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.381758] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.390057] Floppy drive(s): fd0 is 1.44M
[    1.407800] FDC 0 is a post-1991 82077
[    1.544501] ata5.00: ATA-7: ST3400832AS, 3.03, max UDMA/133
[    1.544503] ata5.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.544508] ata5.00: limited to UDMA/33 due to 40-wire cable
[    1.552503] ata5.00: configured for UDMA/33
[    1.684042] Refined TSC clocksource calibration: 3400.120 MHz.
[    1.684047] Switching to clocksource tsc
[    1.688049] ata3: SATA link down (SStatus 0 SControl 300)
[    1.692050] ata2: SATA link down (SStatus 0 SControl 300)
[    1.692081] ata1: SATA link down (SStatus 0 SControl 300)
[    1.696049] ata4: SATA link down (SStatus 0 SControl 300)
[    1.696182] scsi 4:0:0:0: Direct-Access     ATA      ST3400832AS      3.03 PQ: 0 ANSI: 5
[    1.696282] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    1.696295] sd 4:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    1.696361] sd 4:0:0:0: [sda] Write Protect is off
[    1.696364] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.696387] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.736470] ata6.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    1.736473] ata6.01: limited to UDMA/33 due to 40-wire cable
[    1.738798]  sda: sda1 sda2 < sda5 >
[    1.739040] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.768404] ata6.01: configured for UDMA/33
[    1.770157] scsi 5:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    1.772887] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.772889] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.772962] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    1.773002] sr 5:0:1:0: Attached scsi generic sg1 type 5
[    2.108034] usb 5-3: new full speed USB device number 2 using ohci_hcd
[    2.133890] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.556020] usb 6-2: new low speed USB device number 2 using ohci_hcd
[    2.992020] usb 3-2: new full speed USB device number 2 using ohci_hcd
[   13.599790] udevd[382]: starting version 173
[   13.757763] MCE: In-kernel MCE decoding enabled.
[   13.759408] EDAC MC: Ver: 2.1.0
[   13.761504] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.761507] Disabling lock debugging due to kernel taint
[   13.765628] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.766330] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   13.766512] wmi: Mapper loaded
[   13.766542] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   13.766879] AMD64 EDAC driver v3.4.0
[   13.767383] lp: driver loaded but no devices found
[   13.775668] cfg80211: Calling CRDA to update world regulatory domain
[   13.781786] Adding 8386556k swap on /dev/sda5.  Priority:-1 extents:1 across:8386556k 
[   13.782436] EDAC amd64: DRAM ECC disabled.
[   13.782504] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.782505]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   13.782506]  (Note that use of the override may cause unknown side effects.)
[   13.790224] ath5k 0000:04:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.790275] ath5k 0000:04:06.0: registered as 'phy0'
[   13.790701] cfg80211: World regulatory domain updated:
[   13.790704] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.790706] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.790708] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.790709] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.790711] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.790712] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.792803] Linux video capture interface: v2.00
[   13.803483] type=1400 audit(1326835805.960:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=447 comm="apparmor_parser"
[   13.803497] type=1400 audit(1326835805.960:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=443 comm="apparmor_parser"
[   13.803798] type=1400 audit(1326835805.960:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=447 comm="apparmor_parser"
[   13.803814] type=1400 audit(1326835805.960:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=443 comm="apparmor_parser"
[   13.803997] type=1400 audit(1326835805.960:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=447 comm="apparmor_parser"
[   13.804023] type=1400 audit(1326835805.964:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=443 comm="apparmor_parser"
[   13.807803] [fglrx] Maximum main memory to use for locked dma buffers: 7768 MBytes.
[   13.807950] [fglrx]   vendor: 1002 device: 94b3 count: 1
[   13.807975] IR NEC protocol handler initialized
[   13.808482] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   13.808494] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.808498] pci 0000:01:00.0: setting latency timer to 64
[   13.808685] [fglrx] Kernel PAT support is enabled
[   13.808700] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[   13.809200] type=1400 audit(1326835805.968:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=530 comm="apparmor_parser"
[   13.809515] type=1400 audit(1326835805.968:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   13.809705] type=1400 audit(1326835805.968:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[   13.811363] IR RC5(x) protocol handler initialized
[   13.812617] IR RC6 protocol handler initialized
[   13.813326] saa7134: Unknown parameter `oss'
[   13.815313] IR JVC protocol handler initialized
[   13.817140] IR Sony protocol handler initialized
[   13.818763] lirc_dev: IR Remote Control driver registered, major 250 
[   13.818880] IR LIRC bridge handler initialized
[   13.858324] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   13.861869] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input2
[   13.862060] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3/input0
[   13.869572] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/input/input3
[   13.869660] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3/input1
[   13.874672] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input4
[   13.874803] generic-usb 0003:045E:0750.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Wired Keyboard 600] on usb-0000:00:13.1-2/input0
[   13.874996] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/input/input5
[   13.875281] usbcore: registered new interface driver uvcvideo
[   13.875283] USB Video Class driver (v1.1.0)
[   13.884589] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input6
[   13.884670] generic-usb 0003:045E:0750.0004: input,hidraw3: USB HID v1.11 Device [Microsoft Wired Keyboard 600] on usb-0000:00:13.1-2/input1
[   13.889535] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.3/input/input7
[   13.889588] generic-usb 0003:046D:0A0C.0005: input,hidraw4: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:12.0-2/input3
[   13.889599] usbcore: registered new interface driver usbhid
[   13.889601] usbhid: USB HID core driver
[   14.252183] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.293917] ath: EEPROM regdomain: 0x809c
[   14.293918] ath: EEPROM indicates we should expect a country code
[   14.293920] ath: doing EEPROM country->regdmn map search
[   14.293921] ath: country maps to regdmn code: 0x52
[   14.293922] ath: Country alpha2 being used: CN
[   14.293923] ath: Regpair used: 0x52
[   14.293926] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.293928] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293929] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.293931] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293932] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.293933] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293935] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.293936] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293937] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.293939] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293940] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.293942] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293943] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.293945] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293946] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.293948] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293949] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.293951] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293952] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.293953] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293955] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.293956] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.293958] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   14.293959] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   14.293960] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   14.293993] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.293995] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.293996] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.293998] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.293999] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.294001] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294002] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.294004] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294005] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.294007] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294008] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.294010] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294011] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.294013] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294014] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.294016] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294017] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.294018] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294020] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.294021] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294023] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.294024] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294026] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.294027] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294029] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.294030] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.294032] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   14.294033] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   14.295995] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.296372] ath5k phy0: Atheros AR2417 chip found (MAC: 0xf0, PHY: 0x70)
[   14.296391] cfg80211: Calling CRDA for country: CN
[   14.296815] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.298543] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.298546] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298548] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.298549] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298551] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.298552] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298554] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.298555] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298556] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.298558] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298559] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.298561] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298562] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.298564] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298565] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.298566] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298568] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.298569] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298570] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.298572] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298573] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.298575] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298576] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.298578] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298579] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.298580] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   14.298582] cfg80211: Disabling freq 2484 MHz
[   14.298584] cfg80211: Regulatory domain changed to country: CN
[   14.298585] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.298587] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   14.298588] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   14.303436] saa7134: Unknown parameter `oss'
[   14.319832] hda_codec: ALC888: BIOS auto-probing.
[   14.331367] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   14.331512] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.331579] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   14.331601] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.346872] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   14.346964] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input9
[   14.454233] type=1400 audit(1326835806.612:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1003 comm="apparmor_parser"
[   14.469005] r8169 0000:02:00.0: eth0: link down
[   14.469816] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.474914] r8169 0000:03:00.0: eth1: link down
[   14.477447] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   14.487946] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.585894] init: failsafe main process (938) killed by TERM signal
[   14.588700] init: apport pre-start process (1046) terminated with status 1
[   14.592132] init: Failed to spawn mysql main process: unable to execute: No such file or directory
[   14.594447] init: apport post-stop process (1080) terminated with status 1
[   14.723800] Bluetooth: Core ver 2.16
[   14.723824] NET: Registered protocol family 31
[   14.723826] Bluetooth: HCI device and connection manager initialized
[   14.723828] Bluetooth: HCI socket layer initialized
[   14.723829] Bluetooth: L2CAP socket layer initialized
[   14.724072] Bluetooth: SCO socket layer initialized
[   14.725309] Bluetooth: RFCOMM TTY layer initialized
[   14.725313] Bluetooth: RFCOMM socket layer initialized
[   14.725314] Bluetooth: RFCOMM ver 1.11
[   14.726246] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.726248] Bluetooth: BNEP filters: protocol multicast
[   14.876086] 2:3:1: cannot get freq at ep 0x86
[   14.876234] set volume quirk for QuickCam E3500
[   14.901673] usbcore: registered new interface driver snd-usb-audio
[   15.635086] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.783708] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   15.783710] vesafb: scrolling: redraw
[   15.783712] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   15.786403] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90012f80000, using 5824k, total 5824k
[   15.786607] Console: switching to colour frame buffer device 175x65
[   15.786628] fb0: VESA VGA frame buffer device
[   15.791201] init: mythtv-backend main process (1248) terminated with status 127
[   15.791217] init: mythtv-backend main process ended, respawning
[   15.794897] init: mythtv-backend main process (1259) terminated with status 127
[   15.794912] init: mythtv-backend main process ended, respawning
[   15.799024] init: mythtv-backend main process (1266) terminated with status 127
[   15.799043] init: mythtv-backend respawning too fast, stopped
[   16.024952] ppdev: user-space parallel port driver
[   16.785400] fglrx_pci 0000:01:00.0: irq 46 for MSI/MSI-X
[   16.785812] [fglrx] Firegl kernel thread PID: 1306
[   16.785887] [fglrx] Firegl kernel thread PID: 1307
[   16.785920] [fglrx] Firegl kernel thread PID: 1308
[   16.786111] [fglrx] IRQ 46 Enabled
[   17.167600] wlan0: authenticate with 98:2c:be:8a:d4:3a (try 1)
[   17.169552] wlan0: authenticated
[   17.169644] wlan0: associate with 98:2c:be:8a:d4:3a (try 1)
[   17.173130] wlan0: RX AssocResp from 98:2c:be:8a:d4:3a (capab=0x411 status=0 aid=4)
[   17.173133] wlan0: associated
[   17.174238] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   17.174302] cfg80211: Calling CRDA for country: US
[   17.176491] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.176494] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176495] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.176497] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176499] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.176500] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176501] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.176503] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176504] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.176506] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176507] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.176509] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176510] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.176512] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176513] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.176515] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176516] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.176518] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176519] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.176521] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176522] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.176523] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   17.176525] cfg80211: Disabling freq 2467 MHz
[   17.176526] cfg80211: Disabling freq 2472 MHz
[   17.176526] cfg80211: Disabling freq 2484 MHz
[   17.176529] cfg80211: Regulatory domain changed to country: US
[   17.176530] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.176532] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.176533] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.176535] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.176536] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.176538] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.176539] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.692111] [fglrx] Gart USWC size:1280 M.
[   17.692114] [fglrx] Gart cacheable size:508 M.
[   17.692118] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.692120] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[   17.692121] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   20.618876] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.996884] 2:3:1: cannot get freq at ep 0x86
[   25.419831] [fglrx] IRQ 46 Disabled
[   25.614095] fglrx_pci 0000:01:00.0: irq 46 for MSI/MSI-X
[   25.614508] [fglrx] Firegl kernel thread PID: 1625
[   25.614541] [fglrx] Firegl kernel thread PID: 1626
[   25.614573] [fglrx] Firegl kernel thread PID: 1627
[   25.614715] [fglrx] IRQ 46 Enabled
[   26.439307] [fglrx] Gart USWC size:1280 M.
[   26.439310] [fglrx] Gart cacheable size:508 M.
[   26.439314] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   26.439316] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[   26.439317] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   27.840015] wlan0: no IPv6 routers present
[  729.398038] ISO 9660 Extensions: Microsoft Joliet Level 1
[  729.431352] ISOFS: changing to secondary root
[ 4998.080821] saa7134: Unknown parameter `oss'

```

---

### Post by Darkhaund on 2012-01-17
This is sooo frustrating.... :(

---

### Post by wolfen69 on 2012-01-17
> **Darkhaund said:**
> This is sooo frustrating.... :(
It can be, but at some point you have to ask yourself if it's worth it to spend countless hours trying to get it going, or simply buy a compatible card. I always recommend the [Hauppauge PVR150]("http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=hauppauge+pvr+150+buy&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=4152797006104428493&sa=X&ei=dDoWT8SEAdCUtwf8kKyTAw&ved=0CE0Q8wIwAg") for $39.

[Here]("http://ubuntuforums.org/showthread.php?t=1734916") is my  guide to get it going. I wish you luck if you choose to stay with your current card.

---

### Post by anewguy on 2012-01-17
put the following in the /etc/modprobe.d/options file:

card=3 tuner=0

such that it is the only thing there


Then:

sudo modprobe saa7134 <press enter> (no parameters - just this alone)

If still the same error message, then:

rename /etc/modprobe.d/options to /etc/modprobe.d/saa7134.conf

Then:

sudo modprobe saa7134 <press enter> (no parameters - just this alone)


Also, keep in mind the following:

- your mythtv front end is stopping due to quick restarts.  This may cause the device not to be seen.

- remember the post about changing the input source


I must say that I agree with others completely - if there is a card out there that works out of the box and is something you can afford (check ebay) then it might be worth getting it just to bypass all of this.  I suspect this will only get harder as newer releases come out, as this appears to be a few years old now.

dave ;)

---

### Post by Darkhaund on 2012-01-18
ok... thanks

When i do the 1st thing this is the error i get

```
 darkhaund@darkbox-ubuntu:~$ sudo gedit /etc/modprobe.d/options
[sudo] password for darkhaund: 

(gedit:5266): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.OREJ8V': No such file or directory

(gedit:5266): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or director 
```Now then i try the second command you say i get this

```
 darkhaund@darkbox-ubuntu:~$ sudo modprobe saa7134
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'card=3'
WARNING: All config files need .conf: /etc/modprobe.d/saa7134, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'card=3'
FATAL: Error inserting saa7134 (/lib/modules/3.0.0-14-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134
darkhaund@darkbox-ubuntu:~$ 

```Finallt. after renaming to saa7134.conf i got this error

```
 darkhaund@darkbox-ubuntu:~$ sudo modprobe saa7134
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'card=3'
WARNING: /etc/modprobe.d/saa7134.conf line 1: ignoring bad line starting with 'card=3'
darkhaund@darkbox-ubuntu:~$ 


```

im just about to give up this linux thing :(

I also notice that when i try to open TV time, my logitech webcam "tries" to activate itself.. as if the Saa thing, or whatever. is trying to turn on my webcam instead of my tv capture card

---

### Post by BicyclerBoy on 2012-01-18
All files in /etc/modprobe.d/ need to be *.conf.
All files in /etc/modprobe.d/*.conf are parsed.

You can put your own tuner options into any file but it is tidy to use saa7134.conf or tuner.conf.

The format of your /etc/modprobe.d/saa7134(.conf) file **is wrong**..
Each line entry should start:
options saa7134 [module options]

Valid [module options] can be determined from 
$ modinfo saa7134

You should tidy up all your /etc/modprobe.d/*.conf files; use .conf extension & name the files to reflect their usage. The filename "options" is does not need to be used.


It is recommended to use gksudo with GUI apps.
$ gksudo gedit [some filename]

---

### Post by Darkhaund on 2012-01-18
Thank you for your response.

So, you are saying that this is how my saa7134.conf file should look like?

options saa7134 card=3
options saa7134 tuner= 0

Thanks in advace

---

### Post by BicyclerBoy on 2012-01-18
Yes
You can put both/all module options on the one line
options saa7134 card=3 tuner=0

Additional:
There is the possibility that some module options are pre-compiled into the kernel boot image. You can force refresh by:
$ sudo update-initramfs -u

---

### Post by Darkhaund on 2012-01-18
ok, let me go do that.

Now, like I asked in my previous post. 
I notice that when I try to lead TVTime my logitech webcam "tries" to work, and then the TVTime window goes blue after .5 seconds and shuts down.

Why is TVTime trying to activate my webcam instead of my TV Tuner card?

---

### Post by Darkhaund on 2012-01-18
I did what you told me and still nothing

TVTime window opens for .5 seconds, goes blue and closes

I used gksudo and got some errors

```
 (gksudo:7619): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:7619): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:7619): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:7619): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


```

---

### Post by xc3RnbFO8P on 2012-01-18
Try:
> tvtime --device /dev/video1

---

### Post by anewguy on 2012-01-18
Sorry about not having gksudo instead of sudo - I know better.

Also - for the file format, I was only going by what was in the thread pointed to by the old thread you posted.

So, if this has gotten you further - all I can say is thanks very much to BicyclerBoy.

As I noted coming into this, I know nothing about your card, etc..  Right now, based on the other threads I found on this subject, I am out of things for your to try.

Your TVtime problem - this is what the others have been talking about when they have told you that you need to change the source away from the default.  Go back and read that post again for more information.

Turning on your webcam - could be a result of the above.  Once you get your input pointed to the correct device the camera may still turn on - it may just be the nature of the beast with the software.

Personally, I'm with the others that say to buy a device that just works.  I don't normally say that, but I think you are fighting a very big battle here that may not be worth it.

At any rate, I can't help you further at this time.

---

### Post by Darkhaund on 2012-01-18
Thanks.. i am trying VERY hard to learn this and not just go the easy way out.

I really appreciate everything you have have done and tried to help

i got tthis error now

```
  

darkhaund@darkbox-ubuntu:~$ tvtime --device /dev/video1
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/darkhaund/.tvtime/tvtime.xml
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't get tuner info: Invalid argument
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
Found "USB Device 0x46d:0x9a4 : USB Audio (hw:1,0)"
Channels count non availabledarkhaund@darkbox-ubuntu:~$


```

How can I know IF MY tuner card is even detected?
I think i am seeing alittle big of light ahead of the tunnel..

Please help..

---

### Post by wolfen69 on 2012-01-18
> **Darkhaund said:**
> 

im just about to give up this linux thing :(



Just like a mac, you need to have compatible hardware to run the operating system properly. You can't run windows on a mac, or mac on a windows machine. Linux is no different. In the beginning, I had an incompatible tv tuner card, and printer. So I went out and bought a new tuner card and printer that *was* compatible, and it was the best decision I ever made.

I'm now free from windows, and my computers have never run better. I do hope you can get this card working, but consider buying one known to work if this doesn't work out. You won't regret it. Good luck to you no matter what you decide.

---

### Post by wolfen69 on 2012-01-18
> **Darkhaund said:**
> 
How can I know IF MY tuner card is even detected?


Do
```
lspci
```

---

### Post by xc3RnbFO8P on 2012-01-18
and now:
> tvtime --device /dev/video0

---

### Post by Darkhaund on 2012-01-18
Thanks for your reply

So you are suggesting that if all else fails, I should get this card? 

[http://compare.ebay.com/like/370566373090?var=lv&ltyp=AllFixedPriceItemTypes&var=sbar&_lwgsi=y&cbt=y](http://compare.ebay.com/like/370566373090?var=lv&ltyp=AllFixedPriceItemTypes&var=sbar&_lwgsi=y&cbt=y)

---

### Post by Darkhaund on 2012-01-18
This is what lspci gave out

```
 darkhaund@darkbox-ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 4770 [RV740]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
04:06.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
darkhaund@darkbox-ubuntu:~$ 
 
```

I am assumin this is my card

04:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

So what now?

---

### Post by BicyclerBoy on 2012-01-18
The card is found but the driver sa7134 does not know the exact model &/or it is not supported..

See this very good post/thread:
[http://www.linuxquestions.org/questions/linux-hardware-18/how-to-bring-up-an-unknown-tv-tuner-card-zogis-ra220-tv-tuner-655784/](http://www.linuxquestions.org/questions/linux-hardware-18/how-to-bring-up-an-unknown-tv-tuner-card-zogis-ra220-tv-tuner-655784/)

Well supported tuner h/w will be listed (with driver status) at LinuxTV.org.
[http://linuxtv.org/wiki/index.php/Category:Hardware](http://linuxtv.org/wiki/index.php/Category:Hardware)

---

### Post by Darkhaund on 2012-01-18
Thank you for the link, I will check it out.

Two things:

1. Is the card that I posted a while ago supported, if so I will go ahead and buy it

2. What command can I do to make dmesg display me the entire log? I cant seem to make it work.

---

### Post by wolfen69 on 2012-01-18
> **Darkhaund said:**
> 
1. Is the card that I posted a while ago supported, if so I will go ahead and buy it



Can you post the link again? 

Btw, the card I mentioned, the Hauppauge PVR150/250/350/500 works perfectly. If you can find one, I **GUARANTEE** it works. I know other ones work, but I can't vouch for those. ivtv based cards are well supported.

---

### Post by Darkhaund on 2012-01-18
This is the card, if it works letme know and  I will but it immediately and would appreciate help once i get it.

[Click here]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=370566373090&category=16145&_trksid=p5197.c0.m619")

---

### Post by anewguy on 2012-01-19
Can't remember if you said how old your PC is, so be sure you have an empty slot of the appropriate type (the card you linked to, which I know nothing about, is "regular" PCI - most newer machines are made with the just PCI Express slots anymore.

BTW - you can see from the latest lspci that indeed it recognizes your card now (whatever type you put in the config file).  Now you need to mess with the tuner= portion until you find a tuner that works.

Best of luck!
Dave ;)

---

### Post by Darkhaund on 2012-01-19
Still no luck.

And my fear is if I go ahead and buy a new card, that will not work as well, and I WOULD have wagted my monety

---

### Post by anewguy on 2012-01-20
On page 3 of this thread, wolfen69 posted a link to a card they say works, and for which they can give you help on.  That link brings up a page for the card - further down on the page is a list of places to get it.  The very top 1 on the list is to an Ebay auction that is still open for which there are still 5 available.  These are priced (used) at something like $16.99 and I believe $5 shipping.  Just verify with wolfen69 that the card will work, and that perhaps they will help you with it, and you should be good to go to purchase that 1 on Ebay.


Dave ;)

---

### Post by Darkhaund on 2012-01-21
Just made the purchase... hope to have it soon

---

### Post by anewguy on 2012-01-21
Good luck, and be sure to post back how it goes!.  I've thought about 1 of these off and on, so I'd like to know it works.

Dave ;)

---

### Post by Darkhaund on 2012-01-22
I will. It is a bit hard for some of us to make the linux transition when not so many ppl help to make it easier.  I appreciate the few of you you have them the time in helpingme sort this issue out.

---

### Post by anewguy on 2012-01-23
I think I'll order one of those myself after the 1st of the month.

Thanks!
Dave ;)

BTW - we all just do what we can to try to help, so when you get this working, you'll be able to play it forward on the forum.  ;)

---

### Post by Darkhaund on 2012-01-28
Will install the card this weekend

---

