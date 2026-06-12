---
title: "SAA7130 Tv card installation probelm"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by eekfonky on 2007-04-13
can anyone help? I have recently installed Ubuntu having dumped Mr. Gates and his excuse for software....anyway enough ranting. The problem is with my TV capture card, it doesn't work yet with Ubuntu. I have downloaded drivers for it but haven't yet worked out how or where to install it I did a

dmseg

and got the following:

[   47.232046] saa7130[0]: found at 0000:00:09.0, rev: 1, irq: 11, latency: 32, mmio: 0xe1101000
[   47.232058] saa7130[0]: subsystem: 1131:0000, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[   47.232081] saa7130[0]: board init: gpio is 38500
[   47.363331] saa7130[0]: Huh, no eeprom present (err=-5)?
[   47.397224] tuner 1-0061: chip found @ 0xc2 (saa7130[0])
[   47.469076] tuner 1-0061: could not clearly identify tuner address, defaulting to 61
[   47.508999] tuner 1-0061: type set to tda8290+75a
[   47.644804] tuner 1-0061: could not clearly identify tuner address, defaulting to 61
[   47.684737] tuner 1-0061: type set to tda8290+75a
[   47.756645] tuner 1-0063: chip found @ 0xc6 (saa7130[0])
[   47.759231] saa7130[0]: registered device video0 [v4l2]
[   47.759323] saa7130[0]: registered device vbi0
[   47.759457] saa7130[0]: registered device radio0
[   47.777978] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[   47.777987] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[   47.801973] saa7134 ALSA driver for DMA sound loaded
[   47.802022] saa7130[0]/alsa: saa7130[0] at 0xe1101000 irq 11 registered as card -2

Can anyone help cos I'm at my wits end!!!
Cheers

---

### Post by reclusivemonkey on 2007-04-13
Post the output of 

```

sudo lspci

```

---

### Post by eekfonky on 2007-04-14
Thanks for the help. Here is what it says:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by reclusivemonkey on 2007-04-14
Try installing tvtime

```

sudo apt-get install tvtim

```

and see if it recognises your card.

---

### Post by eekfonky on 2007-04-14
I installed TVtime and when I click on it nothing happens.....what now?

---

### Post by reclusivemonkey on 2007-04-14
> **eekfonky said:**
> I installed TVtime and when I click on it nothing happens.....what now?

You need to start giving some more descriptive answers or you aren't going to get anywhere.

---

### Post by eekfonky on 2007-04-15
TVtime is installed under Applications -> Sound & Video-> TVtime.
When I click on it it starts to load, a window opens saying TVtime on the taskbar, a small black screen appears on the sesktop and then they both disappear.
If I use Zapping TV viewer it actually starts but come up with an error message "Cannot start video overlay. Zapping_setup_fb failed".

---

### Post by reclusivemonkey on 2007-04-15
Start TVTime from a terminal and post the output here please.

---

### Post by eekfonky on 2007-04-15
Here is what happened from the terminal:

~$ gksudo tvtime
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

---

### Post by reclusivemonkey on 2007-04-15
Looks like you graphics card isn't up to the job. BTW, you shouldn't be running as root.

---

### Post by eekfonky on 2007-04-15
Sorry, what does BTW mean? When I was running XP the TV card works fine. It's apparently a "Phillips semiconductor  SAA7130 Video Broadcast Decoder" card if that helps? I just really don't want to have to go back to Windows if I can avoid it. Thanks for the help

---

### Post by eekfonky on 2007-04-16
Sorry, what does BTW mean? My TV card is worked fine with windows xp. I'd rather not have to use xp again if I can avoid it. Any other ideas? Thanks

---

### Post by reclusivemonkey on 2007-04-16
> **eekfonky said:**
> Sorry, what does BTW mean? My TV card is worked fine with windows xp. I'd rather not have to use xp again if I can avoid it. Any other ideas? Thanks

It means "By the way".

I will see if I can find anything to help this evening. I am at work right now.

The fact your card works in Windows XP means it *may* work in Linux, but not that it certainly will.

---

### Post by eekfonky on 2007-04-17
Can I use WINE to install the Windows driver instead?

---

### Post by eekfonky on 2007-04-18
So you can't help then I take it. Thanks anyway. Can anyone else out there?

---

### Post by reclusivemonkey on 2007-04-18
I might be able to. My electricity went out last night for about five hours. I also have a nine month old baby, so I'm afraid I have other priorities. Have you googled the problem? Looked on the TVTime website?

---

### Post by eekfonky on 2007-04-18
I understand you have other priorities, didn't mean to hassle you. I've googled it to no avail. I'll check the TVTime website now and get back to you

---

### Post by eekfonky on 2007-04-18
checked the site for tvtime and is says it supports my TV capture card and the latest linux kernel (which I have) has the correct driver on it. However I'm told if it's set at a value of -1 it's not installed.
How do I check and how do I re-install if that's the issue?

---

### Post by eekfonky on 2007-04-18
just re-installed the downloaded driver: saa7134-0.2.12.tar.gz
and this happened:

~$ tar zxvpf /home/chris/Desktop/Applications/saa7134-0.2.12.tar.gz
saa7134-0.2.12/
saa7134-0.2.12/v4l1-compat.c
saa7134-0.2.12/v4l2-common.c
saa7134-0.2.12/video-buf.c
saa7134-0.2.12/video-buf.h
saa7134-0.2.12/videodev.h
saa7134-0.2.12/videodev2.h
saa7134-0.2.12/tuner.c
saa7134-0.2.12/tuner.h
saa7134-0.2.12/tda9887.c
saa7134-0.2.12/tda9887.h
saa7134-0.2.12/id.h
saa7134-0.2.12/audiochip.h
saa7134-0.2.12/i2c-compat.h
saa7134-0.2.12/doc/
saa7134-0.2.12/doc/CVS/
saa7134-0.2.12/doc/CVS/Root
saa7134-0.2.12/doc/CVS/Repository
saa7134-0.2.12/doc/CVS/Entries
saa7134-0.2.12/doc/CARDLIST.bttv
saa7134-0.2.12/doc/CARDLIST.saa7134
saa7134-0.2.12/doc/CARDLIST.tuner
saa7134-0.2.12/doc/Cards
saa7134-0.2.12/doc/MAKEDEV
saa7134-0.2.12/doc/README.bttv
saa7134-0.2.12/doc/README.cx88
saa7134-0.2.12/doc/README.ir
saa7134-0.2.12/doc/README.saa7134
saa7134-0.2.12/doc/Sound-FAQ
saa7134-0.2.12/doc/Tuners
saa7134-0.2.12/doc/insmod-options
saa7134-0.2.12/doc/not-in-cx2388x-datasheet.txt
saa7134-0.2.12/doc/README.cx88~
saa7134-0.2.12/ir-common.c
saa7134-0.2.12/ir-common.h
saa7134-0.2.12/msp3400.c
saa7134-0.2.12/msp3400.h
saa7134-0.2.12/tvaudio.c
saa7134-0.2.12/tvaudio.h
saa7134-0.2.12/tvmixer.c
saa7134-0.2.12/saa7134-cards.c
saa7134-0.2.12/saa7134-core.c
saa7134-0.2.12/saa7134-i2c.c
saa7134-0.2.12/saa7134-input.c
saa7134-0.2.12/saa7134-oss.c
saa7134-0.2.12/saa7134-reg.h
saa7134-0.2.12/saa7134-ts.c
saa7134-0.2.12/saa7134-tvaudio.c
saa7134-0.2.12/saa7134-vbi.c
saa7134-0.2.12/saa7134-video.c
saa7134-0.2.12/saa7134.h
saa7134-0.2.12/saa6752hs.c
saa7134-0.2.12/saa6752hs.h
saa7134-0.2.12/ir-kbd-i2c.c
saa7134-0.2.12/Makefile
saa7134-0.2.12/Make.config
saa7134-0.2.12/linux
saa7134-0.2.12/media
saa7134-0.2.12/.tmp_versions/
saa7134-0.2.12/.tmp_versions/video-buf.mod
saa7134-0.2.12/.tmp_versions/v4l1-compat.mod
saa7134-0.2.12/.tmp_versions/v4l2-common.mod
saa7134-0.2.12/.tmp_versions/saa7134.mod
saa7134-0.2.12/.tmp_versions/saa6752hs.mod
saa7134-0.2.12/.tmp_versions/ir-common.mod
saa7134-0.2.12/.tmp_versions/tuner.mod
saa7134-0.2.12/.tmp_versions/tda9887.mod
saa7134-0.2.12/.tmp_versions/msp3400.mod
saa7134-0.2.12/.tmp_versions/tvaudio.mod
saa7134-0.2.12/.tmp_versions/tvmixer.mod
saa7134-0.2.12/.tmp_versions/ir-kbd-i2c.mod


