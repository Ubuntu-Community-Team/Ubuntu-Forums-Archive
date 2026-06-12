---
title: "dialup **URGENT**"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by windows-killer on 2009-01-04
Am trying to get dialup working on ubuntu but am having some trouble
here is what I did:

1) downloaded gnomePPP all settings are current except my modem is not detected, tried all drop down menus and pressed the connect button but its not working

2) downloaded the appropriate driver (intel536ep-intrepid_3-Philippe.Vouters_i386.deb) for intel modem model 90/92V

3) driver installation was successful, went to gnomePPP and its not dectecting my analog modem.

what should I do?
your help is greatly appriciated!:p

---

### Post by dmizer on 2009-01-05
Try this link:
[https://help.ubuntu.com/community/DialupModemHowto#Download%20/%20Detect%20and%20Configure%20/%20Install](https://help.ubuntu.com/community/DialupModemHowto#Download%20/%20Detect%20and%20Configure%20/%20Install)

---

### Post by ranch hand on 2009-01-05
Most folks don't use dial up.  I will see if I can help.

First off, what kind of modem do you have?  Hardware or Winmodem?  Internal or External?

---

### Post by ranch hand on 2009-01-05
Another thing that I would like is the result of the command  lspci .  Just copy paste the bugger.  Lets see if we can find your modem.

---

### Post by windows-killer on 2009-01-05
btw I have a PCI modem and here is what I got:

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 03)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

---

### Post by ranch hand on 2009-01-05
This is real interesting.  You have a winmodem and a modem controler in different locations.

I assume you are dual booting, could you tell me with what and does the modem work there.  I see that there has been some issue with drivers for XP.

I have a fairly busy day today, the cows are out 10 miles from here and need sorted out and I have a frozen water source here to sort out.

I will be checking in as often as I pass the house here.

You will get a lot better service out of a hardware modem under any OS.  I changed the winmodem out of this box for a USR5610c and increased the speed by at least 25% and connection reliability by about 80%.  The winmodem would not stay connected well.  That was under Vista.  I never got it going under Ubuntu because the free drivers for conexant modems only give a 14k modem and that just seemed silly.

I think we can sort this out though, we will need some research on the controler and I am on that now.

---

### Post by ranch hand on 2009-01-05
Give a little info on your computer.  What are the specs and who made it.  Your controler is listed as supported, at least on some computers.

---

### Post by windows-killer on 2009-01-05
> **ranch hand said:**
> Give a little info on your computer.  What are the specs and who made it.  Your controler is listed as supported, at least on some computers.

my pc specs:
AMD athlon 64 2.2 GHZ (Overclocked)
1GB RAM 
80GB hard drive(Ubuntu)
60GB (Windows xp)
Graphics card: ATI 9250 pro 128MB Diretc X and 256MB OpenGL
DVD-RW DVD-RAM speed 24X LG
Modem: Intel 90V 92V (intel536ep)

I bought this computer in 2005, however it was build by an independent  computer store not dell, hp etc
I have the drivers for both ubuntu and xp but the modem is being detected only by xp.

ranch hand, thank you for your time:D

---

### Post by ranch hand on 2009-01-05
Why don't you try downloading scanModem and trying it.  I will admit that it did nothing for me but they have a new version and it might.

It is on the linmodem site which deals with connexant but it might be worth a try.  I would run a search for scanModem directly as the site is slow to navigate.  They have directions for using it when you are downloading in a dual boot.

It may tell us where your modem is to be detected by what needs to detect it.

---

### Post by ranch hand on 2009-01-05
I think I may be being silly or slow.  What port is the modem on in windows?  This will give us an Idea where to look in linux.

---

### Post by windows-killer on 2009-01-05
here are the results from scan modem and I apologyze for the length: 


CLASS=0703
NAME="Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI "
PCIDEV=8086:1080
SUBSYS=8086:100a
IRQ=17
HDA=
CodecDiagnosed=
slamrTest=
CodecClass=
IDENT=INTEL537EP
SLMODEMD_DEVICE=
OPTS=
Driver=
--------------------------------------------------------------------------

CLASS=0780
NAME="Communication controller: VIA Technologies, Inc. AC'97 Modem Controller "
PCIDEV=1106:3068
SUBSYS=none
IRQ=22
SOFT=1106:3068.MC97
CodecArchived=AGR02_possibly
HDA=
CodecDiagnosed=
slamrTest=
CodecClass=
IDENT=slmodemd
SLMODEMD_DEVICE=modem:1
OPTS=
Driver=snd-via82xx-modem
------------------------------------------------------------------------

--------------------------  System information ----------------------
CPU=i686,  
Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Dec 19 16:29:52 UTC 2008
 scanModem update of:  2009_01_03

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:


USB modems not recognized

For candidate card in slot 00:0c.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0c.0	8086:1080	8086:100a	Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 

 Modem interrupt assignment and sharing: 
 17:       7940   IO-APIC-fasteoi   eth0
 --- Bootup diagnostics for card in PCI slot 00:0c.0 ----
[    0.386795] PCI: 0000:00:0c.0 reg 10 32bit mmio: [fde00000, fde00fff]
[    0.386801] PCI: 0000:00:0c.0 reg 14 io port: [b000, b0ff]
[    0.386831] pci 0000:00:0c.0: PME# supported from D0 D3hot D3cold
[    0.386835] pci 0000:00:0c.0: PME# disabled
[    1.474093] serial 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.474448] 0000:00:0c.0: ttyS1 at I/O 0xb008 (irq = 17) is a 16450
[    1.474657] 0000:00:0c.0: ttyS2 at I/O 0xb010 (irq = 17) is a 8250
[    1.474865] 0000:00:0c.0: ttyS3 at I/O 0xb018 (irq = 17) is a 16450
[    1.474932] Couldn't register serial port 0000:00:0c.0: -28

 The PCI slot 00:0c.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

For candidate card in slot 00:11.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:11.6	1106:3068		Communication controller: VIA Technologies, Inc. AC'97 Modem Controller 

 Modem interrupt assignment and sharing: 
 22:        801   IO-APIC-fasteoi   VIA8237
 --- Bootup diagnostics for card in PCI slot 00:11.6 ----
[    0.387368] PCI: 0000:00:11.6 reg 10 io port: [0, ff]
[    0.396772] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396776] pnp 00:08: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396779] pnp 00:08: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396782] pnp 00:08: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396785] pnp 00:08: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396788] pnp 00:08: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396791] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396795] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396798] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396801] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396804] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396807] pnp 00:08: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396810] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[   14.799364] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   14.799459] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.556061] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   16.060239] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   16.060258] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13

 The PCI slot 00:11.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

PCIbus=00:11.6
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Flags: medium devsel, IRQ 22
	I/O ports at 1000 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-via82xx-modem


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.17
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-01: VIA 8237 : VIA 8237 : playback 1 : capture 1
00-00: VIA 8237 : VIA 8237 : playback 4 : capture 1

about /proc/asound/cards:
------------------------
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with AD1980 at 0xc800, irq 22
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:0c.0:
	Modem chipset  detected on
NAME="Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI "
CLASS=0703
PCIDEV=8086:1080
SUBSYS=8086:100a
IRQ=17
IDENT=INTEL537EP

 For candidate modem in:  00:0c.0
   0703 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 
      Primary device ID:  8086:1080
 Support type needed or chipset:	INTEL537EP
 

----------------end Softmodem section --------------


Predictive  diagnostics for card in bus 00:11.6:
	Modem chipset  detected on
