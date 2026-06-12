---
title: "HDA ATI SB with NO SOUND in FF 7.04-Help!"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by intricate on 2007-05-14
My laptop using FF 7.04 shows the following detected sound chip:

HDA ATI SB (Alsa mixer).

Ive added some programs using the SYNAPTIC MANAGER but I cannot hear any sound when I try to playback a DVD  movie. The video plays back fine.

What do I need to add to FF 7.04 in order to hear sound when I playback a DVD movie?

Thanks to all responding experts.

---

### Post by krismatth3 on 2007-05-16
I am having this same issue. Everything *seems* to work, but there is no sound.

---

### Post by intricate on 2007-05-17
I used AUTOMATIX to install the needed codecs and ALSA files but nada de nada de noodle sound!  VLC plays cool video but all movies are silent! Whats the next step to overcome this glitch?  The HD ATI SB 450 is seen by 7.04 bit NO SOUND OUTPUT occurs.  Help! Will Robinson-Help.

---

### Post by volkswagner on 2007-05-21
No sound here

ATI SB 450
I have been searching for a solution to no sound, volume icon is x'd out.
sound controls only show caller id and hook

I found a possible solution someone has:[http://www.puchalla-online.de/nx6325.html]("http://www.puchalla-online.de/nx6325.html")
working on Debian GNU Linux (Etch) on an HP compaq nx6325 laptop

HERE IT IS! 
What does it mean?
How do i perform these tasks? NEWBEE

> 
Soundcard
Sound works fine with ALSA 1.0.12rc3, I had to install it manually.
The version with Linux 2.6.17.5 is too old.
Create /etc/modutils/mythings:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=hp position_fix=1 enable=yes

and run update-modules.modutils.

I SEE I AM NOT ALONE HOPE ALL OF US  CAN GET THIS TO WORK

---

### Post by krismatth3 on 2007-05-21
I tried what your link mentioned, but it did not work (for me). The website is for a version of debian, which is using an older kernel and older alsa. 7.04 comes with a newer version of alsa than the web page mentions.

---

### Post by volkswagner on 2007-05-21
If the link does not work google this

Debian GNU Linux (Etch) on an HP compaq nx6325 laptop

it should be the first result

On his page updates using kernel 2.6.21

Does anyone know if i can use this setup?

---

### Post by volkswagner on 2007-05-22
UPDATE

Here is what i have done

>  Originally Posted by calgarystevens  View Post
Just reread your post, and realized you have Kubuntu installed, so I don't know if this will apply to your problem or not, buyer beware.

OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end


This removed the x on the volume icon. 

Alsamixer still wont start......Then did this

Posted by Scott_Kirkwood

> Fixed:
Solution was to
Code:

rm ~/.asoundrc

I found the problem by doing
Code:

strace -eopen alsamixer

And noticing that it was loading ~/.asoundrc. something in that file was screwing up my sound.

This now lets alsamixer start.  Nothing is muted still no sound but my volume slider works with the hardware knob on my machine still no sound.  any advice?

---

### Post by volkswagner on 2007-05-23
bump and update


> 
 Re: Audio (SB450) stopped working after upgrading to 7.04
Quote:
Originally Posted by Anaea View Post
I've got it. djails was mostly right, I just had to tweak one little thing.
Code:

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack

and then in /etc/modprobe.d/alsa-base
Code:

options snd-hda-intel probe_mask=8 model=3stack

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*] spot too.

Good luck, and thanks to everybody for helping out on this. I was about to give up and start building kernels.
Thanks a bunch. THe 3stack in the alsa-base file WORKED. You rock!!!!!! I have a Toshiba laptop A135-S2246 with the SB450 audio card. Did you also figure out how to turn off the laptop speakers while using headphones as the speakers still play when I put headphones in?

When i run 
 sudo rmmod snd-hda-intel
I get this
ERROR: Module snd_hda_intel is in use
[SIZE="3"]
How do i stop alsamixer[/SIZE]

I see i am running alsamixer v1.0.13
in alsamixer i see my card= HDA ATI SB, Chip=Realtek ALC861-vd

