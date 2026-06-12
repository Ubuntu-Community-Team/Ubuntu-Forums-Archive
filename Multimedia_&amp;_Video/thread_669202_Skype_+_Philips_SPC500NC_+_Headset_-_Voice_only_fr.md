---
title: "Skype + Philips SPC500NC + Headset - Voice only from headset?"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by zeusalmighty on 2008-01-16
Hi, I want to use my Philips Webcam with Skype, only thing webcam doesn't work. The little light is on, but no feed from camorama, error message:

```
Could not connect to video device
```

Also, I want to be able to listen to any conversations from Skype, only through my headset, not through my speakers. Right now, no sound is playing from my headset, but the microphone works correctly.

I have an onboard SoundMAX AD1985 sound card, and a 5.1 surround system out of which I am currently using only 2.1. So of my three outputs I have:

1- Headset
2- Front - Left Speakers
3- Headset Mic.

Thanks!

---

### Post by linuxwizard on 2008-01-16
Which driver did you install for your webcam ? Here is a list of webcams that works for Skype
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by zeusalmighty on 2008-01-17
Thanks for the list.
My webcam is clearly not listed in there, but I would hope that it could be enabled, since the list isn't absolute...
```
lsmod | grep videodev
```
gives absolutely no output. Any ideas on the headset?

---