NAME="Communication controller: VIA Technologies, Inc. AC'97 Modem Controller "
CLASS=0780
PCIDEV=1106:3068
SUBSYS=none
IRQ=22
SOFT=1106:3068.MC97
CodecArchived=AGR02_possibly
IDENT=slmodemd
SLMODEMD_DEVICE=modem:1
Driver=snd-via82xx-modem

 For candidate modem in:  00:11.6
   0780 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller 
      Primary device ID:  1106:3068
    Subsystem PCI_id  none 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: AGR02_possibly
                        
      

Support type needed or chipset:	slmodemd


 Pending fixes to gcc-4.3, temporarily use instead of SLMODEMD.gcc4.3.tar.gz, use
 	SLMODEMD_gcc4.2_alsa1.0.17.tar.gz

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-via82xx-modem
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD_gcc4.2_alsa1.0.17.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD_gcc4.2_alsa1.0.17.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.


Compressed files at: /usr/src/qc-usb.tar.bz2


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 ppp0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/10-local.rules:KERNEL=="536ep0", SYMLINK=="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

A modem device/card may be disabled at bootup, due to a variety of causes.
 Look at the bootup diagnostics record dmesg.txt  and try to garner some 
 understanding from it. Attach it to your query to  [email]discuss@linmodems.org[/email]
 Possibilities therein are too  diverse to be automagically processed by 
 scanModem. A line including the PCI
 bus slot 00:11.6 of your modem, and "disable" or "disabling" predicts problems,
 though sometimes corrected later in the bootup.  Similarly a line with "@"
 in the interrupt (IRQ) for your 00:11.6 slot is predictive of problems. 

 Possible corrections are:
 1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
 Instructions for accessing BIOS are at:
 [http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within:  Additional Resourcces.
 2a) Add an option "pci=routeirq" to the kernel boot up line.
 Here is an example paragraph from  /boot/grub/menu.lst :
       title           Ubuntu, kernel 2.6.15-26-686
       root            (hd0,6)
       kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
       initrd          /boot/initrd.img-2.6.15-26-686
       savedefault
 2b) Same as above, but use "pollirq" instead of "pci=routeirq".
 3) Within some BIOS setups, IRQ assignments can be changed.
 4) On non-laptop systems, moving the modem card to another slot has helped.
 5) Blacklist as many drivers as possible. See
         [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg01593.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg01593.html)
 6) Sometimes upgrading the kernel solves the problem.
 7) Sometimes downgrading the kernel solves the problem.
 8) Sometimes changing the Linux distribution solves the problem.
 9) Get unloading.gz from [http://linmodems.technion.ac.il/linmodems/](http://linmodems.technion.ac.il/linmodems/)
 This script unloads excess drivers which may be competing for resources. 
 Before trying to set up the modem, do:
 $ gunzip unloading.gz
 $ chmod +x unloading
 $ su - root 
 # ./unloading
 Or for Ubuntu related Distros
 $ sudo ./unloading
---------------------------------------------------------------------

           CPU0       
  0:        121   IO-APIC-edge      timer
  1:       5018   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge    
  8:          2   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:     211950   IO-APIC-edge      i8042
 14:      20444   IO-APIC-edge      pata_via
 15:      50971   IO-APIC-edge      pata_via
 16:     255625   IO-APIC-fasteoi   radeon@pci:0000:01:00.0
 17:       7940   IO-APIC-fasteoi   eth0
 20:          0   IO-APIC-fasteoi   sata_via
 21:          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5
 22:        801   IO-APIC-fasteoi   VIA8237
NMI:          0   Non-maskable interrupts
LOC:     251782   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Dec 19 16:29:52 UTC 2008 (Ubuntu 2.6.27-11.22-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3ff30 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781d000 - 37fef352
[    0.000000] ACPI: RSDP 000FAAC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF30000, 0030 (r1 A M I  OEMRSDT  10000409 MSFT       97)
[    0.000000] ACPI: FACP 3FF30200, 0081 (r1 A M I  OEMFACP  10000409 MSFT       97)
[    0.000000] ACPI: DSDT 3FF303E0, 362A (r1  A0091 A0091006        6 MSFT  100000D)
[    0.000000] ACPI: FACS 3FF40000, 0040
[    0.000000] ACPI: APIC 3FF30390, 004A (r1 A M I  OEMAPIC  10000409 MSFT       97)
[    0.000000] ACPI: OEMB 3FF40040, 003F (r1 A M I  OEMBIOS  10000409 MSFT       97)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fef352]          RAMDISK ==> [003781d000 - 0037fef352]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003ff30
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ff30
[    0.000000] On node 0 totalpages: 261823
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32273 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff80000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259520
[    0.000000] Kernel command line: root=UUID=6fc91425-38f9-44f2-b85c-133c7fe1e046 ro quiet splash vga=792 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2202.743 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1023924k/1047744k available (2576k kernel code, 22988k reserved, 1165k data, 424k init, 130240k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 4405.48 BogoMIPS (lpj=8810972)
[    0.004035] Security Framework initialized
[    0.004046] SELinux:  Disabled at boot.
[    0.004073] AppArmor: AppArmor initialized
[    0.004082] Mount-cache hash table entries: 512
[    0.004258] Initializing cgroup subsys ns
[    0.004262] Initializing cgroup subsys cpuacct
[    0.004264] Initializing cgroup subsys memory
[    0.004280] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004282] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004298] Checking 'hlt' instruction... OK.
[    0.020428] SMP alternatives: switching to UP code
[    0.025273] Freeing SMP alternatives: 11k freed
[    0.025277] ACPI: Core revision 20080609
[    0.026648] ACPI: Checking initramfs for custom DSDT
[    0.332537] ENABLING IO-APIC IRQs
[    0.332852] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.372548] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[    0.376023] Brought up 1 CPUs
[    0.376023] Total of 1 processors activated (4405.48 BogoMIPS).
[    0.376023] CPU0 attaching NULL sched-domain.
[    0.376023] net_namespace: 840 bytes
[    0.376023] Booting paravirtualized kernel on bare hardware
[    0.376023] Time: 19:57:30  Date: 01/05/09
[    0.376023] NET: Registered protocol family 16
[    0.376023] EISA bus registered
[    0.376023] ACPI: bus type pci registered
[    0.376023] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.376023] PCI: Using configuration type 1 for base access
[    0.376023] ACPI: EC: Look up EC in DSDT
[    0.379907] ACPI: Interpreter enabled
[    0.379912] ACPI: (supports S0 S1 S3 S4 S5)
[    0.379927] ACPI: Using IOAPIC for interrupt routing
[    0.386563] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.386638] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.386696] pci 0000:00:01.0: supports D1
[    0.386728] PCI: 0000:00:0a.0 reg 10 32bit mmio: [fdd00000, fdd03fff]
[    0.386734] PCI: 0000:00:0a.0 reg 14 io port: [ec00, ecff]
[    0.386753] PCI: 0000:00:0a.0 reg 30 32bit mmio: [fdc00000, fdc1ffff]
[    0.386764] pci 0000:00:0a.0: supports D1
[    0.386766] pci 0000:00:0a.0: supports D2
[    0.386768] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.386772] pci 0000:00:0a.0: PME# disabled
[    0.386795] PCI: 0000:00:0c.0 reg 10 32bit mmio: [fde00000, fde00fff]
[    0.386801] PCI: 0000:00:0c.0 reg 14 io port: [b000, b0ff]
[    0.386831] pci 0000:00:0c.0: PME# supported from D0 D3hot D3cold
[    0.386835] pci 0000:00:0c.0: PME# disabled
[    0.386858] PCI: 0000:00:0f.0 reg 10 io port: [e800, e807]
[    0.386863] PCI: 0000:00:0f.0 reg 14 io port: [e400, e403]
[    0.386869] PCI: 0000:00:0f.0 reg 18 io port: [e000, e007]
[    0.386874] PCI: 0000:00:0f.0 reg 1c io port: [d800, d803]
[    0.386880] PCI: 0000:00:0f.0 reg 20 io port: [d400, d40f]
[    0.386885] PCI: 0000:00:0f.0 reg 24 io port: [d000, d0ff]
[    0.386932] PCI: 0000:00:0f.1 reg 20 io port: [fc00, fc0f]
[    0.386986] PCI: 0000:00:10.0 reg 20 io port: [b400, b41f]
[    0.387002] pci 0000:00:10.0: supports D1
[    0.387004] pci 0000:00:10.0: supports D2
[    0.387006] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.387009] pci 0000:00:10.0: PME# disabled
[    0.387041] PCI: 0000:00:10.1 reg 20 io port: [b800, b81f]
[    0.387058] pci 0000:00:10.1: supports D1
[    0.387059] pci 0000:00:10.1: supports D2
[    0.387061] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.387065] pci 0000:00:10.1: PME# disabled
[    0.387098] PCI: 0000:00:10.2 reg 20 io port: [c000, c01f]
[    0.387114] pci 0000:00:10.2: supports D1
[    0.387116] pci 0000:00:10.2: supports D2
[    0.387117] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.387121] pci 0000:00:10.2: PME# disabled
[    0.387153] PCI: 0000:00:10.3 reg 20 io port: [c400, c41f]
[    0.387169] pci 0000:00:10.3: supports D1
[    0.387171] pci 0000:00:10.3: supports D2
[    0.387173] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.387176] pci 0000:00:10.3: PME# disabled
[    0.387196] PCI: 0000:00:10.4 reg 10 32bit mmio: [fdf00000, fdf000ff]
[    0.387225] pci 0000:00:10.4: supports D1
[    0.387226] pci 0000:00:10.4: supports D2
[    0.387228] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.387232] pci 0000:00:10.4: PME# disabled
[    0.387280] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.387285] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.387315] PCI: 0000:00:11.5 reg 10 io port: [c800, c8ff]
[    0.387346] pci 0000:00:11.5: supports D1
[    0.387347] pci 0000:00:11.5: supports D2
[    0.387368] PCI: 0000:00:11.6 reg 10 io port: [0, ff]
[    0.387468] PCI: 0000:01:00.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.387473] PCI: 0000:01:00.0 reg 14 io port: [a000, a0ff]
[    0.387477] PCI: 0000:01:00.0 reg 18 32bit mmio: [fd600000, fd60ffff]
[    0.387486] PCI: 0000:01:00.0 reg 30 32bit mmio: [fd500000, fd51ffff]
[    0.387495] pci 0000:01:00.0: supports D1
[    0.387496] pci 0000:01:00.0: supports D2
[    0.387508] PCI: 0000:01:00.1 reg 10 32bit mmio: [e0000000, e7ffffff]
[    0.387512] PCI: 0000:01:00.1 reg 14 32bit mmio: [fd400000, fd40ffff]
[    0.387528] pci 0000:01:00.1: supports D1
[    0.387529] pci 0000:01:00.1: supports D2
[    0.387550] PCI: bridge 0000:00:01.0 io port: [a000, afff]
[    0.387554] PCI: bridge 0000:00:01.0 32bit mmio: [fd100000, fd6fffff]
[    0.387558] PCI: bridge 0000:00:01.0 32bit mmio pref: [d7f00000, f7efffff]
[    0.387564] bus 00 -> node 0
[    0.387570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.394325] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.394431] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.394535] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.394638] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.394742] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.394846] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.394950] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.395055] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.395197] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.395227] pnp: PnP ACPI init
[    0.395233] ACPI: bus type pnp registered
[    0.396772] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396776] pnp 00:08: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396779] pnp 00:08: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396782] pnp 00:08: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396785] pnp 00:08: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396788] pnp 00:08: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396791] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396795] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396798] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396801] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396804] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396807] pnp 00:08: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.396810] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.398256] pnp: PnP ACPI: found 12 devices
[    0.398258] ACPI: ACPI bus type pnp unregistered
[    0.398262] PnPBIOS: Disabled by ACPI PNP
[    0.398590] PCI: Using ACPI for IRQ routing
[    0.398698] NET: Registered protocol family 8
[    0.398698] NET: Registered protocol family 20
[    0.398698] NetLabel: Initializing
[    0.398698] NetLabel:  domain hash size = 128
[    0.398698] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.398698] NetLabel:  unlabeled traffic allowed by default
[    0.398698] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.398698]    actual entries 65620
[    0.398698] AppArmor: AppArmor Filesystem Enabled
[    0.398698] ACPI: RTC can wake from S4
[    0.398698] system 00:08: ioport range 0x295-0x296 has been reserved
[    0.398698] system 00:08: ioport range 0x3e1-0x3e7 has been reserved
[    0.398698] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.398698] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.398698] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.398698] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.398698] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.398698] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.398698] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.398698] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[    0.398698] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.398698] system 00:0b: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.434394] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.434398] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.434402] pci 0000:00:01.0:   MEM window: 0xfd100000-0xfd6fffff
[    0.434406] pci 0000:00:01.0:   PREFETCH window: 0x000000d7f00000-0x000000f7efffff
[    0.434420] pci 0000:00:01.0: setting latency timer to 64
[    0.434424] bus: 00 index 0 io port: [0, ffff]
[    0.434426] bus: 00 index 1 mmio: [0, ffffffff]
[    0.434428] bus: 01 index 0 io port: [a000, afff]
[    0.434430] bus: 01 index 1 mmio: [fd100000, fd6fffff]
[    0.434432] bus: 01 index 2 mmio: [d7f00000, f7efffff]
[    0.434434] bus: 01 index 3 mmio: [0, 0]
[    0.434446] NET: Registered protocol family 2
[    0.434564] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.434912] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.435980] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.436550] TCP: Hash tables configured (established 131072 bind 65536)
[    0.436554] TCP reno registered
[    0.436660] NET: Registered protocol family 1
[    0.436800] checking if image is initramfs... it is
[    0.936080] Switched to high resolution mode on CPU 0
[    1.079602] Freeing initrd memory: 8008k freed
[    1.080316] audit: initializing netlink socket (disabled)
[    1.080336] type=2000 audit(1231185451.080:1): initialized
[    1.085820] highmem bounce pool size: 64 pages
[    1.085826] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.087713] VFS: Disk quotas dquot_6.5.1
[    1.087792] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.087885] msgmni has been set to 1761
[    1.088014] io scheduler noop registered
[    1.088017] io scheduler anticipatory registered
[    1.088019] io scheduler deadline registered
[    1.088029] io scheduler cfq registered (default)
[    1.088040] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.088120] pci 0000:01:00.0: Boot video device
[    1.088403] isapnp: Scanning for PnP cards...
[    1.441833] isapnp: No Plug & Play device found
[    1.473216] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.473332] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.473963] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.474093] serial 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.474448] 0000:00:0c.0: ttyS1 at I/O 0xb008 (irq = 17) is a 16450
[    1.474657] 0000:00:0c.0: ttyS2 at I/O 0xb010 (irq = 17) is a 8250
[    1.474865] 0000:00:0c.0: ttyS3 at I/O 0xb018 (irq = 17) is a 16450
[    1.474932] Couldn't register serial port 0000:00:0c.0: -28
[    1.476666] brd: module loaded
[    1.476735] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.476850] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.477253] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.477258] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.477600] mice: PS/2 mouse device common for all mice
[    1.477721] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.477757] rtc0: alarms up to one year, y3k
[    1.477859] EISA: Probing bus 0 at eisa.0
[    1.477867] Cannot allocate resource for EISA slot 1
[    1.477892] EISA: Detected 0 cards.
[    1.477896] cpuidle: using governor ladder
[    1.477898] cpuidle: using governor menu
[    1.478350] TCP cubic registered
[    1.478379] Using IPI No-Shortcut mode
[    1.478539] registered taskstats version 1
[    1.478664]   Magic number: 9:800:1000
[    1.478795]  pnp1: hash matches
[    1.478801] rtc_cmos 00:02: hash matches
[    1.478855] rtc_cmos 00:02: setting system clock to 2009-01-05 19:57:31 UTC (1231185451)
[    1.478859] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.478861] EDD information not available.
[    1.479239] Freeing unused kernel memory: 424k freed
[    1.479294] Write protecting the kernel text: 2580k
[    1.479327] Write protecting the kernel read-only data: 940k
[    1.506915] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.546625] vesafb: framebuffer at 0xe8000000, mapped to 0xf8880000, using 4608k, total 16384k
[    1.546630] vesafb: mode is 1024x768x24, linelength=3072, pages=6
[    1.546633] vesafb: protected mode interface info at c000:577a
[    1.546636] vesafb: pmi: set display start = c00c580e, set palette = c00c585a
[    1.546638] vesafb: pmi: ports = a010 a016 a054 a038 a03c a05c a000 a004 a0b0 a0b2 a0b4 
[    1.546645] vesafb: scrolling: redraw
[    1.546648] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.546869] Console: switching to colour frame buffer device 128x48
[    1.609058] fb0: VESA VGA frame buffer device
[    1.827253] fuse init (API version 7.9)
[    1.847430] processor ACPI0007:00: registered as cooling_device0
[    2.596206] skge 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.596219] skge 0000:00:0a.0: PCI: Disallowing DAC for device
[    2.596246] skge 1.13 addr 0xfdd00000 irq 17 chip Yukon-Lite rev 9
[    2.596547] skge eth0: addr 00:11:d8:47:52:3f
[    2.627197] No dock devices found.
[    2.682784] SCSI subsystem initialized
[    2.742350] usbcore: registered new interface driver usbfs
[    2.742379] usbcore: registered new interface driver hub
[    2.765791] usbcore: registered new device driver usb
[    2.790132] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.790148] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.790212] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.790261] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdf00000
[    2.792954] libata version 3.00 loaded.
[    2.800026] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.800222] usb usb1: configuration #1 chosen from 1 choice
[    2.800249] hub 1-0:1.0: USB hub found
[    2.800260] hub 1-0:1.0: 8 ports detected
[    2.800374] USB Universal Host Controller Interface driver v3.0
[    2.904361] sata_via 0000:00:0f.0: version 2.3
[    2.904383] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.904432] sata_via 0000:00:0f.0: routed to hard irq line 10
[    2.904516] scsi0 : sata_via
[    2.904601] scsi1 : sata_via
[    2.904631] ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd400 irq 20
[    2.904634] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xd408 irq 20
[    3.108043] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.312020] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.312101] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.312112] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.312155] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    3.312181] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b400
[    3.312365] usb usb2: configuration #1 chosen from 1 choice
[    3.312392] hub 2-0:1.0: USB hub found
[    3.312401] hub 2-0:1.0: 2 ports detected
[    3.521186] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.521198] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.521237] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    3.521263] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b800
[    3.521434] usb usb3: configuration #1 chosen from 1 choice
[    3.521460] hub 3-0:1.0: USB hub found
[    3.521470] hub 3-0:1.0: 2 ports detected
[    3.728247] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.728259] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.728282] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    3.728306] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c000
[    3.728400] usb usb4: configuration #1 chosen from 1 choice
[    3.728425] hub 4-0:1.0: USB hub found
[    3.728433] hub 4-0:1.0: 2 ports detected
[    3.936542] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.936553] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.936700] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    3.936726] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c400
[    3.938820] usb usb5: configuration #1 chosen from 1 choice
[    3.938983] hub 5-0:1.0: USB hub found
[    3.938994] hub 5-0:1.0: 2 ports detected
[    4.150963] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.151026] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    4.161465] pata_via 0000:00:0f.1: version 0.3.3
[    4.161483] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.162260] scsi2 : pata_via
[    4.162849] scsi3 : pata_via
[    4.164960] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    4.164964] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    4.504548] ata3.00: ATA-6: ST360015A, 3.33, max UDMA/100
[    4.504553] ata3.00: 117231408 sectors, multi 16: LBA 
[    4.512332] ata3.01: HPA unlocked: 66055248 -> 156368016, native 156368016
[    4.512336] ata3.01: ATA-7: SAMSUNG SP0802N, TK200-04, max UDMA/100
[    4.512338] ata3.01: 156368016 sectors, multi 16: LBA48 
[    4.528432] ata3.00: configured for UDMA/100
[    4.536304] ata3.01: configured for UDMA/100
[    4.708345] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A103, max UDMA/33
[    4.708366] ata4.01: ATAPI: SONY    CD-RW  CRX215E5, 5.0D, max UDMA/33
[    4.724220] ata4.00: configured for UDMA/33
[    4.740232] ata4.01: configured for UDMA/33
[    4.740338] scsi 2:0:0:0: Direct-Access     ATA      ST360015A        3.33 PQ: 0 ANSI: 5
[    4.740530] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    4.741057] scsi 2:0:1:0: Direct-Access     ATA      SAMSUNG SP0802N  TK20 PQ: 0 ANSI: 5
[    4.741138] scsi 2:0:1:0: Attached scsi generic sg1 type 0
[    4.744892] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A103 PQ: 0 ANSI: 5
[    4.744978] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[    4.746545] scsi 3:0:1:0: CD-ROM            SONY     CD-RW  CRX215E5  5.0D PQ: 0 ANSI: 5
[    4.746623] scsi 3:0:1:0: Attached scsi generic sg3 type 5
[    4.780082] Driver 'sd' needs updating - please use bus_type methods
[    4.780203] sd 2:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[    4.780218] sd 2:0:0:0: [sda] Write Protect is off
[    4.780220] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.780240] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.780302] sd 2:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[    4.780312] sd 2:0:0:0: [sda] Write Protect is off
[    4.780315] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.780333] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.780337]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.798504]  sda1
[    4.798620] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.798714] sd 2:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[    4.798729] sd 2:0:1:0: [sdb] Write Protect is off
[    4.798732] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.798753] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.798822] sd 2:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[    4.798833] sd 2:0:1:0: [sdb] Write Protect is off
[    4.798835] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.798854] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.798858]  sdb: sdb1 < sdb5 >
[    4.810053] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.825985] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.825993] Uniform CD-ROM driver Revision: 3.20
[    4.826100] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.830601] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.830710] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    5.203272] kjournald starting.  Commit interval 5 seconds
[    5.203291] EXT3-fs: mounted filesystem with ordered data mode.
[   11.759809] udevd version 124 started
[   12.348162] Linux agpgart interface v0.103
[   12.384182] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[   12.388152] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   12.428189] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.497733] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.612263] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.624256] ACPI: Power Button (FF) [PWRF]
[   12.624384] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.632036] ACPI: Power Button (CM) [PWRB]
[   12.632144] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.644014] ACPI: Sleep Button (CM) [SLPB]
[   14.620701] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.799364] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   14.799459] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.367055] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   15.556061] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   16.060239] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   16.060258] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   16.060366] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   16.060505] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   16.574574] codec_read: codec 0 is not valid [0xfe0000]
[   16.580934] codec_read: codec 0 is not valid [0xfe0000]
[   16.587342] codec_read: codec 0 is not valid [0xfe0000]
[   16.593701] codec_read: codec 0 is not valid [0xfe0000]
[   17.679716] lp: driver loaded but no devices found
[   17.728465] Intel536: disagrees about version of symbol struct_module
[   18.494035] EXT3 FS on sdb5, internal journal
[   19.621043] type=1505 audit(1231203470.084:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3943
[   19.826669] type=1505 audit(1231203470.288:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3948
[   19.826961] type=1505 audit(1231203470.288:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3948
[   19.885547] type=1505 audit(1231203470.348:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3952
[   19.929529] type=1505 audit(1231203470.392:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=3956
[   20.066052] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.135681] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.135833] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   20.135836] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   20.135839] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.283739] NET: Registered protocol family 10
[   20.284257] lo: Disabled Privacy Extensions
[   20.304655] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   21.449597] ACPI: WMI: Mapper loaded
[   21.729885] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[   21.731658] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   21.994826] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   24.045279] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   24.045285] apm: overridden by ACPI.
[   24.254177] ppdev: user-space parallel port driver
[   27.386615] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   27.386620] vboxdrv: Successfully done.
[   27.386622] vboxdrv: Found 1 processor cores.
[   27.386817] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   27.386820] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   31.067802] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   31.237340] [drm] Initialized drm 1.1.0 20060810
[   31.249898] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   31.396066] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
[   31.396082] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   31.396140] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   31.621227] [drm] Setting GART location based on new memory map
[   31.621237] [drm] Loading R200 Microcode
[   31.621304] [drm] writeback test succeeded in 1 usecs
[   33.204359] skge eth0: enabling interface
[   33.207905] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.471371] skge eth0: Link is up at 10 Mbps, half duplex, flow control none
[   35.471631] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.981988] PPP generic driver version 2.4.2
[   36.009944] NET: Registered protocol family 17
[   36.389820] NET: Registered protocol family 24
[   45.952007] eth0: no IPv6 routers present