Also when i run strace -eopen alsamixer
alsamixer opens and i see this when i esc

eric@vista:~$ strace- eopen alsamixer
bash: strace-: command not found
eric@vista:~$ strace -eopen alamixer
strace: alamixer: command not found
eric@vista:~$ strace -eopen alsamixer
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY)    = 3
open("/dev/snd/controlC0", O_RDWR)      = 3
open("/dev/snd/controlC0", O_RDONLY)    = 3
open("/dev/snd/controlC0", O_RDWR)      = 3
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 4
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 4
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 4
open("/lib/terminfo/x/xterm", O_RDONLY|O_LARGEFILE) = 4

Process 6660 detached

ANY PROBLEMS HERE?

I FEEL I AM SO CLOSE BUT STILL NEED GUIDANCE

---

### Post by volkswagner on 2007-05-24
See dmesg output..  (ATTACHED).  Any problems here...?  Things i notice not sure if they are normal or possible problems

[    0.000000] ATI board detected. Disabling timer routing over 8254.

[   19.619049] ACPI Error (evregion-0317): No handler for Region [ERAM] (da0e6484) [EmbeddedControl] [20060707]
[   19.619056] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[   19.619062] ACPI Exception (dswexec-0458): AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20060707]
[   19.619068] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node da0dee8c), AE_NOT_EXIST
[   19.619102] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node da0e7f2c), AE_NOT_EXIST
[   19.629456] ACPI: Interpreter enabled

[   19.630339] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.630345] PCI: Probing PCI hardware (bus 00)
[   19.631962] Boot video device is 0000:01:05.0
[   19.632414] PCI: Transparent bridge - 0000:00:14.4
[   19.632532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.634845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   19.642262] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   19.642566] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   19.642842] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   19.643114] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   19.643429] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   19.643910] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   19.644184] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   19.644496] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   19.644775] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   19.690353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   19.690839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   19.691463] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.691472] pnp: PnP ACPI init
[   19.714368] pnp: PnP ACPI: found 10 devices
[   19.714373] PnPBIOS: Disabled by ACPI PNP
[   19.714424] PCI: Using ACPI for IRQ routing
[   19.714427] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,

CAN I TRY PCI=ROUTEIRQ TO SE IF IT HELPS?   HOW DOW I DO THIS?

---

### Post by volkswagner on 2007-05-24
Here is the complete dmesg output