Still no joy though, curses!!!

---

### Post by crispy_420 on 2007-04-19
First of all this is not an issue with your tv tuner card. You got that error on launching tvtime due to a video card driver issue. To sum it up, set up you graphics card and it will work. Tvtime is wanting to set it's output format and your video drivers won't let it. If you have an ATI card I can help.

Don't worry about saaXXXX driver, they are part of kernel now. So don't wate time with tv driver.

---

### Post by harmony on 2007-04-19
have a look at this wiki, its for gentoo but there is some helpfull information there [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134) your card and tuner might be in the lists there.
Its a matter of finding the right card and tuner and then adding a line in /etc/modprobe.d/saa7134
options saa7134 card=xx  tuner=xx

---

### Post by eekfonky on 2007-04-19
I have on board graphics, no separate card. How do I check this to give you any relevant or useful information?

---

### Post by reclusivemonkey on 2007-04-19
As I mentioned before, I am not sure that your TV card will work with your graphics cards. I think you would be much better off simply getting a stand alone AGP/PCI graphics card. You should be able to pick one up for about £25/$15. You would also be able to run Beryl then as well =]

However, on the subject of identifying your TV card, you may find this site useful;

[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

Good luck.

---

### Post by Evil_Ether on 2007-04-20
> **crispy_420 said:**
> First of all this is not an issue with your tv tuner card. You got that error on launching tvtime due to a video card driver issue. To sum it up, set up you graphics card and it will work. Tvtime is wanting to set it's output format and your video drivers won't let it. If you have an ATI card I can help.

Don't worry about saaXXXX driver, they are part of kernel now. So don't wate time with tv driver.

I am having the same problem and am using an ATI Radeon X1600 with the ATI drivers installed via the restricted driver manager. If you could help me it would be much appreciated.

I have just installed Feisty 64bit and tvtime. when I run tvtime in a terminal i get the same error as the original poster.

$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/evilether/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/evilether/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

My Tuner card from lspci
01:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)

---

### Post by reclusivemonkey on 2007-04-20
Did you try the solution offered in the error message?

---

### Post by Evil_Ether on 2007-04-20
> **reclusivemonkey said:**
> Did you try the solution offered in the error message?

that will teach me to do this after a long week of work.
no I didn't. I will go and try that now.

Thanks for the fast reply.

*EDIT*
It seems that gatos is the driver for ATI capture cards. My tv tuner card is a "Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)" it is my video card that is ATI. 

Does this mean that my tv tuner card is not installed proply yet?

---

### Post by reclusivemonkey on 2007-04-20
> **Evil_Ether said:**
> that will teach me to do this after a long week of work.
no I didn't. I will go and try that now.

Thanks for the fast reply.

No problem. The link actually has a missing "r"; it should be 