Module                  Size  Used by
pppoe                  18496  2 
pppox                  11276  1 pppoe
af_packet              25728  2 
ppp_generic            32668  6 pppoe,pppox
slhc                   14208  1 ppp_generic
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
vboxnetflt             93832  0 
vboxdrv               120360  1 vboxnetflt
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
battery                18436  0 
ipt_REJECT             11136  1 
ipt_addrtype           10496  4 
xt_state               10112  2 
xt_tcpudp              11008  7 
xt_conntrack           11904  2 
ip6table_filter        10624  1 
ip6_tables             21008  1 ip6table_filter
ipv6                  263972  10 
nf_nat_irc             10240  0 
nf_conntrack_irc       13348  1 nf_nat_irc
nf_nat_ftp             10880  0 
nf_nat                 25368  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      21900  6 nf_nat
nf_conntrack_ftp       15652  1 nf_nat_ftp
nf_conntrack           72032  8 xt_state,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         10752  1 
ip_tables              19600  1 iptable_filter
x_tables               22916  7 ipt_REJECT,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_via82xx            32536  2 
snd_via82xx_modem      19464  0 
gameport               19468  1 snd_via82xx
snd_ac97_codec        111652  2 snd_via82xx,snd_via82xx_modem
evdev                  17696  7 
psmouse                45200  0 
snd_seq_dummy          10884  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_pcm                83204  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart        15360  1 snd_via82xx
k8temp                 12416  0 
snd_seq_midi           14336  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
i2c_viapro             15764  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               31892  1 i2c_viapro
snd                    63268  16 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              15328  1 snd
button                 14224  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
amd64_agp              18184  1 
agpgart                42184  2 drm,amd64_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  2 
crc_t10dif              9984  1 sd_mod
pata_via               16132  1 
sg                     39732  0 
pata_acpi              12160  0 
sata_via               15492  0 
ata_generic            12932  0 
uhci_hcd               30736  0 
ehci_hcd               43788  0 
libata                178208  4 pata_via,pata_acpi,sata_via,ata_generic
usbcore               149360  3 uhci_hcd,ehci_hcd
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
skge                   48144  0 
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fuse                   60828  3 
vesafb                 13828  1 
fbcon                  47648  72 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by windows-killer on 2009-01-05
My modem is attached to port 3 on Windows xp