eric@vista:~$ demsg
bash: demsg: command not found
eric@vista:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000004000 end: 00000000000e0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001bd80000 end: 000000001be80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001be80000 size: 0000000000011000 end: 000000001be91000 type: 3
[    0.000000] copy_e820_map() start: 000000001be91000 size: 000000000006f000 end: 000000001bf00000 type: 4
[    0.000000] copy_e820_map() start: 000000001bf00000 size: 0000000000100000 end: 000000001c000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001be80000 (usable)
[    0.000000]  BIOS-e820: 000000001be80000 - 000000001be91000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001be91000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6a50
[    0.000000] Entering add_active_range(0, 0, 114304) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114304
[    0.000000]   HighMem    114304 ->   114304
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114304
[    0.000000] On node 0 totalpages: 114304
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 861 pages used for memmap
[    0.000000]   Normal zone: 109347 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f69c0
[    0.000000] ACPI: RSDT (v001 TOSCPL TOSCPL00 0x06040000  LTP 0x00000000) @ 0x1be896c5
[    0.000000] ACPI: FADT (v001 TOSCPL SB450    0x06040000 ATI  0x000f4240) @ 0x1be90d8a
[    0.000000] ACPI: SLIC (v001 TOSCPL TOSCPL00 0x06040000 LOHR 0x00000000) @ 0x1be90dfe
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1be90f74
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x1be90fc4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x1be8ad69
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Tst 0x00003000 INTL 0x20050228) @ 0x1be8ab0a
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x1be89705
[    0.000000] ACPI: DSDT (v001 TOSCPL    SB450 0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:c4000000)
[    0.000000] Detected 1733.440 MHz processor.
[   18.583284] Built 1 zonelists.  Total pages: 113411
[   18.583289] Kernel command line: root=UUID=5d92f640-6b01-4efb-831a-15732dce06ac ro quiet splash
[   18.583459] mapped APIC to ffffd000 (fee00000)
[   18.583461] mapped IOAPIC to ffffc000 (fec00000)
[   18.583465] Enabling fast FPU save and restore... done.
[   18.583468] Enabling unmasked SIMD FPU exception support... done.
[   18.583481] Initializing CPU#0
[   18.583578] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   18.584648] Console: colour VGA+ 80x25
[   18.585123] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.585460] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.599369] Memory: 441912k/457216k available (1992k kernel code, 14668k reserved, 893k data, 328k init, 0k highmem)
[   18.599379] virtual kernel memory layout:
[   18.599380]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.599381]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.599382]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   18.599384]     lowmem  : 0xc0000000 - 0xdbe80000   ( 446 MB)
[   18.599385]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   18.599386]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   18.599387]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   18.599391] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.675475] Calibrating delay using timer specific routine.. 3470.95 BogoMIPS (lpj=6941915)
[   18.675519] Security Framework v1.0.0 initialized
[   18.675528] SELinux:  Disabled at boot.
[   18.675545] Mount-cache hash table entries: 512
[   18.675683] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[   18.675690] monitor/mwait feature present.
[   18.675692] using mwait in idle threads.
[   18.675697] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.675700] CPU: L2 cache: 1024K
[   18.675703] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002940 0000c109 00000000 00000000
[   18.675713] Compat vDSO mapped to ffffe000.
[   18.675717] Remapping vsyscall page to ffffe000
[   18.675730] Checking 'hlt' instruction... OK.
[   18.691558] SMP alternatives: switching to UP code
[   18.691749] Freeing SMP alternatives: 11k freed
[   18.691934] Early unpacking initramfs... done
[   19.024185] ACPI: Core revision 20060707
[   19.042332] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.460984] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[   19.461013] Total of 1 processors activated (3470.95 BogoMIPS).
[   19.461191] ENABLING IO-APIC IRQs
[   19.461407] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   19.606393] Brought up 1 CPUs
[   19.606637] Booting paravirtualized kernel on bare hardware
[   19.606738] Time:  6:30:45  Date: 04/24/107
[   19.606771] NET: Registered protocol family 16
[   19.606865] EISA bus registered
[   19.606870] ACPI: bus type pci registered
[   19.611538] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[   19.611540] PCI: Using configuration type 1
[   19.611542] Setting up standard PCI resources
[   19.619049] ACPI Error (evregion-0317): No handler for Region [ERAM] (da0e6484) [EmbeddedControl] [20060707]
[   19.619056] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[   19.619062] ACPI Exception (dswexec-0458): AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20060707]
[   19.619068] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node da0dee8c), AE_NOT_EXIST
[   19.619102] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node da0e7f2c), AE_NOT_EXIST
[   19.629456] ACPI: Interpreter enabled
[   19.629459] ACPI: Using IOAPIC for interrupt routing
[   19.630339] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.630345] PCI: Probing PCI hardware (bus 00)
[   19.631962] Boot video device is 0000:01:05.0
[   19.632414] PCI: Transparent bridge - 0000:00:14.4
[   19.632532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.634845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   19.642262] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   19.642566] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   19.642842] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   19.643114] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   19.643429] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   19.643910] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   19.644184] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   19.644496] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   19.644775] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   19.690353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   19.690839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   19.691463] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.691472] pnp: PnP ACPI init
[   19.714368] pnp: PnP ACPI: found 10 devices
[   19.714373] PnPBIOS: Disabled by ACPI PNP
[   19.714424] PCI: Using ACPI for IRQ routing
[   19.714427] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.746405] NET: Registered protocol family 8
[   19.746407] NET: Registered protocol family 20
[   19.746627] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   19.746630] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   19.746633] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   19.746635] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   19.746908] PCI: Bridge: 0000:00:01.0
[   19.746911]   IO window: 9000-9fff
[   19.746915]   MEM window: d0000000-d00fffff
[   19.746919]   PREFETCH window: d8000000-dfffffff
[   19.746923] PCI: Bridge: 0000:00:06.0
[   19.746924]   IO window: disabled.
[   19.746928]   MEM window: d0100000-d01fffff
[   19.746931]   PREFETCH window: disabled.
[   19.746942] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[   19.746944]   IO window: 0000a400-0000a4ff
[   19.746950]   IO window: 0000a800-0000a8ff
[   19.746957]   PREFETCH window: 20000000-23ffffff
[   19.746964]   MEM window: 28000000-2bffffff
[   19.746970] PCI: Bridge: 0000:00:14.4
[   19.746974]   IO window: a000-afff
[   19.746981]   MEM window: d0200000-d02fffff
[   19.746987]   PREFETCH window: 20000000-23ffffff
[   19.747011] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.747043] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[   19.747077] NET: Registered protocol family 2
[   19.782231] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   19.782320] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   19.782466] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   19.782532] TCP: Hash tables configured (established 16384 bind 8192)
[   19.782535] TCP reno registered
[   19.794248] checking if image is initramfs... it is
[   20.458489] Freeing initrd memory: 6992k freed
[   20.459128] audit: initializing netlink socket (disabled)
[   20.459148] audit(1179988245.540:1): initialized
[   20.459284] VFS: Disk quotas dquot_6.5.1
[   20.459305] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.459363] io scheduler noop registered
[   20.459366] io scheduler anticipatory registered
[   20.459368] io scheduler deadline registered
[   20.459376] io scheduler cfq registered (default)
[   20.459603] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.459640] assign_interrupt_mode Found MSI capability
[   20.459643] Allocate Port Service[0000:00:06.0:pcie00]
[   20.459677] Allocate Port Service[0000:00:06.0:pcie02]
[   20.459823] isapnp: Scanning for PnP cards...
[   20.816541] isapnp: No Plug & Play device found
[   20.843240] Real Time Clock Driver v1.12ac
[   20.843318] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.844158] mice: PS/2 mouse device common for all mice
[   20.844713] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.845037] input: Macintosh mouse button emulation as /class/input/input0
[   20.845069] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.845073] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.845382] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   20.845645] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.845725] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.845729] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.845732] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.845734] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.845737] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.845860] EISA: Probing bus 0 at eisa.0
[   20.845873] Cannot allocate resource for EISA slot 1
[   20.845902] Cannot allocate resource for EISA slot 8
[   20.845904] EISA: Detected 0 cards.
[   20.876095] TCP cubic registered
[   20.876108] NET: Registered protocol family 1
[   20.876132] Using IPI No-Shortcut mode
[   20.876217] ACPI: (supports S0 S3 S4 S5)
[   20.876272]   Magic number: 7:907:519
[   20.876812] Time: tsc clocksource has been installed.
[   20.876957] Freeing unused kernel memory: 328k freed
[   20.878575] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.065022] Capability LSM initialized
[   22.100244] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.100250] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.100262] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.100269] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.100275] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.100281] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.100288] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.100294] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.100300] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.479852] SCSI subsystem initialized
[   22.485205] libata version 2.20 loaded.
[   22.488233] sata_sil 0000:00:12.0: version 2.2
[   22.488265] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   22.488279] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   22.488354] ata1: SATA max UDMA/100 cmd 0xdc864080 ctl 0xdc86408a bmdma 0xdc864000 irq 17
[   22.488390] ata2: SATA max UDMA/100 cmd 0xdc8640c0 ctl 0xdc8640ca bmdma 0xdc864008 irq 17
[   22.488405] scsi0 : sata_sil
[   22.500727] usbcore: registered new interface driver usbfs
[   22.500749] usbcore: registered new interface driver hub
[   22.500771] usbcore: registered new device driver usb
[   22.528418] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.625319] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.684000] Time: acpi_pm clocksource has been installed.
[    3.856000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.864000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.864000] ata1.00: ATA-6: TOSHIBA MK8032GSX, AS112M, max UDMA/100
[    3.864000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.872000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.872000] ata1.00: configured for UDMA/100
[    3.872000] scsi1 : sata_sil
[    4.184000] ata2: SATA link down (SStatus 0 SControl 300)
[    4.184000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8032GS AS11 PQ: 0 ANSI: 5
[    4.184000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[    4.184000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.184000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    4.184000] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0504000
[    4.240000] usb usb1: configuration #1 chosen from 1 choice
[    4.240000] hub 1-0:1.0: USB hub found
[    4.240000] hub 1-0:1.0: 4 ports detected
[    4.344000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[    4.344000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.344000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    4.344000] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd0505000
[    4.400000] usb usb2: configuration #1 chosen from 1 choice
[    4.400000] hub 2-0:1.0: USB hub found
[    4.400000] hub 2-0:1.0: 4 ports detected
[    4.504000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    4.504000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.504000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.504000] ehci_hcd 0000:00:13.2: irq 18, io mem 0xd0506000
[    4.504000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.504000] usb usb3: configuration #1 chosen from 1 choice
[    4.504000] hub 3-0:1.0: USB hub found
[    4.504000] hub 3-0:1.0: 8 ports detected
[    4.608000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.608000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[    4.608000] ATIIXP: chipset revision 128
[    4.608000] ATIIXP: not 100% native mode: will probe irqs later
[    4.608000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[    4.608000] Probing IDE interface ide1...
[    4.624000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.624000] sda: Write Protect is off
[    4.624000] sda: Mode Sense: 00 3a 00 00
[    4.624000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.624000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.624000] sda: Write Protect is off
[    4.624000] sda: Mode Sense: 00 3a 00 00
[    4.624000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.624000]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    4.720000] sd 0:0:0:0: Attached scsi disk sda
[    4.724000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.032000] Attempting manual resume
[    5.032000] swsusp: Resume From Partition 8:8
[    5.032000] PM: Checking swsusp image.
[    5.032000] PM: Resume from disk failed.
[    5.068000] kjournald starting.  Commit interval 5 seconds
[    5.068000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.344000] hdc: DVD/CDRW UJDA770, ATAPI CD/DVD-ROM drive
[    5.680000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.680000] 8139cp 0000:09:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.680000] 8139cp 0000:09:06.0: Try the "8139too" driver instead.
[   16.572000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.600000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.392000] ath_hal: module license 'Proprietary' taints kernel.
[   17.392000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   17.436000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.588000] wlan: 0.8.4.2 (0.9.3)
[   17.620000] ath_pci: 0.9.4.5 (0.9.3)
[   17.624000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   17.624000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   18.180000] ath_rate_sample: 1.2 (0.9.3)
[   18.180000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   18.180000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   18.180000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   18.180000] wifi0: mac 10.0 phy 6.1 radio 10.2
[   18.180000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   18.180000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   18.180000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   18.180000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   18.180000] wifi0: Use hw queue 8 for CAB traffic
[   18.180000] wifi0: Use hw queue 9 for beacons
[   18.212000] wifi0: Atheros 5424/2424: mem=0xd0100000, irq=20
[   18.228000] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[   18.228000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.228000] Yenta: Routing CardBus interrupts to PCI
[   18.228000] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[   18.240000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   18.240000] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[   18.248000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   18.272000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   18.280000] 8139too Fast Ethernet driver 0.9.28
[   18.304000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   18.304000] Uniform CD-ROM driver Revision: 3.20
[   18.460000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   18.460000] Socket status: 30000006
[   18.460000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   18.460000] cs: IO port probe 0xa000-0xafff: clean.
[   18.460000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   18.460000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   18.468000] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 17
[   18.468000] eth0: RealTek RTL8139 at 0xdc950000, 00:16:d4:8b:48:ac, IRQ 17
[   18.468000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   18.556000] input: PC Speaker as /class/input/input3
[   18.632000] eth0: link down
[   18.732000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   19.000000] cs: IO port probe 0x100-0x3af: clean.
[   19.004000] cs: IO port probe 0x3e0-0x4ff: clean.
[   19.004000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   19.004000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   19.004000] cs: IO port probe 0xa00-0xaff: clean.
[   19.160000] fuse init (API version 7.8)
[   19.360000] lp: driver loaded but no devices found
[   19.384000] Adding 995988k swap on /dev/disk/by-uuid/5584751f-3203-4897-a5fd-0d9ec322af91.  Priority:-1 extents:1 across:995988k
[   19.556000] EXT3 FS on sda6, internal journal
[   19.696000] NET: Registered protocol family 17
[   20.764000] kjournald starting.  Commit interval 5 seconds
[   20.764000] EXT3 FS on sda7, internal journal
[   20.764000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.812000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   20.888000] NTFS volume version 3.1.
[   25.348000] ACPI: Battery Slot [BAT1] (battery present)
[   25.488000] input: Power Button (FF) as /class/input/input4
[   25.492000] ACPI: Power Button (FF) [PWRF]
[   25.532000] input: Lid Switch as /class/input/input5
[   25.536000] ACPI: Lid Switch [LID]
[   25.572000] input: Power Button (CM) as /class/input/input6
[   25.576000] ACPI: Power Button (CM) [PWRB]
[   25.652000] No dock devices found.
[   25.664000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.676000] Using specific hotkey driver
[   25.692000] ibm_acpi: ec object not found
[   25.720000] ACPI: AC Adapter [ACAD] (on-line)
[   25.764000] pcc_acpi: loading...
[   31.484000] ppdev: user-space parallel port driver
[   32.340000] apm: BIOS not found.
[   32.492000] Bluetooth: Core ver 2.11
[   32.492000] NET: Registered protocol family 31
[   32.492000] Bluetooth: HCI device and connection manager initialized
[   32.492000] Bluetooth: HCI socket layer initialized
[   32.532000] Bluetooth: L2CAP ver 2.8
[   32.532000] Bluetooth: L2CAP socket layer initialized
[   32.660000] Bluetooth: RFCOMM socket layer initialized
[   32.660000] Bluetooth: RFCOMM TTY layer initialized
[   32.660000] Bluetooth: RFCOMM ver 1.8
[   34.640000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   62.344000] NET: Registered protocol family 10
[   62.344000] lo: Disabled Privacy Extensions
[   62.344000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.072000] ath0: no IPv6 routers present
[   99.460000] ath0: no IPv6 routers present

---

### Post by volkswagner on 2007-05-25
Bump
Am I beyond help?
Is this thread dead?
shall I start a new one?
Is there a better place to post?

I think there is a solution, hardware is detected, alsamixer is starting, volume slider works.  
Any advice is greatly appreciated.

---

### Post by volkswagner on 2007-05-25
just installed kmix
here i what i get when launched

eric@vista:~$ kmix
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by volkswagner on 2007-05-25
sorry, scratch last post.  Kmix now starts normal after changing pref>sound>device to hda

still no sound though

---

### Post by Ankit S. on 2007-05-25
I am also having trouble with what I think is the same sound card.

(Gateway T2060 model laptop)

Not getting any sound. I can change the volume but it has no effect on the speakers.

Any help would be appreciated.

---

### Post by irezumi_x on 2007-05-29
same here, exactly same card, same problem..

---

### Post by volkswagner on 2007-06-04
ok there seems to be a fix

see this thread
[http://ubuntuforums.org/showthread.php?t=452992&highlight=%5BSOLVED%5D+No+sound%3A+Toshiba+Satellite+a135-s2386]("http://ubuntuforums.org/showthread.php?t=452992&highlight=%5BSOLVED%5D+No+sound%3A+Toshiba+Satellite+a135-s2386")

---

### Post by damo79 on 2008-01-14
7.10 seems to be working but not until i typed alsamixer in prompt and scrolled to the speaker volume and turned it up did it work. changing it in the taskbar seemed to do nothing

---