[http://gatos.sourceforge.net/](http://gatos.sourceforge.net/)

I'll alert the TVTime author.

---

### Post by eekfonky on 2007-05-02
Ok, went out and bought a graphics card, tvtime now opens, but I can't find out how to tune in the channels, I checked the tvtime website but it wasn't very helpful, any ideas?

Cheers

---

### Post by reclusivemonkey on 2007-05-02
> **eekfonky said:**
> Ok, went out and bought a graphics card, tvtime now opens, but I can't find out how to tune in the channels, I checked the tvtime website but it wasn't very helpful, any ideas?


The tuning is very simple, just follow the on screen menu. Give it the right info (i.e. PAL/NTSC) and region and it "just works".

[http://tvtime.sourceforge.net/usage.html#configure](http://tvtime.sourceforge.net/usage.html#configure)

---

### Post by eekfonky on 2007-05-03
no joy, when I right click a menu appears, I have configured PAL but bothing, just a black screen....this is driving me mad!!

Help, please....anyone

---

### Post by eekfonky on 2007-05-25
Still nothing it's apparently a Philips Semiconductor  SAA7130 - I just want it to work is there anyone out there??

Hello

When I type $dsmeg:
[   18.903831]       .text : 0xc0100000 - 0xc02f8b15   (2018 kB)
[   18.903837] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.963897] Calibrating delay using timer specific routine.. 3409.77 BogoMIPS (lpj=1704887)
[   18.963983] Security Framework v1.0.0 initialized
[   18.963995] SELinux:  Disabled at boot.
[   18.964029] Mount-cache hash table entries: 512
[   18.964312] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   18.964336] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   18.964341] CPU: L2 cache: 128K
[   18.964345] CPU: Hyper-Threading is disabled
[   18.964348] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00003080 00000000 00000000 00000000
[   18.964370] Compat vDSO mapped to ffffe000.
[   18.964376] Remapping vsyscall page to ffffe000
[   18.964398] Checking 'hlt' instruction... OK.
[   18.968095] SMP alternatives: switching to UP code
[   18.968434] Freeing SMP alternatives: 9k freed
[   18.968752] Early unpacking initramfs... done
[   19.478861] ACPI: Core revision 20060707
[   19.487028] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.489514] ACPI: setting ELCR to 0200 (from 0c20)
[   19.492312] CPU0: Intel(R) Celeron(R) CPU 1.70GHz stepping 03
[   19.492324] SMP motherboard not detected.
[   19.492328] Local APIC not detected. Using dummy APIC emulation.
[   19.492419] Brought up 1 CPUs
[   19.492929] Booting paravirtualized kernel on bare hardware
[   19.493163] Time: 17:07:20  Date: 04/25/107
[   19.493227] NET: Registered protocol family 16
[   19.493478] EISA bus registered
[   19.493493] ACPI: bus type pci registered
[   19.535010] PCI: PCI BIOS revision 2.10 entry at 0xfb3a0, last bus=1
[   19.535015] PCI: Using configuration type 1
[   19.535018] Setting up standard PCI resources
[   19.552635] ACPI: Interpreter enabled
[   19.552644] ACPI: Using PIC for interrupt routing
[   19.554199] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.554209] PCI: Probing PCI hardware (bus 00)
[   19.554322] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   19.554894] Enabling SiS 96x SMBus.
[   19.555746] Boot video device is 0000:01:00.0
[   19.555889] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.592454] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[   19.593060] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   19.593645] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   19.594310] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[   19.594936] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 14 15)
[   19.595521] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 14 15)
[   19.596144] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   19.596732] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 14 15)
[   19.603654] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.603696] pnp: PnP ACPI init
[   19.612719] pnp: PnP ACPI: found 14 devices
[   19.612757] PnPBIOS: Disabled by ACPI PNP
[   19.612928] PCI: Using ACPI for IRQ routing
[   19.612937] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.648785] NET: Registered protocol family 8
[   19.648789] NET: Registered protocol family 20
[   19.650807] PCI: Bridge: 0000:00:01.0
[   19.650813]   IO window: disabled.
[   19.650823]   MEM window: e0000000-e1ffffff
[   19.650830]   PREFETCH window: d8000000-dfffffff
[   19.650914] NET: Registered protocol family 2
[   19.660803] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   19.661006] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   19.661266] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[   19.661447] TCP: Hash tables configured (established 16384 bind 8192)
[   19.661455] TCP reno registered
[   19.663917] checking if image is initramfs... it is
[   20.634403] Freeing initrd memory: 6867k freed
[   20.635447] audit: initializing netlink socket (disabled)
[   20.635487] audit(1180112841.025:1): initialized
[   20.635929] VFS: Disk quotas dquot_6.5.1
[   20.635982] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.636095] io scheduler noop registered
[   20.636103] io scheduler anticipatory registered
[   20.636107] io scheduler deadline registered
[   20.636135] io scheduler cfq registered (default)
[   20.636747] isapnp: Scanning for PnP cards...
[   20.993216] isapnp: No Plug & Play device found
[   21.159942] Real Time Clock Driver v1.12ac
[   21.160156] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.160420] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.161010] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   21.163253] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.164142] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   21.165139] mice: PS/2 mouse device common for all mice
[   21.167406] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.167847] input: Macintosh mouse button emulation as /class/input/input0
[   21.168058] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.168067] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.168612] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.169025] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.169218] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.169534] EISA: Probing bus 0 at eisa.0
[   21.169549] Cannot allocate resource for EISA slot 1
[   21.169583] EISA: Detected 0 cards.
[   21.187233] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.199718] TCP cubic registered
[   21.199742] NET: Registered protocol family 1
[   21.199788] Using IPI No-Shortcut mode
[   21.199885] Time: tsc clocksource has been installed.
[   21.200007] ACPI: (supports S0 S1 S4 S5)
[   21.200103]   Magic number: 7:739:138
[   21.200924] Freeing unused kernel memory: 328k freed
[   22.703534] Capability LSM initialized
[   22.802131] ACPI: Fan [FAN] (on)
[   22.814916] ACPI: Thermal Zone [THRM] (49 C)
[   24.264462] usbcore: registered new interface driver usbfs
[   24.264525] usbcore: registered new interface driver hub
[   24.264618] usbcore: registered new device driver usb
[   24.266304] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.266758] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[   24.266767] PCI: setting IRQ 10 as level-triggered
[   24.266772] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   24.266801] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   24.267065] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   24.267100] ohci_hcd 0000:00:02.2: irq 10, io mem 0xe3003000
[   24.329543] usb usb1: configuration #1 chosen from 1 choice
[   24.329610] hub 1-0:1.0: USB hub found
[   24.329633] hub 1-0:1.0: 3 ports detected
[   24.350582] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.430745] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   24.430754] PCI: setting IRQ 11 as level-triggered
[   24.430760] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   24.430789] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   24.430867] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   24.430896] ohci_hcd 0000:00:02.3: irq 11, io mem 0xe3000000
[   24.472691] Floppy drive(s): fd0 is 1.44M
[   24.483211] usb usb2: configuration #1 chosen from 1 choice
[   24.483282] hub 2-0:1.0: USB hub found
[   24.483304] hub 2-0:1.0: 3 ports detected
[   24.580173] FDC 0 is a post-1991 82077
[   24.586536] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   24.586565] SIS5513: chipset revision 208
[   24.586570] SIS5513: not 100% native mode: will probe irqs later
[   24.586602] SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
[   24.586624]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   24.586648]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   24.586663] Probing IDE interface ide0...
[   24.849478] hda: ExcelStor Technology J240, ATA DISK drive
[   25.104018] hdb: HDS728080PLAT20, ATA DISK drive
[   25.155280] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   25.174677] Probing IDE interface ide1...
[   25.997463] hdc: HITACHI DVD-ROM GD-2500, ATAPI CD/DVD-ROM drive
[   26.710181] hdd: ARTEC WRR-4048 1.00 20020510, ATAPI CD/DVD-ROM drive
[   26.820001] ide1 at 0x170-0x177,0x376 on irq 15
[   26.895858] SCSI subsystem initialized
[   26.908079] libata version 2.20 loaded.
[   26.920003] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   26.920010] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[   26.924906] 8139too Fast Ethernet driver 0.9.28
[   26.926192] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   26.926200] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   26.927076] eth0: RealTek RTL8139 at 0xe0854000, 00:04:61:42:68:78, IRQ 11
[   26.927083] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   26.956363] hda: max request size: 128KiB
[   26.986568] hda: 80418240 sectors (41174 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
[   26.988055] hda: cache flushes supported
[   26.988152]  hda: hda1 hda2 < hda5 >
[   27.021306] hdb: max request size: 512KiB
[   27.022723] hdb: 160836480 sectors (82348 MB) w/1719KiB Cache, CHS=16383/255/63, UDMA(100)
[   27.022918] hdb: cache flushes supported
[   27.022997]  hdb: hdb1 hdb2
[   27.167552] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[   27.167570] Uniform CD-ROM driver Revision: 3.20
[   27.522606] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   27.533744] Attempting manual resume
[   27.533752] swsusp: Resume From Partition 3:5
[   27.533756] PM: Checking swsusp image.
[   27.570522] PM: Resume from disk failed.
[   27.627402] kjournald starting.  Commit interval 5 seconds
[   27.627434] EXT3-fs: mounted filesystem with ordered data mode.
[   38.431218] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   40.035056] NET: Registered protocol family 17
[   41.248368] Linux agpgart interface v0.102 (c) Dave Jones
[   41.904958] agpgart: Detected SiS 650 chipset
[   41.927476] agpgart: AGP aperture is 128M @ 0xd0000000
[   41.936930] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.024620] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.103271] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1080
[   42.480829] Linux video capture interface: v2.00
[   42.859972] saa7130/34: v4l2 driver version 0.2.14 loaded
[   42.860164] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   42.860183] saa7130[0]: found at 0000:00:0a.0, rev: 1, irq: 11, latency: 32, mmio: 0xe3001000
[   42.860194] saa7134: <rant>
[   42.860195] saa7134:  Congratulations!  Your TV card vendor saved a few
[   42.860197] saa7134:  cents for a eeprom, thus your pci board has no
[   42.860199] saa7134:  subsystem ID and I can't identify it automatically
[   42.860201] saa7134: </rant>
[   42.860202] saa7134: I feel better now.  Ok, here are the good news:
[   42.860204] saa7134: You can use the card=<nr> insmod option to specify
[   42.860206] saa7134: which board do you have.  The list:
[   42.860211] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   42.860217] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   42.860226] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   42.860235] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   42.860243] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   42.860249] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   42.860256] saa7134:   card=6 -> Tevion MD 9717                          
[   42.860261] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   42.860269] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   42.860276] saa7134:   card=9 -> Medion 5044                             
[   42.860281] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   42.860286] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   42.860292] saa7134:   card=12 -> Medion 7134                              16be:0003
[   42.860299] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   42.860304] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   42.860311] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   42.860317] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   42.860327] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   42.860334] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   42.860339] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   42.860345] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   42.860352] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   42.860358] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   42.860365] saa7134:   card=23 -> BMK MPEX Tuner                          
[   42.860370] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   42.860376] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   42.860383] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   42.860390] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   42.860395] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[   42.860401] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   42.860408] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   42.860415] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   42.860421] saa7134:   card=32 -> AVACS SmartTV                           
[   42.860426] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   42.860432] saa7134:   card=34 -> Noval Prime TV 7133                     
[   42.860437] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   42.860443] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   42.860450] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   42.860454] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   42.860461] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   42.860468] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   42.860475] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   42.860481] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   42.860486] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   42.860491] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   42.860496] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   42.860502] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   42.860508] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   42.860515] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   42.860521] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   42.860528] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   42.860534] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   42.860541] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   42.860548] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   42.860555] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 1489:0214 5168:0304
[   42.860564] saa7134:   card=55 -> LifeView FlyDVB-T DUO                    5168:0306
[   42.860571] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   42.860577] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   42.860583] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   42.860594] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   42.860599] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   42.860609] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   42.860615] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   42.860620] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   42.860625] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   42.860631] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   42.860636] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   42.860641] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   42.860648] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   42.860654] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   42.860660] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   42.860667] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   42.860673] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   42.860680] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   42.860686] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   42.860693] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   42.860699] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   42.860705] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   42.860712] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4876
[   42.860721] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   42.860727] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   42.860733] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   42.860740] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   42.860746] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   42.860753] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   42.860759] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   42.860767] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   42.860775] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   42.860781] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   42.860788] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   42.860794] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[   42.860801] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   42.860807] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   42.860814] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   42.860820] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[   42.860828] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   42.860834] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   42.860842] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   42.860850] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   42.860856] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   42.860863] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   42.860869] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   42.860876] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   42.860883] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   42.860889] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   42.860895] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   42.860903] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   42.860927] saa7130[0]: board init: gpio is 38500
[   43.052686] saa7130[0]: Huh, no eeprom present (err=-5)?
[   43.052835] saa7130[0]: registered device video0 [v4l2]
[   43.052935] saa7130[0]: registered device vbi0
[   43.071870] input: PC Speaker as /class/input/input2
[   43.086465] parport: PnPBIOS parport detected.
[   43.086558] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.150900] nvidia: module license 'NVIDIA' taints kernel.
[   43.431172] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   43.431182] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   43.431663] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   43.589138] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   43.716159] saa7134 ALSA driver for DMA sound loaded
[   43.716218] saa7130[0]/alsa: saa7130[0] at 0xe3001000 irq 11 registered as card -2
[   43.915564] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[   43.915575] PCI: setting IRQ 5 as level-triggered
[   43.915580] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[   44.225508] intel8x0_measure_ac97_clock: measured 50918 usecs
[   44.225516] intel8x0: clocking to 48000
[   44.622283] lp0: using parport0 (interrupt-driven).
[   44.680316] fuse init (API version 7.8)
[   44.766918] Adding 1502036k swap on /dev/disk/by-uuid/4baff313-4c36-4388-9c46-9f8e8e22acb5.  Priority:-1 extents:1 across:1502036k
[   44.856978] EXT3 FS on hda1, internal journal
[   45.162241] NET: Registered protocol family 10
[   45.162462] lo: Disabled Privacy Extensions
[   53.034577] input: Power Button (FF) as /class/input/input4
[   53.044012] ACPI: Power Button (FF) [PWRF]
[   53.106892] input: Power Button (CM) as /class/input/input5
[   53.116263] ACPI: Power Button (CM) [PWRB]
[   53.152165] Using specific hotkey driver
[   53.197607] No dock devices found.
[   53.284324] ibm_acpi: ec object not found
[   53.491977] pcc_acpi: loading...
[   55.567098] eth0: no IPv6 routers present
[   60.384769] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   60.385396] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   60.386036] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   61.719726] ppdev: user-space parallel port driver
[   67.717219] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   67.717796] apm: overridden by ACPI.
[   72.592734] ip_tables: (C) 2000-2006 Netfilter Core Team
[   73.006915] Netfilter messages via NETLINK v0.30.
[   73.036733] nf_conntrack version 0.5.0 (4095 buckets, 32760 max)
[   75.603096] eth0: no IPv6 routers present
[   77.433087] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   77.612254] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   77.624406] NFSD: starting 90-second grace period
[   82.323487] Bluetooth: Core ver 2.11
[   82.323640] NET: Registered protocol family 31
[   82.323646] Bluetooth: HCI device and connection manager initialized
[   82.323652] Bluetooth: HCI socket layer initialized
[   82.401076] Bluetooth: L2CAP ver 2.8
[   82.401086] Bluetooth: L2CAP socket layer initialized
[   82.479562] Bluetooth: RFCOMM socket layer initialized
[   82.479590] Bluetooth: RFCOMM TTY layer initialized
[   82.479594] Bluetooth: RFCOMM ver 1.8
[  808.332642] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=202.56.7.164 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=1751 DF PROTO=TCP SPT=3023 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[  811.431855] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=202.56.7.164 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=1829 DF PROTO=TCP SPT=3023 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[  817.320037] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=202.56.7.164 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=2017 DF PROTO=TCP SPT=3023 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1569.080804] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=88.160.108.142 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=8403 DF PROTO=TCP SPT=1608 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1571.993607] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=88.160.108.142 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=8413 DF PROTO=TCP SPT=1608 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1578.018529] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=88.160.108.142 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=8437 DF PROTO=TCP SPT=1608 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2881.098251] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=88.109.213.0 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=3440 DF PROTO=TCP SPT=3030 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2884.040070] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=88.109.213.0 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=3531 DF PROTO=TCP SPT=3030 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2889.965631] Inbound IN=eth0 OUT= MAC=00:04:61:42:68:78:00:11:f5:f7:79:09:08:00 SRC=88.109.213.0 DST=192.168.1.3 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=3726 DF PROTO=TCP SPT=3030 DPT=44941 WINDOW=16384 RES=0x00 SYN URGP=0 
chris@chris-desktop:~$