---

### Post by ranch hand on 2009-01-05
Ok I'll be right with you.  I am on the phone with my son.

---

### Post by dmizer on 2009-01-05
When posting lengthy terminal output, please be sure to enclose the output in ```
 brackets like so: [noparse][code]terminal output
```[/noparse] this makes it both easier to follow a thread, and retains formatting.

Thank you :)

---

### Post by windows-killer on 2009-01-05
> **dmizer said:**
> When posting lengthy terminal output, please be sure to enclose the output in ```
 brackets like so: [noparse][code]terminal output
```[/noparse] this makes it both easier to follow a thread, and retains formatting.

Thank you :)

ok ill keep that in mind:D

---

### Post by ranch hand on 2009-01-05
All right, I'm back.

I see that scanModem would not have done me any good either.

I got gnome-ppp and tried it - worthless, uninstalled it because I was afraid it might screw up my connection.  It is the gui for wvdial which didn't work for me then and does not detect my modem now.

I tried minicom again and it thinks my modem is at ttys8.  In reality it is at ttyS0.

I am very sorry that I led you on this merry chase when what we need is the windows port.  I did not think about it because I am now windows free.  Once again I am sorry.

What you need to do is print out these instructions and try them.  I believe they will work unless there is an issue with the modem controller.

Go first to your network manager applet and click on it.  Click on Manual configuration.  When the box comes up click on the hosts tab.  The results will be grayed out but readable.  I think that your local host will be 127.0.0.1 and the next down with your computers name on it should be 127.0.1.1.  What ever those 2 are use them in pppconfig.