### Post by linuxwizard on 2008-01-17
Yes that list may not be complete and does not mean your cam will not work. But you didn't answer my question Have you installed a driver for that webcam ? If not looks like this is the driver you need
[http://saillard.org/linux/pwc/](http://saillard.org/linux/pwc/)

---

### Post by zeusalmighty on 2008-01-17
Thanks, but! I'm pretty much a noob and can't really figure out the instructions. The install.en file says I could compile the source myself, but my **make** command outputs a bunch of errors...what is it I'm supposed to do?

---

### Post by zeusalmighty on 2008-01-20
bump!

---

### Post by imon9 on 2008-01-20
can u "cut and paste" the error here?

the thing about compling from source is that u might need to install a few / a lot of associated library files which is only required for compiling (but not needed when u run the program)

so u need to fulfill this requirement by installing the library that is missing.... most of the time, if u already have the said version of required library, u are advised to installed the -dev version of it from synaptic, with that, ur compilation most probably will run fine

---

### Post by zeusalmighty on 2008-01-20
The manual says I should have the actual kernel source installed, but how do I do that?

Here it is!

```
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.o
In file included from /media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:69:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:166: error: variable &#8216;pwc_template&#8217; has initializer but incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field &#8216;owner&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field &#8216;name&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:168: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:168: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:169: error: unknown field &#8216;type&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:169: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:169: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:170: error: unknown field &#8216;hardware&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:170: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:170: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field &#8216;release&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:171: error: &#8216;video_device_release&#8217; undeclared here (not in a function)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:171: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:171: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:172: error: unknown field &#8216;fops&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:172: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:172: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:173: error: unknown field &#8216;minor&#8217; specified in initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:173: warning: excess elements in struct initializer
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:173: warning: (near initialization for &#8216;pwc_template&#8217;)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_isoc_init&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:921: warning: assignment from incompatible pointer type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;cd_to_pwc&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1019: warning: implicit declaration of function &#8216;to_video_device&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1019: warning: initialization makes pointer from integer without a cast
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1020: warning: implicit declaration of function &#8216;video_get_drvdata&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1020: warning: return makes pointer from integer without a cast
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_create_sysfs_files&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1062: warning: initialization makes pointer from integer without a cast
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1064: warning: implicit declaration of function &#8216;video_device_create_file&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_remove_sysfs_files&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1070: warning: initialization makes pointer from integer without a cast
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1072: warning: implicit declaration of function &#8216;video_device_remove_file&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_open&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1112: warning: implicit declaration of function &#8216;video_devdata&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1112: warning: initialization makes pointer from integer without a cast
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1117: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_close&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1231: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_read&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1292: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_poll&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1359: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_ioctl&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1375: warning: implicit declaration of function &#8216;video_usercopy&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_mmap&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1388: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;usb_pwc_probe&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1722: warning: implicit declaration of function &#8216;video_device_alloc&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1722: warning: assignment makes pointer from integer without a cast
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1730: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1731: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1732: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1733: warning: implicit declaration of function &#8216;video_set_drvdata&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1756: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1757: warning: implicit declaration of function &#8216;video_register_device&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1757: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1757: error: (Each undeclared identifier is reported only once
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1757: error: for each function it appears in.)
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1760: warning: implicit declaration of function &#8216;video_device_release&#8217;
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1765: error: dereferencing pointer to incomplete type
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;usb_pwc_disconnect&#8217;:
/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.c:1819: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
make[2]: *** [/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/media/space/Downloads/drivers/Linux/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

---

### Post by imon9 on 2008-01-20
if u need kernel source installed, just go to synaptic and look for:
linux-header...[insert current verion number]-generic-src (generally the one which say src at the back)

but i not sure if it is gonna work anyhow

actually, the thing about webcam driver is that the changes had to be written onto the kernel ...that is why they need to write the changes to your kernel source and replace the new kernel onto ur old kernel....

so the kernel version must be corresponding to the one your machine is using, k?

hope this helps

---

### Post by zeusalmighty on 2008-01-21
Thanks, I tried using the synaptic for getting that file, but it doesn't exist! I have this **linux-headers-2.6.22-14-generic** already installed, but make doesn't compile!

---

### Post by imon9 on 2008-01-21
i know u have linux-header installed, but what it did is to download a deb file to your computer and install it from there...so in shorted words, the "source"/source code is not downloaeded

what u will need is the source code version...search the synaptic for "kernel source"

---

### Post by zeusalmighty on 2008-01-21
Tried it, I found the** linux-source-2.6.22** and **linux-source** and installed both, but *sudo make* still doesn't compile!!! Anything more?

---

### Post by zeusalmighty on 2008-01-22
Well, I also tried installing gspca, but still, I can't use the make command! As far as I checked, I have all the necessary packages!

Camorama ansd xawtv get an error message saying they can't connect to** /dev/video0**, so I checked with dmesg and this is what I got:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 261936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261936
[    0.000000] On node 0 totalpages: 261936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32306 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9D90 checksum 0
[    0.000000] ACPI: RSDP 000F9D90, 0021 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3FF30100, 003C (r1 A M I  OEMXSDT   8000515 MSFT       97)
[    0.000000] ACPI: FACP 3FF30290, 00F4 (r3 A M I  OEMFACP   8000515 MSFT       97)
[    0.000000] ACPI: DSDT 3FF303F0, 382D (r1  P4P81 P4P81106      106 INTL  2002026)
[    0.000000] ACPI: FACS 3FF40000, 0040
[    0.000000] ACPI: APIC 3FF30390, 005C (r1 A M I  OEMAPIC   8000515 MSFT       97)
[    0.000000] ACPI: OEMB 3FF40040, 003F (r1 A M I  OEMBIOS   8000515 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Built 1 zonelists.  Total pages: 259890
[    0.000000] Kernel command line: root=UUID=d113d9ee-87f8-470c-b853-b790f1e89e57 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2998.663 MHz processor.
[   37.953292] Console: colour VGA+ 80x25
[   37.953667] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   37.954057] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   37.978570] Memory: 1027124k/1047744k available (2015k kernel code, 19952k reserved, 916k data, 364k init, 130240k highmem)
[   37.978579] virtual kernel memory layout:
[   37.978580]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   37.978582]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   37.978584]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   37.978584]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   37.978585]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   37.978586]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   37.978587]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   37.978590] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   37.978626] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   38.058535] Calibrating delay using timer specific routine.. 6001.90 BogoMIPS (lpj=12003807)
[   38.058560] Security Framework v1.0.0 initialized
[   38.058568] SELinux:  Disabled at boot.
[   38.058580] Mount-cache hash table entries: 512
[   38.058721] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   38.058732] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   38.058735] CPU: L2 cache: 512K
[   38.058737] CPU: Physical Processor ID: 0
[   38.058739] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   38.058749] Compat vDSO mapped to ffffe000.
[   38.058762] Checking 'hlt' instruction... OK.
[   38.074615] SMP alternatives: switching to UP code
[   38.075030] Early unpacking initramfs... done
[   38.340419] ACPI: Core revision 20070126
[   38.340465] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   38.353461] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   38.353479] SMP alternatives: switching to SMP code
[   38.353610] Booting processor 1/1 eip 3000
[   38.363749] Initializing CPU#1
[   38.441995] Calibrating delay using timer specific routine.. 5997.57 BogoMIPS (lpj=11995150)
[   38.442004] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   38.442014] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   38.442016] CPU: L2 cache: 512K
[   38.442018] CPU: Physical Processor ID: 0
[   38.442020] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   38.442175] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   38.442213] Total of 2 processors activated (11999.47 BogoMIPS).
[   38.442340] ENABLING IO-APIC IRQs
[   38.442519] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   38.589908] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   38.609897] Brought up 2 CPUs
[   38.653932] migration_cost=130
[   38.654107] Booting paravirtualized kernel on bare hardware
[   38.654177] Time:  8:25:08  Date: 00/22/108
[   38.654198] NET: Registered protocol family 16
[   38.654300] EISA bus registered
[   38.654306] ACPI: bus type pci registered
[   38.654372] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   38.654374] PCI: Using configuration type 1
[   38.654376] Setting up standard PCI resources
[   38.665246] ACPI: EC: Look up EC in DSDT
[   38.669638] ACPI: Interpreter enabled
[   38.669642] ACPI: (supports S0 S1 S3 S4 S5)
[   38.669665] ACPI: Using IOAPIC for interrupt routing
[   38.676478] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   38.676494] PCI: Probing PCI hardware (bus 00)
[   38.676951] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   38.676955] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   38.677511] PCI: Transparent bridge - 0000:00:1e.0
[   38.677537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   38.677639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   38.683635] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   38.683729] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   38.683820] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   38.683912] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   38.684003] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   38.684094] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   38.684188] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   38.684280] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   38.684384] Linux Plug and Play Support v0.97 (c) Adam Belay
[   38.684400] pnp: PnP ACPI init
[   38.684412] ACPI: bus type pnp registered
[   38.687860] pnp: PnP ACPI: found 12 devices
[   38.687863] ACPI: ACPI bus type pnp unregistered
[   38.687867] ASUS P4P800 detected. Disabling PnPBIOS
[   38.687869] PnPBIOS: Disabled
[   38.687942] PCI: Using ACPI for IRQ routing
[   38.687946] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   38.692169] NET: Registered protocol family 8
[   38.692172] NET: Registered protocol family 20
[   38.692278] pnp: 00:08: ioport range 0x680-0x6ff has been reserved
[   38.692281] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[   38.692288] pnp: 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   38.692291] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[   38.692297] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   38.692299] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[   38.692305] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   38.692308] pnp: 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[   38.692310] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   38.692313] pnp: 00:0b: iomem range 0x100000-0x3ffeffff could not be reserved
[   38.693669] Time: tsc clocksource has been installed.
[   38.722668] PCI: Bridge: 0000:00:01.0
[   38.722670]   IO window: disabled.
[   38.722675]   MEM window: f3d00000-f7dfffff
[   38.722679]   PREFETCH window: d3c00000-f3bfffff
[   38.722684] PCI: Bridge: 0000:00:1e.0
[   38.722687]   IO window: d000-dfff
[   38.722692]   MEM window: f7e00000-f7efffff
[   38.722696]   PREFETCH window: disabled.
[   38.722712] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   38.722725] NET: Registered protocol family 2
[   38.761709] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   38.761813] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   38.762624] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   38.763100] TCP: Hash tables configured (established 131072 bind 65536)
[   38.763104] TCP reno registered
[   38.773812] checking if image is initramfs... it is
[   39.224928] Switched to high resolution mode on CPU 0
[   39.225020] Switched to high resolution mode on CPU 1
[   39.304627] Freeing initrd memory: 7042k freed
[   39.305014] audit: initializing netlink socket (disabled)
[   39.305027] audit(1200990308.088:1): initialized
[   39.305154] highmem bounce pool size: 64 pages
[   39.307574] VFS: Disk quotas dquot_6.5.1
[   39.307633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   39.307738] io scheduler noop registered
[   39.307741] io scheduler anticipatory registered
[   39.307742] io scheduler deadline registered
[   39.307758] io scheduler cfq registered (default)
[   39.307843] Boot video device is 0000:01:00.0
[   39.308052] isapnp: Scanning for PnP cards...
[   39.661170] isapnp: No Plug & Play device found
[   39.689959] Real Time Clock Driver v1.12ac
[   39.690060] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.690147] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.690337] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.690983] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.691293] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.692130] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.692380] input: Macintosh mouse button emulation as /class/input/input0
[   39.692530] PNP: No PS/2 controller found. Probing ports directly.
[   39.695024] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.695033] serio: i8042 AUX port at 0x60,0x64 irq 12
[   39.695246] mice: PS/2 mouse device common for all mice
[   39.695386] EISA: Probing bus 0 at eisa.0
[   39.695426] EISA: Detected 0 cards.
[   39.695515] TCP cubic registered
[   39.695529] NET: Registered protocol family 1
[   39.695553] Using IPI No-Shortcut mode
[   39.695728]   Magic number: 8:841:422
[   39.696161] Freeing unused kernel memory: 364k freed
[   40.925487] AppArmor: AppArmor initialized<5>audit(1200990309.588:2):  type=1505 info="AppArmor initialized" pid=1193
[   40.932753] fuse init (API version 7.8)
[   40.938172] Failure registering capabilities with primary security module.
[   41.556872] usbcore: registered new interface driver usbfs
[   41.556914] usbcore: registered new interface driver hub
[   41.556959] usbcore: registered new device driver usb
[   41.558288] USB Universal Host Controller Interface driver v3.0
[   41.558366] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.558381] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   41.558386] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   41.558548] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   41.558579] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
[   41.558735] usb usb1: configuration #1 chosen from 1 choice
[   41.558778] hub 1-0:1.0: USB hub found
[   41.558786] hub 1-0:1.0: 2 ports detected
[   41.661446] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   41.661462] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   41.661468] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   41.661500] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   41.661529] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ef00
[   41.661663] usb usb2: configuration #1 chosen from 1 choice
[   41.661707] hub 2-0:1.0: USB hub found
[   41.661718] hub 2-0:1.0: 2 ports detected
[   41.663778] SCSI subsystem initialized
[   41.670414] libata version 2.21 loaded.
[   41.747998] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   41.748006] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   41.765295] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   41.765310] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   41.765316] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   41.765349] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   41.765378] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
[   41.765516] usb usb3: configuration #1 chosen from 1 choice
[   41.765556] hub 3-0:1.0: USB hub found
[   41.765566] hub 3-0:1.0: 2 ports detected
[   41.869110] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   41.869126] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   41.869131] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   41.869168] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   41.869194] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
[   41.869339] usb usb4: configuration #1 chosen from 1 choice
[   41.869386] hub 4-0:1.0: USB hub found
[   41.869395] hub 4-0:1.0: 2 ports detected
[   41.900925] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   41.973805] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   41.973829] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   41.973835] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   41.973892] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   41.973939] ehci_hcd 0000:00:1d.7: debug port 1
[   41.973949] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   41.973964] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7fff800
[   42.016797] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   42.016994] usb usb5: configuration #1 chosen from 1 choice
[   42.017040] hub 5-0:1.0: USB hub found
[   42.017054] hub 5-0:1.0: 8 ports detected
[   42.121206] VP_IDE: IDE controller at PCI slot 0000:02:04.0
[   42.121228] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 23 (level, low) -> IRQ 19
[   42.121243] VP_IDE: chipset revision 6
[   42.121257] VP_IDE: VIA vt6410 (rev 06) IDE UDMA133 controller on pci0000:02:04.0
[   42.121263] VP_IDE: 100% native mode on irq 19
[   42.121271]     ide0: BM-DMA at 0xdf90-0xdf97, BIOS settings: hda:pio, hdb:pio
[   42.121285]     ide1: BM-DMA at 0xdf98-0xdf9f, BIOS settings: hdc:pio, hdd:pio
[   42.121298] Probing IDE interface ide0...
[   42.424142] usb 1-1: device not accepting address 2, error -71
[   42.687762] Probing IDE interface ide1...
[   43.255005] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   43.307798] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[f7eff800-f7efffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   43.312985] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 21
[   43.313030] skge 1.11 addr 0xf7ef8000 irq 21 chip Yukon rev 1
[   43.313651] skge eth0: addr 00:0c:6e:92:fb:3a
[   43.313799] ata_piix 0000:00:1f.1: version 2.11
[   43.313817] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   43.313825] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   43.313875] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   43.314386] scsi0 : ata_piix
[   43.314469] scsi1 : ata_piix
[   43.314656] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fc00 irq 14
[   43.314662] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fc08 irq 15
[   43.582433] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   43.650705] ata1.00: ATA-6: ST340014A, 3.06, max UDMA/100
[   43.650709] ata1.00: 78165360 sectors, multi 16: LBA48 
[   43.650886] ata1.01: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[   43.650888] ata1.01: 80293248 sectors, multi 16: LBA 
[   43.666673] ata1.00: configured for UDMA/100
[   43.682630] ata1.01: configured for UDMA/133
[   43.760261] usb 2-1: configuration #1 chosen from 1 choice
[   44.001810] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   44.021966] ata2.01: ATAPI: CD-RW CR52, Ver 3.20, max UDMA/33
[   44.176590] usb 2-2: configuration #1 chosen from 1 choice
[   44.179664] usbcore: registered new interface driver hiddev
[   44.193714] ata2.01: configured for UDMA/33
[   44.193848] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.06 PQ: 0 ANSI: 5
[   44.194010] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[   44.194348] scsi 1:0:1:0: CD-ROM            MSI      CD-RW CR52       3.20 PQ: 0 ANSI: 5
[   44.194433] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   44.194453] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   44.194492] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   44.194551] scsi2 : ata_piix
[   44.194649] scsi3 : ata_piix
[   44.194689] ata3: SATA max UDMA/133 cmd 0x0001efe0 ctl 0x0001efae bmdma 0x0001ef90 irq 18
[   44.194694] ata4: SATA max UDMA/133 cmd 0x0001efa0 ctl 0x0001efaa bmdma 0x0001ef98 irq 18
[   44.417197] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   44.553144] ata4.00: ATA-7: ST3250620AS, 3.AAE, max UDMA/133
[   44.553148] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   44.581088] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800002ce51c]
[   44.628002] ata4.00: configured for UDMA/133
[   44.628131] scsi 3:0:0:0: Direct-Access     ATA      ST3250620AS      3.AA PQ: 0 ANSI: 5
[   44.640882] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   44.643345] sd 0:0:0:0: [sda] Write Protect is off
[   44.643351] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.643393] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.643493] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   44.643512] sd 0:0:0:0: [sda] Write Protect is off
[   44.643515] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.643545] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.643550]  sda:<6>usb 1-1: configuration #1 chosen from 1 choice
[   44.665367]  sda1 sda2 <<6>input: Logitech USB Receiver as /class/input/input1
[   44.668078] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   44.686729]  sda5 >
[   44.686856] sd 0:0:0:0: [sda] Attached SCSI disk
[   44.686963] sd 0:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   44.686980] sd 0:0:1:0: [sdb] Write Protect is off
[   44.686985] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   44.687011] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.687081] sd 0:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   44.687099] sd 0:0:1:0: [sdb] Write Protect is off
[   44.687103] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   44.687132] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.687138]  sdb: sdb1
[   44.688324] sd 0:0:1:0: [sdb] Attached SCSI disk
[   44.688501] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   44.688521] sd 3:0:0:0: [sdc] Write Protect is off
[   44.688525] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   44.688553] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.688726] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   44.688744] sd 3:0:0:0: [sdc] Write Protect is off
[   44.688748] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   44.688923] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.688928]  sdc:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   44.691024] Uniform CD-ROM driver Revision: 3.20
[   44.691079] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   44.700075] input: Logitech USB Receiver as /class/input/input2
[   44.700116] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   44.700146] usbcore: registered new interface driver usbhid
[   44.700151] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   44.755874]  [LDM] sdc1
[   44.756244] sd 3:0:0:0: [sdc] Attached SCSI disk
[   44.764156] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.764387] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   44.764607] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   44.764867] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   45.108612] Attempting manual resume
[   45.108616] swsusp: Resume From Partition 8:5
[   45.108617] PM: Checking swsusp image.
[   45.108951] PM: Resume from disk failed.
[   45.147684] kjournald starting.  Commit interval 5 seconds
[   45.147697] EXT3-fs: mounted filesystem with ordered data mode.
[   52.491140] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.541733] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.813656] input: PC Speaker as /class/input/input3
[   52.819498] intel_rng: FWH not detected
[   52.827785] parport_pc 00:07: reported by Plug and Play ACPI
[   52.827888] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   52.892048] iTCO_vendor_support: vendor-support=0
[   52.893465] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   52.991954] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   52.992032] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   53.102508] Linux agpgart interface v0.102 (c) Dave Jones
[   53.262601] input: Wacom Graphire as /class/input/input4
[   53.268731] usbcore: registered new interface driver wacom
[   53.268739] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   53.443271] agpgart: Detected an Intel 865 Chipset.
[   53.446903] agpgart: AGP aperture is 64M @ 0xf8000000
[   53.480010] nvidia: module license 'NVIDIA' taints kernel.
[   53.733989] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.734200] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   54.076490] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   54.076516] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   54.498265] intel8x0_measure_ac97_clock: measured 52098 usecs
[   54.498270] intel8x0: clocking to 48000
[   55.503618] lp0: using parport0 (interrupt-driven).
[   55.575244] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   55.852759] EXT3 FS on sda1, internal journal
[   56.885717] No dock devices found.
[   56.940879] input: Power Button (FF) as /class/input/input5
[   56.940906] ACPI: Power Button (FF) [PWRF]
[   56.941012] input: Power Button (CM) as /class/input/input6
[   56.941035] ACPI: Power Button (CM) [PWRB]
[   58.464835] ppdev: user-space parallel port driver
[   58.730839] audit(1200990328.291:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4935 profile="/usr/sbin/cupsd"
[   58.804978] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   58.804985] apm: disabled - APM is not SMP safe.
[   59.012859] Failure registering capabilities with primary security module.
[   59.227828] Bluetooth: Core ver 2.11
[   59.228006] NET: Registered protocol family 31
[   59.228011] Bluetooth: HCI device and connection manager initialized
[   59.228016] Bluetooth: HCI socket layer initialized
[   59.253631] Bluetooth: L2CAP ver 2.8
[   59.253638] Bluetooth: L2CAP socket layer initialized
[   59.346498] Bluetooth: RFCOMM socket layer initialized
[   59.346653] Bluetooth: RFCOMM TTY layer initialized
[   59.346658] Bluetooth: RFCOMM ver 1.8
[   62.196398] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   62.196415] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   62.196450] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  136.718358] NET: Registered protocol family 10
[  136.718525] lo: Disabled Privacy Extensions
[  305.709839] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  305.709858] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  305.709893] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  458.212608] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  458.212627] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  458.212661] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  582.723128] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  582.723150] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  582.723186] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  614.946017] skge eth0: enabling interface
[  614.953515] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  616.758853] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[  616.763821] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  616.998710] NET: Registered protocol family 17
[  627.545520] eth0: no IPv6 routers present
[ 4452.508548] usb 1-1: USB disconnect, address 4
[ 4467.765755] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 4467.999463] usb 1-1: configuration #1 chosen from 1 choice
```

Also, I checked in Hardware Information, and found my webcam, it was registered as a **VGA Single Chip**, **USB Vendor Specific Interface** and under **USB Raw Device Access**, I found an entry *linux.device.file* with a value of **/dev/bus/usb/001/005**. The entry *usbraw.device* also had the same value.

Is this actually helping or am I just throwing pointless information at you?

---

### Post by imon9 on 2008-01-22
actually, i felt a bit not helpful to u at the moment, i hipe someone could jump in to help

anyway, just curious, what program are u trying/tried to use ur webcam with?

---

### Post by zeusalmighty on 2008-01-22
Mostly skype, but for starters, I just want to see any kind of input from my webcam...!

---

### Post by zeusalmighty on 2008-01-22
I followed this post: [http://ubuntuforums.org/showpost.php?p=4181180&postcount=43]("http://ubuntuforums.org/showpost.php?p=4181180&postcount=43"), and it worked for a while, even though it was only 320*240 and completely dark (you can see the attached image below that post). But now it has completely stopped working. I used "make" on the file the poster gave a link to and make worked. The driver does not work anymore though...

---

### Post by imon9 on 2008-01-22
sorry, just to try something out, install this program:

and lemme know if ur webcam works with it :)
[http://jagbox.com/dnwcpl](http://jagbox.com/dnwcpl)

---

### Post by imon9 on 2008-01-22
btw, just for ur knowledge, i used to have v4l webcam, but now mine is v4l2 (uvc)..so it is kindda hard for me to recall

---

### Post by zeusalmighty on 2008-01-22
I'm sorry if I sound rude, but the file you're having me download seems a bit shady. What is it and why is it posted at such a site?

---

### Post by imon9 on 2008-01-22
oh...sorry for that, coz that is just a temporary file hosting site..

anyway, if u feel unsecure about it...try look for "cheese" in synaptic...coz i know it is in hardy and gutsy repositories, not sure about feisty and earlier tho

---

### Post by zeusalmighty on 2008-01-22
Sorry about that, but you never know...I always prefer using the repos... I tried cheese, thanks, but it doesn't work! It says there is no camera connected!

---

### Post by imon9 on 2008-01-23
dun worry about that, anyway, i finally got some time to do a search....
it seem ur webcam should not use thw pwc/uvc driver which u had error compiling earlier

u need the latest gspcav driver... try get it from the link below:
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

and complie it

---

### Post by imon9 on 2008-01-23
here's the link saying ur camshould use gspcav
[http://wiki.ubuntu.org.cn/UbuntuWiki:HardwareSupportComponentsMultimediaWebCamerasPhilips](http://wiki.ubuntu.org.cn/UbuntuWiki:HardwareSupportComponentsMultimediaWebCamerasPhilips)

and pls post ur "sudo lsusb" here (with ur webcam attached of cource)

---

### Post by imon9 on 2008-01-23
oh yes, u only mentioned "make" command, i hope u know that usually before the "make" command, one need to first run "./configure"

disregard if u already knew... most linux user did

---

### Post by zeusalmighty on 2008-01-23
I followed the guide found here: [http://ubuntuforums.org/showpost.php?p=4181180&postcount=43]("http://ubuntuforums.org/showpost.php?p=4181180&postcount=43") but no ./configure command is available, I tried it, I get a ```
bash: ./configure: No such file or directory
```

Eitherway, I followed through with the install and the webcam was indeed installed. The problem is, it's really dark, as in REALLY dark, chek the post below the one I gave you to see an example. Plus, later on it stopped working at all.

This is is lsusb output:

```
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 093a:2603 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 056a:0010 Wacom Co., Ltd Graphire
Bus 002 Device 004: ID 046d:c512 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

The Pixart Imaging is ofcourse the webcam...

---

### Post by imon9 on 2008-01-23
seems like ur model support in linux is really poor...i guess there is no help to install anything unless there is a fix/workaround somewhere

try borrow another webcam from a fren and play with it,k?

---

### Post by zeusalmighty on 2008-01-23
> 
try borrow another webcam from a fren and play with it,k?

:lolflag: that sounded sooo weird! As I read in the site you sent me, indeed support for this camera is really bad. I guess I'll just be patient until they roll out some new drivers maybe.

---

### Post by zeusalmighty on 2008-02-01
bump!

Having Skype audio only from Headset on a 5.1 embedded sound card?

---