---

### Post by fenian on 2007-05-25
A few questions....

Phillips SAA7130 is the name of the chipset on the card do you know the manufaturer of the card itself?

How are you connecting to your TV source (Antennae,direct cable,or settop cable/sat. box)?

What kind of connection is it (Svideo,RCA,coax)?

---

### Post by eekfonky on 2007-05-25
It's an "Easy TV capture" off of ebay a cheap generic card I think?

The Source is an antennae and the Connection is coax. I know it all worked as it worked with Windows XP but I'm not going back to that just to watch TV!!

Thanks

---

### Post by fenian on 2007-05-25
I think you have to set some things manually.First remove some settings...

> sudo rmmod saa7134-alsa
sudo rmmod saa7134

Then you need to install some setting...
> 
sudo modprobe saa7134 card=#tuner#

You need to replace the # signs with numbers that correnspond to your card.The tricky part is we don't know which card that is.We can look at this [list]("http://ubuntuforums.org/showthread.php?t=423005&highlight=modprobe+SAA7130") as a reference.Basically you will have to enter numbers until you find the right combo.[Here is a link to somebody who solved a similiar problem.]("http://ubuntuforums.org/showthread.php?t=423005&highlight=modprobe+SAA7130")

---

### Post by super breadfish on 2007-05-26
If it's any help, feel free to look through my thread here: [http://ubuntuforums.org/showthread.php?t=405327](http://ubuntuforums.org/showthread.php?t=405327)