To get there, go to Terminal and enter  sudo pppconfig   and follow the directions for a new connection.  Make sure you have all your connection information written down.  Will be the same as under windows.  The telephone number that your modem uses for example.

Make sure that you check everything before you save the connection and make sure you do that before hitting the exit command.

Your connection will still not work.

Go back to the network manager applet and repeat that up to when the box shows up.  Unlock it with your pass word.

Ignore the tabs and click on the point to point connection and then on properties.  click on enable this connection.  Leave the modem as serial.  Enter phone #.  enter username and password.

Next tab:Modem  Enter ttyS2 (you need this in pppconfig too).  Set volumn at loud (you can reset this later if it bugs you).

Next tab:options.  Check them all.  You want them.

Click on OK.

At this point, if your drivers are right, and the modem controller is not a problem, you should happily hear your modem dialing.  

Check on your system monitor (/system/administration/system monitor) to see if there is input output registered within a few seconds or if your modem redials after about 90 second and then you get some IO.

If so, you are connected.  If you cursor over the network applet it will tell you "No Network Connection" it lies.  If you click on it you should get a dial up connections option that allows you to disconnect and connect.

Firefox will need to be enabled to get on line as it will be set to work off line and you need to go to file and down next to the bottom uncheck that.  After you update there is a fix for this that I will reveal (I found out today) when you report back that you are online under Ubuntu.

---

### Post by windows-killer on 2009-01-05
ranch hand thank you for trying. I guess there is no solution to my problem, maybe in the future there will be a fix.
I wanted to use dialup because I was thinking to downgrade my service to dial up since its $3 per month and I dont use the internet for large file downloads, I just surf the internet and thats it... am a basic user:):D
best regards

---

### Post by ranch hand on 2009-01-05
Did you try it.  I think it should work.

The ttyS2, btw, is because the 4 ttys that work for modems under linux are ttyS0 through ttyS3 and correspond to ports 1 through 4 under windows.  As you are on port 3 under windows the modem should be on ttyS2 under windows.