What is happening is Linux can't identify what type of TV card and tuner you have. The cards usually have this information on chip inside them, but a lot of the cheaper cards don't have this.

What you need to do is find the right card and tuner number. You can either do this by Googling for other users who have your card running user Linux, as I did, or through guesswork. If you have to resort to guesswork, there are a few scripts that you could try which will flick through one by one (see my thread) and check them with TVtime.

---

### Post by eekfonky on 2007-05-27
If only i could find the card number, tried google and didn't come up with any good answers.
Basically you say if I can find the number I can install the damn thing?

Tried numbers 61, 69 and 81 under a list I found of tv card numbers. Should I start at 0 and just work my up until tvtime just automatically works?

---

### Post by super breadfish on 2007-05-29
> **eekfonky said:**
> Tried numbers 61, 69 and 81 under a list I found of tv card numbers. Should I start at 0 and just work my up until tvtime just automatically works?

Unfortunately, yes. You can try the script in my thread, or do it by hand. Just change the card and tuner number and test with TVtime for each one. Run tvtime-scanner from the terminal if you want, that will flick through each frequency and tell you if there is a signal, then add the ones to the TVtime list.
Make sure you flick through all the channels too, as the channels TVtime finds are often between channels 80 and 100, at least on my card. You can soon renumber them though.

It's time consuming, but apart from dual booting there isn't much option, unless you want to buy another card. Is there any documentation with the card, booklets, install cds etc? Any names might help narrow down which card to try.

EDIT: I've done some reading, and I think the Easy TV Capture is card number 2. I don't know about the tuner number though. Apparently it's often on the card itself, so you might have to open up your box and have a look.

---

### Post by eekfonky on 2007-05-29
I was looking at the WIndows driver cd and it says to go to this webpage if the drivr doesn't work, however, I fear it's a Windows driver and of no use, here it is anyway:

Please find below the link to the driver. 



- Drivers can cause some problems with different motherboard configurations. The

Phillips 7130 chipset is the best but please but ONLY if the driver on the CD

does not work please try the alternative driver on:



[http://www.innovico-jsy.com/Downloads/TV](http://www.innovico-jsy.com/Downloads/TV) PCI TUNER CARD/



- Missing Serial number for software - The serial number for the software may on

a sticker on the back of the card starting with S/N. If not there and you bought

the product before 1st Nov 2006 Try 8PKD3IFQRV28AYS

---

### Post by josesanders on 2007-05-29
I posted a HOWTO about the problem you seem to be having:

[http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

As it says when you run the command 'dmesg', your card can't be automatically detected:

> [ 42.860195] saa7134: Congratulations! Your TV card vendor saved a few
[ 42.860197] saa7134: cents for a eeprom, thus your pci board has no
[ 42.860199] saa7134: subsystem ID and I can't identify it automatically

Just follow the HOWTO.  I included the script by "super breadfish" there.

---

### Post by eekfonky on 2007-05-29
tried the script in a terminal (I don't know where else to run it) and I got the following message all 69 times:

ERROR: Module saa7134_alsa does not exist in /proc/modules
ERROR: Module saa7134 does not exist in /proc/modules
FATAL: Error inserting saa7134 (/lib/modules/2.6.20-16-lowlatency/kernel/drivers/media/video/saa7134/saa7134.ko): Operation not permitted
FATAL: Error running install command for saa7134
Actual card is: 0
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/chris/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Thank you for using tvtime.
ERROR: Module saa7134_alsa does not exist in /proc/modules
ERROR: Module saa7134 does not exist in /proc/modules
FATAL: Error inserting saa7134 (/lib/modules/2.6.20-16-lowlatency/kernel/drivers/media/video/saa7134/saa7134.ko): Operation not permitted
FATAL: Error running install command for saa7134
Actual card is: 1

Where the "Actual Card is" went from 0-69

---

### Post by cblanquer on 2007-05-29
I had an ASUS TV card based on the same chip working on U6.10. 
Now when installing U7.04 I replaced it by another card with a different chip (Hauppauge).

The point is that my new card was not working under tvtime (analogic receiver) but after installing the DVB-T drivers (digital receiver for digital terrestial TV broadcast)  I could perfectly access the DVB-T broadcasts using Kaffeine (the Kubuntu player one can install from Synaptic).

If you are in an area receiving them and your antenna is able you could try this alternative.

---

### Post by eekfonky on 2007-05-30
in the stix here, no terrestrial digital TV until 2008!!

---

### Post by reclusivemonkey on 2007-05-30
> **eekfonky said:**
> in the stix here, no terrestrial digital TV until 2008!!

Pah, out here in the stix, no digital till 2011! =[ I have my digital tv card that I got for £7 ready and waiting to slot into the HTPC for MythTV ggggrrrrr....

---

### Post by eekfonky on 2007-05-30
so does anyone know what I can do? or am I up sh*t creek without a paddle?

---

### Post by josesanders on 2007-05-31
Did you run the script as root?

You should run it with something like this:
$ sudo ./scriptname

What happens if you just run the following command:

$ sudo modprobe saa7134 card=2

---

### Post by eekfonky on 2007-06-01
First of all I don't know how to create a script. What do I use? a terminal, what?
Second when I type:
sudo modprobe saa7134 card=2 into a terminal nothing happens.

---

### Post by josesanders on 2007-06-01
> Second when I type:
sudo modprobe saa7134 card=2 into a terminal nothing happens.

If nothing happens, that means that the module was successfully loaded.  If it weren't, there would be an error message.  All the script does, in essence, is run that command over and over again with a different card number each time, then run TVTime so that you can see if it works.

> First of all I don't know how to create a script. What do I use? a terminal, what?

To create the script, open a terminal.  Then, create a new file, called say cardscript:

$ touch cardscript

Then edit the file:
$ gedit cardscript

Paste this into the file, then save and exit:
> #/bin/sh
MAXTUNER=69
i=0

while [ $i -lt $MAXTUNER ];
do
  rmmod saa7134_alsa saa7134
  modprobe saa7134 card=$i
  echo "Actual card is:" $i
  sleep 1 # this is to make sure /dev/video is registered when tvtime starts
  tvtime
  i=$(($i+1))
done

Then go back to the terminal, and change the permissions to make the file executable:
$ chmod 755 cardscript

Then execute it:
$ ./cardscript

What will happen is the script will load the driver with card number 1, display the card number on the command line, then open TVTime.  When TVTime opens, see if you get channels.  Make sure that you are using the television input, and not SVideo (you do that by right-clicking and selecting the input).  If you don't get anything, just close TVTime, and the script will automatically unload the driver, then reload it with the next card number and open TVTime again.  If you get channels in TVTime, all you have to do is go back to the terminal (without closing TVTime), make note of the current card number (that is the one you want to use, obviously), then press CTRL+C to stop the script.  TVTime will close, but the correct driver should still be loaded.  Now, you want to make sure that the correct card number is loaded every time you boot your machine, so you need to edit the file /etc/modprobe.d/options by adding the following line:

Options saa7134 card=<card number>

where obiously <card number> is the card number that worked.

---

### Post by eekfonky on 2007-06-06
tvtime opens a quick blue flash appears then a black screen...tried 80 and still nothing
Curses!!!
Any ideas?

---

### Post by josesanders on 2007-06-06
When TVTime opens, are you able to switch inputs?  I believe that when it starts up, the video input is selected, so you need to right-click in the screen area and change the input to Television.  Alternatively, you can test it by hooking up a signal from a VCR or something to the video or SVideo input.  Even if you aren't able to tune channels, you should be able to get a signal from the video input.

---

### Post by Faust942 on 2007-06-07
Thank you so much! I found my card and it worked in TVTime. I have Composite1, Composite2, S-Video and Television. You had previously stated not to use S-Video, but I don't have the choice, since I don't use Cable.

My card is:
[47.380824] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138

Now how do I make it work in MythTV? It keeps says nothing in the Input Devices.

Please help I'd like to watch some TV soon. :)

---

### Post by josesanders on 2007-06-07
I should warn you that I've never been able to get my saa7134 card to work properly with MythTV.  You should at least be able to get MythTV to use the card, but I can't guarantee that it will work properly.

When you say that MythTV says nothing in the input devices, have you added the card?  You need to stop the backend:

$ sudo /etc/init.d/mythtv-backend stop

Then run the setup:

$ sudo mythtv-setup

If you run into trouble, let me know where specifically you get suck.

---

### Post by Faust942 on 2007-06-07
This is what I got:

sudo mythtv-setup
Password:
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-06-07 11:02:27.031 Using runtime prefix = /usr
2007-06-07 11:02:27.069 DPMS is active.
2007-06-07 11:02:27.380 New DB connection, total: 1
2007-06-07 11:02:27.414 Connected to database 'mythconverg' at host: localhost
2007-06-07 11:02:27.416 Total desktop dim: 1280x1024, with 1 screen[s].
2007-06-07 11:02:27.434 Using screen 0, 1280x1024 at 0,0
2007-06-07 11:02:27.451 Current Schema Version: 
2007-06-07 11:02:27.460 Newest Schema Version : 1160
2007-06-07 11:02:27.461 New DB connection, total: 2
2007-06-07 11:02:27.461 Connected to database 'mythconverg' at host: localhost
2007-06-07 11:02:27.462 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-06-07 11:02:27.463 New DB connection, total: 3
2007-06-07 11:02:27.463 Connected to database 'mythconverg' at host: localhost
2007-06-07 11:02:27.466 Told to create a NEW database schema, but the database
already has 5 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-06-07 11:02:27.466 Database Schema upgrade FAILED, unlocking.
2007-06-07 11:02:27.512 Total desktop dim: 1280x1024, with 1 screen[s].
2007-06-07 11:02:27.513 Using screen 0, 1280x1024 at 0,0
2007-06-07 11:02:27.569 Switching to square mode (G.A.N.T.)
2007-06-07 11:02:27.659 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-06-07 11:02:28.413 Joystick disabled.
2007-06-07 11:02:28.438 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'UP', 'Up Arrow', 'Up', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.442 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'DOWN', 'Down Arrow', 'Down', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.443 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'LEFT', 'Left Arrow', 'Left', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.444 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'RIGHT', 'Right Arrow', 'Right', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.445 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'SELECT', 'Select', 'Return,Enter,Space', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.447 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'ESCAPE', 'Escape', 'Esc', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.448 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'MENU', 'Pop-up menu', 'M', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.449 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'INFO', 'More information', 'I', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.450 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'PAGEUP', 'Page Up', 'PgUp', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.451 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'PAGEDOWN', 'Page Down', 'PgDown', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.452 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'PREVVIEW', 'Previous View', 'Home', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.453 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'NEXTVIEW', 'Next View', 'End', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.454 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'HELP', 'Help', 'F1', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.455 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', 'EJECT', 'Eject Removable Media', '', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.456 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '0', '0', '0', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.457 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '1', '1', '1', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.458 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '2', '2', '2', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.460 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '3', '3', '3', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.461 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '4', '4', '4', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.462 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '5', '5', '5', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.463 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '6', '6', '6', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.465 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '7', '7', '7', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.466 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '8', '8', '8', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.467 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '9', '9', '9', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:28.974 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-06-07 11:02:29.070 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-06-07 11:02:30.713 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'Language' AND hostname = 'FAUST' ;
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-06-07 11:02:30.714 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'Language', 'EN', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-06-07 11:02:30.716 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'Language' AND hostname = 'FAUST' ;
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-06-07 11:02:30.717 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'Language', 'EN', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-06-07 11:02:30.781 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'qt', 'DELETE', 'Delete', 'D', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:30.783 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'qt', 'EDIT', 'Edit', 'E', 'FAUST' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-06-07 11:02:56.735 DB Error (CaptureCard::fillSelections):
Query was:
SELECT cardid, cardtype, videodevice FROM capturecard WHERE hostname = 'FAUST' AND parentid='0'
Driver error was [2/1054]:
QMYSQL3: Unable to execute query
Database error was:
Unknown column 'parentid' in 'where clause'

2007-06-07 11:02:58.922 DB Error (DiSEqCDevTree::Load):
Query was:
SELECT diseqcid FROM capturecard WHERE cardid = 0
Driver error was [2/1054]:
QMYSQL3: Unable to execute query
Database error was:
Unknown column 'diseqcid' in 'field list'

2007-06-07 11:03:11.372 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:03:11.568 DB Error (CaptureCard::fillSelections):
Query was:
SELECT cardid, cardtype, videodevice FROM capturecard WHERE hostname = 'FAUST' AND parentid='0'
Driver error was [2/1054]:
QMYSQL3: Unable to execute query
Database error was:
Unknown column 'parentid' in 'where clause'

2007-06-07 11:03:30.324 Fetching lineups from Tribune Media Zap2It...
2007-06-07 11:03:30.348 Grabbing channel data
--11:03:30--  [http://datadirect.webservices.zap2it.com/tvlistings/xtvdService](http://datadirect.webservices.zap2it.com/tvlistings/xtvdService)
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [    <=>                              ] 21,161         7.08K/s             

11:03:34 (7.08 KB/s) - `-' saved [21161]

2007-06-07 11:03:34.864 New DB DataDirect connection
2007-06-07 11:03:34.954 Connected to database 'mythconverg' at host: localhost
2007-06-07 11:03:35.124 DataDirect: Your subscription expires on 22/06/07 05:15:05 AM
2007-06-07 11:03:35.125 DB Error (Updating DataDirect Status Message):
Query was:
UPDATE settings SET data ='Your subscription expires on 22/06/07 05:15:05 AM' WHERE value='DataDirectMessage'
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-06-07 11:03:35.288 DB Error (end_element):
Query was:
SELECT sourceid FROM videosource WHERE lineupid = '0005989:X'
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.videosource' doesn't exist

2007-06-07 11:03:39.235 DB Error (inserting row):
Query was:
INSERT INTO videosource (sourceid) VALUES (0);
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.videosource' doesn't exist

2007-06-07 11:03:39.236 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:03:39.237 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:03:39.237 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:03:39.238 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:03:39.239 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:03:39.239 DB Error (simpledbstorage update):
Query was:

No error type from QSqlError?  Strange...
2007-06-07 11:05:05.359 DB Error (checkStoragePaths):
Query was:
SELECT data FROM settings WHERE value='RecordFilePrefix' AND hostname = 'FAUST';
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

I eventually got out of Myth Setup by ESC. It asked me if I wanted to run the mythfillingdatabase or something. I cancelled.

Here is 2 screenshots of the various setup points in Myth.
[ATTACH]34625[/ATTACH]

[ATTACH]34626[/ATTACH]

---

### Post by josesanders on 2007-06-07
Apparantly the database is screwed up.  How did you install mythtv?  Did you follow a specific guide?  Is it too late to start over?

---

### Post by Faust942 on 2007-06-07
I installed it through Synaptic, by just marking Mythtv it came with all its dependencies.
Here is the [LINK]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O") to the site I got the instructions of installation from.

Do you want me to post my specific parts?

---

### Post by josesanders on 2007-06-07
I don't think it's a hardware problem, just a problem with the mythconverg database.  Since you obviously don't have any data in the database that you want to save, I recommend just recreating it from scratch:

This will delete the existing database:
$ mysqladmin -u root -p drop mythconverg

This recreates the database from the template:
$ mysql -u root -p < /usr/share/mythtv/sql/mc.sql

Then you should hopefully be able to run the setup again as I mentioned previously.  Let me know what happens.

---

### Post by Faust942 on 2007-06-07
Well I entered in what you had said, but I got a Access Denied. 

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

I entered my password right, but it still says Access Denied. So maybe I need to reset the password? How do I do that? I tried both Accessories>Terminal and System Tools>Root Terminal.

I should have added this before, but here is a screenshot if I click Yes on the Mythfiledatabase box. [ATTACH]34655[/ATTACH]

---

### Post by josesanders on 2007-06-07
Are you using the password from the file /etc/mythtv/mysql.txt?  Can you log into the database at all?  Try this:

$ mysql -u root -p mythconverg

If that lets you in, you can drop the database with:

mysql> drop database mythconverg;

If that works, try running the command again to create the database

EDIT:
If that doesn't work, I found this page about resetting the mysql password:
[http://www.tribalwar.com/forums/archive/t-448762.html](http://www.tribalwar.com/forums/archive/t-448762.html)

---

### Post by gkasinath on 2007-06-08
Hello all, 

In my very first try with TV tuner cards, I have had no success at all. I have the same problem as one of the other members.. no signal on tvtime. 

I have the saa7134 card and dmesg output suggested that the card=46. I tried the script with card=46 and tuner=$i, in vain. Ran the script for tvtime-scanner, and after 69 iterations, no signal everywhere.. :( 

Please advise.. I installed the AverMedia cardbus hybrid driver (that is my card, linux driver). I used alien to convert the .rpm for mandriva to .deb and installed that. 

At the moment, I have no idea what I m missing.. :(

Cheers
Gautham Kasinath

---

### Post by josesanders on 2007-06-09
In my experience, the tuner number is not important, changing the card number is what you need to do.  By using the "tuner=$i", your card number is the same every time.  I recommend using the script from my howto:

[http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

---

### Post by DaneM. on 2007-06-09
**@eekfonky** , I have the same chipset on my TV card - Phillips SAA7130. I solved my problem when I followed these steps:
 Open terminal and type this:
     ```
sudo nano /etc/modules
```
   This is for load module when booting. Then type
    ```
saa7134
```
   in that field, on first empty line and save changes pressing both CTRL+X, followed with letter Y and then hit ENTER. Return to terminal and type 
    ```
sudo nano /etc/modprobe.d/bttv
```
and paste this line into that open file
    ```
options saa7134 card=[COLOR="Red"]**3**[/COLOR] tuner=[COLOR="Red"]**2**[/COLOR]
```
and save changes again by pressing both CTRL+X, followed with letter Y and then hit ENTER. After that reboot your computer and start "tvtime" aplication and set "television" for source input and scan for TV channels. Buy yourself a pop-corn :popcorn: and enjoy in TV programme.

In case that your card have no signal - try to replace two numbers in last code line - marked with red color - with some other number. It works with that number [COLOR="Red"]3[/COLOR] and [COLOR="Red"]2[/COLOR] for my card (as its written in original instruction). Or you can type
  ```
dmesg
```
 into terminal to determine what number is for your card (if its recognized). Sorry for my bad English, I hope that you will solve your problem. Post reply if it works.

---

### Post by gkasinath on 2007-06-10
Hey Jose, 

Thanks for that tip. I discovered that E506 had card number 46, So, I kept the card number static and changes the tuner number. 

I will try just running the iteration through for card number instead of tuner. I dont seem to have bttv. How do I confirm if I ve got that? sudo apt-get install bttv was negative.

Cheers
Gautham Kasinath

---

### Post by stadt on 2007-06-10
My SAA7134 based TV-card works 'perfectly' in Feisty. 

Unfortunately I had to accept, that, as soon I activate the card, everywhere, where text can be inserted, I get a lot of '0000000' inserted - no it's not hickup of my keyboard - so the system gets completly unusable. Curiously this happens ~5 Min. after system was started and got worse by newer kernels (2.6.20-16.28 and 2.6.20-16.29)

After deactiving the SAA7134 the 'zero-ghostwriter' went away

---

### Post by josesanders on 2007-06-10
> 
Unfortunately I had to accept, that, as soon I activate the card, everywhere, where text can be inserted, I get a lot of '0000000' inserted - no it's not hickup of my keyboard - so the system gets completly unusable. Curiously this happens ~5 Min. after system was started and got worse by newer kernels (2.6.20-16.28 and 2.6.20-16.29)


Actually, that's happened to me before, when I didn't know which card to use and I was trying different card numbers.  There were just one or two card numbers that did that, so I I recommend you try a different card number.

---

### Post by stadt on 2007-06-10
> **josesanders said:**
>  I recommend you try a different card number.

Thanks for the hint. But it doesn't work. I used the card number from V4L for my card (Terratec Cinergy TV400 )  using a different card number gives no picture/sound. It's curious both linux and Dscaler on Windows (quite similar to tvtime, some of the deinterlacescalers in tvime are borrowed from dscaler) report as vendor id 1131=generic and ffff=unknown as product ID, but both work with the settings vendorID=153b (terratec) and productID=1142. No  I didn't test all current 94 card numbers....;)

I guess the malfunction is related to using a SMP Kernel due to a Intel Core2Duo

---

### Post by stadt on 2007-06-11
I have to say lots of thanks. Your suggestion pointed me to the right direction.

I have now a different card, an Anubis/Typhoon EasyLite CardNumber=2, TunerNumber=37. Works like a charm. The keyboard hickups, aka zero-ghostwriting, are gone. 

As this card correctly sets the ir-input, which is assigend to input/keyboard, input/button I'm rather shure now that the Terratec Cinergy TV400 ir-input was falsly configuerd and produced the zero's

---

### Post by josesanders on 2007-06-11
To Faust942:

I found this thread which seems to fix your database problem:

[http://ubuntuforums.org/showthread.php?t=416897](http://ubuntuforums.org/showthread.php?t=416897)

---

### Post by DrMega on 2007-06-11
> **stadt said:**
> I have to say lots of thanks. Your suggestion pointed me to the right direction.

I have now a different card, an Anubis/Typhoon EasyLite CardNumber=2, TunerNumber=37. Works like a charm. The keyboard hickups, aka zero-ghostwriting, are gone. 

As this card correctly sets the ir-input, which is assigend to input/keyboard, input/button I'm rather shure now that the Terratec Cinergy TV400 ir-input was falsly configuerd and produced the zero's

I have an saa7134 based TV card and despite loads of attempts, and searching on the net, and frustrating finding a couple of people who said they'd had it work, mine never worked so I gave up.

Do you know exactly what make/model the card was that wouldn't work? Mine is a Pinnacle 300i. I had thought about getting another card but didn't want the expense and the trouble if I was going to have the same lack of success.

---

### Post by stadt on 2007-06-11
> **DrMega said:**
> IDo you know exactly what make/model the card was that wouldn't work? 

Mine was a Terratec Cinergy TV 400 bought ~2years ago, seems a revision which differs from the supported Terratec Cinergy TV 400 (card=8, tuner=5), although nothing can be seen on the card itself to identify the revision.

Luckily I've made an agreement. If the Anubis/Typhoon card (without ir-sensor and remote-controller) works in my PC, the person from whom I got it for testing purpose, gets my Terratec ( with ir-sensor an remote-control) , as he only uses WinXP.

So a win-win situation and I hadn't to pay anything

---

### Post by david.rahrer on 2007-07-05
> **stadt said:**
> 
I have now a different card, an Anubis/Typhoon EasyLite CardNumber=2, TunerNumber=37. Works like a charm. The keyboard hickups, aka zero-ghostwriting, are gone. 


Can you tell me where I can get this card?  I can't find any links to buy it through Google.  I'm looking for a card under $100 that I can use to record occasional TV programs and I understand that Feisty works with more of them than Edgy, but I'm not finding a lot of recommendations.  I just want one that is the least bother, I'm not going to do anything fancy.  Thanks.

---

### Post by Faust942 on 2007-07-06
> **josesanders said:**
> To Faust942:

I found this thread which seems to fix your database problem:

[http://ubuntuforums.org/showthread.php?t=416897](http://ubuntuforums.org/showthread.php?t=416897)

Hey Jose,

Thanks for all the help, but for now I've given up on my search for a MythTV setup with my SAA7130 (Piece of crap is what it is...).

Whenever I have enough cash I'll try a Haupagge. I've heard that those are a good Linux-compatible brand.

Again thanks for the help :)

---

### Post by asmweb on 2007-07-06
Hello, I have an terratec usb tv card and i'm using ubuntu 7.04. Unfurtunately I can not make it work. When I plug the usb in there is no light turning on but on the other side when I do

$ lsusb
Bus 005 Device 003: ID 0ccd:003b TerraTec Electronic GmbH
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp.
Bus 001 Device 006: ID 413c:8105 Dell Computer Corp.
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

and as well I seem to have no dev/video0 as I get this from tvtime

videoinput: Cannot open capture device /dev/video0: No such file or directory

What am I missing...

thanks

---

### Post by ToTeB on 2007-07-10
i using Aver Go 007 too and have problems with remote control?
have any idea how to make remote avalaible ?

Thank you in advice.

---

### Post by stmiller on 2007-07-10
I wanted to add to this thread that I have a philips based PCI tv tuner card that is working in Feisty with no fuss. It's not a fantastic card, but it seems to work ok. I have a cheapo Nvidia 7300LE PCIe graphics card.

The tv card is an AlchemyTV DVR PCI card This is the product page:

[http://miglia.com/products/video/alchemytvdvr/](http://miglia.com/products/video/alchemytvdvr/)

It's a Mac OS X model, but is standard PCI so fits in my Shuttle box (AMD X2 box).

Uses saa7133/7134 driver built into kernel.

```
ir_common              34308  2 saa7134,ir_kbd_i2c
videodev               30336  1 saa7134
v4l2_common            28800  4 tuner,saa7134,compat_ioctl32,videodev
v4l1_compat            14980  2 saa7134,videodev

```

I did have to do this:

```

$ sudo chmod 775 /dev/video0

```

as the device was owned by root only at first.

---

### Post by sir_cheats_a_lot on 2007-10-10
hmm...glad i found this thread.  have a SAA7130 card myself, so far i have video on the TV input but no audio.  on the other inputs i have audio but no video.  im stuck with broadcast tv so i can really only use  one.   until now i haven't had a reason to upgrade from dapper to fiesty... so maybe i'll pop in the live cd and see if im as lucky as the rest of those reporting success...if i can't other wise get it working  via DaneM's suggestion.

---

### Post by josesanders on 2007-10-12
I don't think upgrading to Feisty will fix your problem.  For me, a lot of different card numbers worked for video, but only a few for audio.  I recommend just trying some different card numbers in the file /etc/modprobe.d/options, as explained earlier in this thread.

---