If the directions weren't clear just ask and I will try to make them planer.  Don't be scared of the terminal, it is your friend.  Windows has one too, it just isn't as friendly.

---

### Post by solomonhomicz on 2009-01-06
I also had this problem on my toshiba laptop.
I installed slmodemd and gnome ppp and still could not connect.

Here's what I did:

-I located and downloaded sl-modem-daemon.

-The daemon will set up your /etc/wvdial.conf file, however after you intall and follow all the instructions with it, you may need to:
~$ cd /etc
~/etc$ sudo gedit wvdial.conf
and then manually enter your phone number, username and password.

-The sl-modem-daemon will default your analog modem port as /dev/tty/SL0.

-Enter this as well as your your baud rate (I can't remember but I think I used scanModem to find this) into your gnome ppp dialer.

-At this point it still won't work until you execute the command:
~$ sudo /etc/init.d/sl-daemon restart

-That's right, you have to execute this command (as root) every time you want to start the modem and then you can dial with gnome ppp

-I made an application launcher with this line that opens in terminal so I can give my sudo password, a little tedious but it works fine.

I think there's commands to enable it on startup but I don't know if this would cause a conflict with the wireless and ethernet drivers-----there's another subject I'm not sure but I think the only way my wireless works is to restart with the wifi switch on and the dialup modem started and then run the package manager-?-?-another post

---

### Post by ranch hand on 2009-01-06
That is of interest to me.

I assume that you have a Smart Link modem.  I searched and found the daemon in the Debian repository.

How on earth did you find this thing?

---

### Post by solomonhomicz on 2009-01-06
I located the info somewhere in ubuntu documentation, nothing else worked.
Once I made the modem work I almost changed my wife to ubuntu (she doesn't like ANYTHING new), but when I set her up for her first session a new bug appeared, sudden shutdown, power off right now, immediately with no warning.
So she's back on XP and I still have a split personality-dammit.
I'm in town right now but I have that documentation printed out at home, it is VERY useful and hard to find, I'll post back with where it's at.

---

### Post by windows-killer on 2009-01-06
> **solomonhomicz said:**
> I located the info somewhere in ubuntu documentation, nothing else worked.
Once I made the modem work I almost changed my wife to ubuntu (she doesn't like ANYTHING new), but when I set her up for her first session a new bug appeared, sudden shutdown, power off right now, immediately with no warning.
So she's back on XP and I still have a split personality-dammit.
I'm in town right now but I have that documentation printed out at home, it is VERY useful and hard to find, I'll post back with where it's at.

thanks, I really wanna get this working

---

### Post by dmizer on 2009-01-06
> **solomonhomicz said:**
> I located the info somewhere in ubuntu documentation, nothing else worked.
Once I made the modem work I almost changed my wife to ubuntu (she doesn't like ANYTHING new), but when I set her up for her first session a new bug appeared, sudden shutdown, power off right now, immediately with no warning.
So she's back on XP and I still have a split personality-dammit.
I'm in town right now but I have that documentation printed out at home, it is VERY useful and hard to find, I'll post back with where it's at.

You wouldn't, by chance, be referring to this?
> **dmizer said:**
> Try this link:
[https://help.ubuntu.com/community/DialupModemHowto#Download%20/%20Detect%20and%20Configure%20/%20Install](https://help.ubuntu.com/community/DialupModemHowto#Download%20/%20Detect%20and%20Configure%20/%20Install)

---

### Post by solomonhomicz on 2009-01-07
The place where I found out about sl-modem-daemon......deb was here:
[https://help.ubuntu.com/community/DialupModemHowto/AlsaModem](https://help.ubuntu.com/community/DialupModemHowto/AlsaModem)

After following these instructions I used this:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

I was unable to make a connection using the network manager so I used the alternative approach downloaded gnome-ppp on my windows side, I attempted alot of different things and was never able to get the dialer to accept my ph #, uname, and pword (invalid?) by editing them by hand into wvdial.conf. The daemon worked but only by using the restart command.

-----HOWEVER after getting the dial-up to work I began suffering from sudden shutdown, I posted here:
[http://ubuntuforums.org/showthread.php?t=1032778](http://ubuntuforums.org/showthread.php?t=1032778)
after spending a few hours to get the wifi working it got worse then I lost wifi and on a restart both my wifi and ethernet drivers disappeared (rather odd don't you think) now my ubuntu will only last about 45 seconds to a minute before gagging and dying. 
----MAYBE it was because I attempted to first use:
SLMODEMD.gcc4.2.tar
which almost worked but just refused to accept ph#, etc.
I then installed: 
sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu4_i386.deb
which actually kind of works but maybe there's a conflict between the two?
I'm probably going to scrub the system tommorrow, start over, try to clean up my modem chicanery, if I come up with a clean way to make it all work I'll post.

-----PS any help at all with this fatal shutdown deal would be greatly appreciated Toshiba Satellite M35X, 1.5g celeron m, 1g RAM, Atheros AR 5004G WiFi, Realtek RTC8139/810x Ethernet

---

### Post by ranch hand on 2009-01-07
Sounds to me like you ought to invest in a real hardware modem.  I went with an internal.  Everyone seemsto think that external is the way to go.  You really get a lot better performance.

Otherwise your search sounds a lot like my search for into on the cannexant that came with this box.  Not fun when having to switch computers and burn everything to CDs.

My wife, I think, is a little more adventurus but it took her 3 weeks to want something other than Vista to my 3 days.  Sometimes it is good to have someone there to slow you down and make you think.

---

### Post by windows-killer on 2009-01-07
solomonhomicz, sorry to hear that about your computer.
am using ubuntu for a year now, am still a newbie but am getting there. I find ubuntu really good OS and well organized and love the out of the box approach. 95% of my hardware work well:D.
Do you guys know if they are any USB dialup modems that work out of the box for ubuntu?

---

### Post by dmizer on 2009-01-07
This will work: [http://www.radi.com/modular47.htm](http://www.radi.com/modular47.htm) (don't know the price though)

I just did a google search with the following terms: usb hardware modem

---

### Post by ranch hand on 2009-01-07
Just about anything by USRobotics will work.  They like linux.  they are also about the best you will get for lasting and holding a connection.

I use and internal USR5610c.

---

### Post by ranch hand on 2009-01-07
You are still going to have to configure it in some way, but they are supposed sto be a little easier.

The developers are not real worried about those of us on Dialup.  It is going fast the way of the dinasaur.

---

### Post by windows-killer on 2009-01-07
I might buy it.:rolleyes:
are the drivers available on the CD, or I have to download them, or maybe they are included with ubuntu?

what steps I have to follow to get it working? easy/hard?:D

---

### Post by ranch hand on 2009-01-07
The modem should be supported by your kernal.  I would check the discription of the modem you want and see what the people that make it say.

The Win drivers came on a CD with my USR modem and there were some handy installation tips and CLI commands for Linux, non of which really helped but did give some hints as to what to look for.

---

### Post by ranch hand on 2009-01-07
I did a little checking and found this site that my give you a clue to installing a usb Modem

<https://help.ubuntu.com/community/DialupModemHowto/Setserial?action=show&redirect=setserial>

I copy/pasted the commands for detection and they installed/activated the needed files, did the checks flawlessly.  Of coarse it failed.  I don't have a sub Modem or the associated files.  But it appears to work in Hardy and you need that tty address to configure the Modem to connect.

---

### Post by ieee488 on 2009-01-08
> **windows-killer said:**
> I might buy it.:rolleyes:
are the drivers available on the CD, or I have to download them, or maybe they are included with ubuntu?

what steps I have to follow to get it working? easy/hard?:D

If you are still looking for a PCI modem, 
my USR PCI modem with [http://xmodem.org/chipsets/ti/ti_700.html]("http://xmodem.org/chipsets/ti/ti_700.html")
chipset works for me. Find them cheap on eBay. Search on eBay for US Robotics modem, and take a look at the photos. I got good at identifying them. Mine has been recognized without having to do anything since Ubuntu 5.04.

---

### Post by windows-killer on 2009-01-10
thanks for the link guys!:)
am looking forward on buying a USR USB modem.

---

### Post by ranch hand on 2009-01-10
Wish I had known that these were recognized.  Hardware modems, USR in particular, are the only way to go for dial up connections.

---

### Post by ieee488 on 2009-01-10
item #320327909463
item #180318448381
item #280300520604	
on eBay right now, all these PCI modems should work in Ubuntu

---

### Post by ranch hand on 2009-01-10
The job I have now is going to end.  The boss up and died on me.  The hiers need to sell the place.

We bought a place in town where I will actually have ADSL.  However, I hope to get another ranch job as I don't like towns.  My next computer will be built by me and I will need dialup on it.  I need to have some Model #s and  the post above should give some to me.

Thanks ieee488

---

### Post by ranch hand on 2009-01-10
I believe that item#180318448381  is a 5610 series modem.  My USR5610c is definately not detected by my box, currently running on 2.6.24-22 (Hardy).

It runs great but takes about 3 to 5 minutes to configure using pppconfig first and then network manager.

They give a link for updating the modem in the listing and the update is for 5610 and mine says perfomance pro on the box.

It is a great modem but I never would have found the right tty address if I had not had Vista at the time to find the port on Win and translate that to ttyS0.

If I go to the ttyS0 file right now it will be empty.  There is no modem listed in any file on this box.  The bugger doesn't care.  It works anyway.  Network manager still shows "no network connection" if you cursor over it.  If you click on the applet it does give you the option of connect/disconnect so I don't care if it thinks there is no connection.

It would be hard to send this if there weren't.

As my next box will never have MS on it, I really need one that will be detected.  I may get some of the others and try them.  That is why I have 3 installs of Hardy.  I have 2 that I can break and still have a box that works.  I am on wone of the 2 "play" installs now.

---

### Post by ranch hand on 2009-01-10
Item# 280300520604  has one USRWinmodem and a USR Hardware modem USR0778.  It appears to be another member of the 5610 family.  5610a and 5610b may work.  I don't know about this one.

I am sure that it will connect and work well but if it is recognized I don't know.

Any clues?

---

### Post by ModelM on 2009-01-10
ranch hand:

I think that if you type ```
lspci
```into a terminal you'll see a line something like```
02:00.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)

```

I do believe that Ubuntu "recognizes" your modem.

And keep in mind that ttyS0 is not a modem, it's a serial port. The operating system only communicates with the serial port. All of the "modem stuff" takes place in the modem (the whole point of a hardware modem) & the operating system has no concern or worry about whatever device is attached to the serial port.

I'm tuning in late but I thought I heard someone asking about USB modems. The USR5637 works perfectly in Ubuntu 8.04 & later. The Rosewill RNX-56USB works perfectly in Ubuntu 8.10, but not 8.04. (Not without grabbing wrenches & going under the hood.)

---

### Post by ranch hand on 2009-01-11
Oh yes, you can find it there.  You just can't find any trace of it anywhere else in files that ought to have it.

Doesn't matter.  The sucker works just fine.  For that matter it works better than it did under Vista by about 20%.  And at the distance I am from our providers modem, about 54 miles, 20% makes a big difference.

---

### Post by .arean on 2009-01-11
For what it's worth, I have a "nexxtech" (think it's just a generic circuit city brand) model NSFTMD1 winmodem that I got from circuit city for like $10 or so. It works great on 8.04 with the dell drivers from [here (already unlocked to full speed)]("http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/") and in 8.10 with the paid (or free if you don't mind 14.4k) drivers from [linuxant]("http://www.linuxant.com/drivers/"). Hopefully dell will start shipping computers with 8.10 so they'll release drivers that work with 8.10.

After installing the deb package, just do sudo wvdialconfig, fill in your connection info in wvdial.conf and everything should be up and running. I tried using alien to convert the 64bit rpm to deb but it wouldn't complete the installation. So if you're on 64bits hardy you'll have to compile the driver from source but that's a fairly simple task if you follow the instructions.

Might be easier and possibly cheaper than trying to track down a working hardware modem.

---

### Post by ieee488 on 2009-01-11
> **ranch hand said:**
> Item# 280300520604  has one USRWinmodem and a USR Hardware modem USR0778.  It appears to be another member of the 5610 family.  5610a and 5610b may work.  I don't know about this one.

I am sure that it will connect and work well but if it is recognized I don't know.

Any clues?



Below is the output of lspci for my PC.
> 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]
02:09.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:09.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:09.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:09.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
02:09.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0d.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)


You still have to do some work even if Ubuntu detects your modem.
But Ubuntu detecting your modem is a very important step.

As I wrote earlier, I had no problems dialing up to AT&T prior to July 2007 when I switched to Verizon DSL.

[http://www.techplusnj.com/linux/linux_dialup.html](http://www.techplusnj.com/linux/linux_dialup.html)

---

### Post by ranch hand on 2009-01-11
Well, if you are going to show me yours, I'd better show you mine.

00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
04:00.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
04:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
04:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
04:05.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
tom@hogwash:~$ 

I am quite happy with the way this modem works the way it is.  It grabs a good connection and holds it well.  Did about 60Mb downloads last night and lost connection once, got it right back.  All I run is Hardy and it gets along just fine in a sort of plutonic relationship with this modem.

It works, I don't mess with it.  I need it too much to contact the forums when I screw up other things, something I am very good at

---

### Post by ieee488 on 2009-01-11
ranch hand,

You keep saying your modem is not recognized. 

It is. The output of the **lspci** command proves it.

That is the first but not only step to getting dial-up working in Ubuntu.

You and I have the same modem.

Dial-up wasn't that easy in Windows either. AT&T gave people a CD for installing software as did Earthlink. In Linux, we don't have that luxury since those ISPs concentrate on helping the Windows users only. We the users have to do a bit more work.

Anyway, those modems being auctioned on eBay *should* work in Linux.

---

### Post by ranch hand on 2009-01-11
I don't think you understand.  My modem is working fine.  I could not be sending this if it weren't.

It just is not in all the files that it supposedly is in.   There is nothing in ttyS0, for instance.  This is where the modem is mounted.  Wvdial to this day claims I have no modem.  Once again, the modem is there and it is working great.

I just find it interesting that it is working when half, or better, of the files are not there.  I think this says a lot about the robustness of linux in general and Ubuntu in particular.

I do NOT have a problem with my modem.

I actually think it is quite easy to get the thing to work under Ubuntu compared to MS.  It is certainly easier to configure for your ISP.  I use pppconfig and then set up the network manager with the same information - service provider, user name, password, host(s), location (ttyS0), and in network manager the preferences (all) - click ok and the thing dials and connects.

It dials on bootup which some people think is a problem, I don't.  I like it to be up and going when I get in as the first job of the day is to check the weather.  This is important to those of us that work out in it.

We did have a problem with FF coming up offline but they fixxed that with an option in the newest update.

Thanks for your concern but I really don't need help with the modem.  I do wonder why yours was good out of the box and it took me about 2 weeks to hunt down the answers.  It took that long because I had Vista at the time and could only get on line with it over a crappy connexant winmodem.  About 2.9K on a good day.

I also find it interesting that I used the CD that came with the modem to install in Vista and it works faster under Ubunto.  Vista would get up to about 3.9K on a good day and Ubuntu gets 4.4 on an average day.  Yes, this is slow.  We have the last line in our area and are 54 miles from from the providers modem.

Seeing how the boss died back in July and the cows ship out on the 13th, this job is coming to an end.  I will probably be here until spring sometime when the "hairs" have their auction (another piece of american agriculture down the tubes).  We bought a place in town and when I get there I will have access to ADSL and be about 5 blocks from the provider.  I have a feeling that that will be a little faster.

I will not be removing the modem as I hope to go to another ranch job and they all are on dialup or satilite which I think is too pricey.

We need another computer so my wife has one in town.  Her mother is across the street from the house we bought.  We need to keep an eye on her.  I think I will build one and send this one there.  I want the dialup modem for backup even then and will just have to change the number.

This really is a lot of fun.  I have not enjoyed computing for years.  I kind of like the change.

---

### Post by ieee488 on 2009-01-11
I understand that your modem is working fine.

I am failing to understand some of the points your raise about your modem in Ubuntu.

**wvdial** is similar to an .EXE file in Windows, you run it to dial out. This is not a file that you edit.

Before you can run **wvdial**, you need to run **sudo wvdialconf** which generates */etc/wvdial.conf* file. Are you saying that you don't have the file */etc/wvdial.conf*? 

Also, if you PC has a serial port at the back (it's a 9-pin DB9 connector) then your modem is most likely at */dev/ttyS1* with the serial port being located at */dev/ttyS0*.

Because I re-installed Ubuntu 8.04 (didn't like Ubuntu 8.10), I just now did the above commands. Since you and I have the same modem, you should see the same thing.

Anyway, I am keeping my modem as the 3rd backup. My AT&T mobile broadband account that I use when I am at work is my backup.

---

### Post by ranch hand on 2009-01-11
The modem is on ttyS0.  I had to move it to get it there because it was, origanaly at 5 which is where the serial is.  Our kernal only supports modems from ttyS0 to ttyS3 so I had to move it.

This box had no serial port at all.  I put that card in to have a paralell port for my old printer.

Wvdial, to this day, claims that I have no modem.

for your entertainment, here  is my Wvdial conf contents:

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

Basically wvdial is one way to get to the internet by modem.  There are others.

If wvdial is the badge - we don't need no stinking badge.

Try that in windows.

---

### Post by ieee488 on 2009-01-11
Which version of Ubuntu are you using?

---

### Post by ranch hand on 2009-01-12
8.04.1 three times, kernal 2.6.24-22 on 2 and the oather on -23  all are 64.

---

### Post by ranch hand on 2009-01-18
I decided to try wvdial again.  It has been several months and several updates sence I last tried it.

The good news is that it did not screw up my ability to connect which is what it used to do.  I also once again have things in my /etc/wvdial.conf file.

It still works the same, it dials and the password will not go through, it tries a few times and then freaks out and the terminal crashes.

Basically, what I need to do now is reedit the file back to nothing so that anyone reading the thing does not read our password out of the file.  This strikes me as a rather silly security hole.  When you are done in pppconfig and close the terminal the password is not readable anymore.

I installed 8.10 and can't get that wucker going because they changed the network manager.  I also installed Mandriva 2009 and it configured the modem during instalation, very easy and smooth and it works.  I don't like the rest of it all that well but modem support is great.

I will play with it a bit.  KDE does not appeal to me.  The rpm does not look as attractive as deb.

Interesting though and will learn a lot, I am sure.

---

### Post by capt.d on 2009-01-18
For dial-up i've used KPP for a few years and it's the first thing i install if not included in the O.S. I love it, looks and works great. It is in Synaptic and works with genome also.

---

### Post by ranch hand on 2009-01-18
That is interesting.  I don't really like the look or feel of KDE, but I wonder if it is more modem friendly.

I have a n instalation of Mandriva2009 and it configured my modem during the instalation proccess.  It does say that I need to get kppp-provider as there is a problem if the connection is lost.  It won't redial, only dials on boot up.  It must be using kppp though.

I have tried gnome-ppp and it does not work in 8.10.  I may have the wrong version.

Kppp is in synaptic.  I have no connection to the internet with the 8.10 instalation.  This makes getting apps tough.  I need to get in Hardy, where I am now, find a downloadable deb package, download, transfer the file(s) to the 8.10 partition, copy the dependancies, reboot to 8.10.  Then I can pull up synaptic and check to see if the dependancies are met.

Kppp has 9 dependancies, 6 unmet.  Of those 6, 1 has 25 dependancies, 17 unmet.  Of those 17, 1 has 45 dependancies, I don't know how many are unmet yet.

Now some are duplicates.  That 1/6 has 5/17 that are the same as the other 5 dependancies of kppp, so I get to kill more than one bird with a stone.  None the less it will take days.  I will probably whittle away at it.

In Mandriva I get the same result that I get in Hardy.  That is that while I am connected, the network monitor, while showing connection speed, claims I am not connected.  Hardys' network manager makes the same claim.

In Hardy, to configure a connection,  sudo pppconfig, go through that, then congigure in network manager.  Takes less than 10 minutes.  After that you can connect/disconnect through the manager applet.

In Intrepid they have changed the network manager and it no longer works.  I am tring to get wvdial to work (never did in Hardy) and I am having no luck so far.

Everybody needs a hobby though.

---

### Post by windows-killer on 2009-01-21
isnt Kpp and gnome ppp the exact same thing but for 2 different desktop environments?

---

### Post by dmizer on 2009-01-22
> **windows-killer said:**
> isnt Kpp and gnome ppp the exact same thing but for 2 different desktop environments?
kppp is a gui front end for pppd and gnome ppp is a gui fronend for wvdial.

---

### Post by ranch hand on 2009-01-24
pppd seems to be the problem.  I installed gppp as it is supposed to be the default dialler for intrepid, but not installed.  Strange.

The poor thing has a nervous breakdown when used.  Dials fine.  Ends up with about a mile of attemps that all end up with the same error - can't use pppd.

As far as I can tell the info in wvdial is correct and I ran pppconfig and it is correct (has the same info as in hardy and that works without wvdial).

---

### Post by ranch hand on 2009-01-24
OK.  Switched to my playtime installation.

I put gppp on here too.  Disabled the config through network manager.  Connected through gppp.

I don't like it but it works and you can't comlain about that.

So, I would say that this is a problem with Intrepid ranther than any thing else.

---

### Post by ranch hand on 2009-01-26
I hope the OP is still with us because I have some good news and some crow to eat.

If you get rid of gnome-ppp and any other attempts that you have made to connect, wvdial works very well indeed.  I am on Intrepid right now.

So thank you to all you folks who insisted wvdial works.  It has never worked for me in Hardy, can't say why, don't know.  Works like a charm here though if you don't go screwwing around with other things.

I don't know about the OP, but I am happy.  I learned something (I really can, just knock my head on the wall a few times).

Now maybe I can get into real trouble with Intrepid.  I broke Hardy several times after gettting connected.  Just a kid in a candy shop.

Thanks again all, what a great bunch.

---

### Post by ranch hand on 2009-01-27
Just thought I should update this a little.

Gnome-ppp did not work because it could not get into the pppd files.  Your user needs to be part of the "dip" group, what ever that is.  This group does nt show up in my Users an Groups manager.

Just typing wvdial into terminal will connect you.  It does not seem to be a very stable connection but it works.

Searching for gnome-ppp comes up with several bug reports.

<https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289575>

This page has the answer to joining the dip group.  Run the 
```

ls -l /usr/sbin/pppd

```
and you should get
```

-rwsr-xr-- 1 root dip 273064 2008-10-16 03:51 /usr/sbin/pppd

```

Gnome-ppp should now work and it seems to reconnect when you loose connection and everything.

---

