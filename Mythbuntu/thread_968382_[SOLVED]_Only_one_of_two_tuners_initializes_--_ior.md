---
title: "[SOLVED] Only one of two tuners initializes -- ioremap failed error (vmalloc)"
date: 2008-11-02
forum: Mythbuntu
---

### Post by GJH15 on 2008-11-02
Hello,
 
I have two Hauppuage HVR-1600 installed but Mythbuntu only recognizes one at a time.  I put each in one at a time and they both work individually.  When I put both in, only one is recognized.  I have /dev/video0 but not /dev/video1.  Any suggestions would be greatly appreciated.
 
I pasted contents from /var/log/dmesg.  It looks like cx18-0 initializes successfully and I have a problem with cx18-1.
 
 Linux video capture interface: v2.00
 nvidia: module license 'NVIDIA' taints kernel.
 cx18:  Start initialization, version 1.0.1
 cx18-0: Initializing card #0
 cx18-0: Autodetected Hauppauge card
 ACPI: PCI Interrupt Link [APC1]enabled at IRQ 16
 ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 20
 cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
 cx18-0: cx23418 revision 01010000 (B)
 tveeprom 2-0050: Hauppauge model 74021, rev C1B2, serial# 1567508
 tveeprom 2-0050: MAC address is 00-0D-FE-17-EB-14
 tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
 tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
 tveeprom 2-0050: audio processor is CX23418 (idx 38)
 tveeprom 2-0050: decoder processor is CX23418 (idx 31)
 tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
 cx18-0: Autodetected Hauppauge HVR-1600
 cx18-0: VBI is not yet supported
 ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
 ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 22 (level, high) -> IRQ 16
 PCI: Setting latency timer of device 0000:00:06.0 to 64
 tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
 cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
 intel8x0_measure_ac97_clock: measured 52836 usecs
 intel8x0: clocking to 47404
 tuner-simple 3-0061: creating new instance
 tuner-simple 3-0061: type set to 50 (TCL 2002N)
 cx18-0: Disabled encoder IDX device
 cx18-0: Registered device video0 for encoder MPEG (2 MB)
 DVB: registering new adapter (cx18)
 MXL5005S: Attached at address 0x63
 DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
 cx18-0: DVB Frontend registered
 cx18-0: Registered device video32 for encoder YUV (2 MB)
 cx18-0: Registered device video24 for encoder PCM audio (1 MB)
 cx18-0: Initialized card #0: Hauppauge HVR-1600
[COLOR="Red"] cx18-1: Initializing card #1
 cx18-1: Autodetected Hauppauge card
 ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
 ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 21
 cx18-1: Unreasonably low latency timer, setting to 64 (was 32)
 allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
 cx18-1: ioremap failed, perhaps increasing __VMALLOC_RESERVE in page.h
 cx18-1: or disabling CONFIG_HIGHMEM4G into the kernel would help
 cx18-1: Error -12 on initialization
 cx18: probe of 0000:01:07.0 failed with error -12
 cx18:  End initialization[/COLOR]

---

### Post by GJH15 on 2008-11-03
I've been scouring the Internet looking for help with my problem.  I found a posting at:

[INDENT][http://www.spinics.net/lists/linux-dvb/msg29645.html](http://www.spinics.net/lists/linux-dvb/msg29645.html)
...I swopped-out hard drives and installed Mythbuntu. After installing the cx18 drivers it also only initialized one card. I then modified the bootloader with "vmalloc=256M" and it worked like a champ. ...[/INDENT]

I'm not sure where the bootloader is located and how risky it is to edit so I continued searching for information on editing the bootloader.  I couldn't find anything.  I have a 640GB hard drive.

I also ran the suggested command, "cat /proc/meminfo | grep Vmalloc" and got the following results:
[INDENT]VmallocTotal:   114680 kB
VmallocUsed:    101208 kB
VmallocChunk:    11764 kB[/INDENT]
Can anybody give me guidance on the steps I need to take?

Thanks,
Greg

---

### Post by ian dobson on 2008-11-03
Hi,

Grub is your bootloader, so to test you can bootup press escape whn the grub countdown appears on the screem. You can then add the vmalloc=XXX to your boot commands. This is only temporary and will not survive a reboot.

When you've found the correct value you can edit /boot/grub/menu.lst and add the vmalloc=XXX to the boot command line.

Regards
Ian Dobson

---

### Post by GJH15 on 2008-11-04
Thanks Ian.  I took your suggestions along with suggestions on another user list and was able to get both cards working.

Greg

[INDENT]**Steps shown below:**

Under Mythbuntu 8.04 and 8.10 you can edit the /boot/grub/menu.lst file. Look for a line that starts with:
# kopt=UUID=[followed by a long string of random characters]

At the end of the # kopt line add your vmalloc=256M setting. So for my system the completed line would be:

# kopt=root=UUID=2ef2c79b-0495-4a52-9d59-a83e5a870371 ro vmalloc=256M

This will preserve the change for any later kernels that get installed.  Also want to add the option to the current default kernel. Look further down in the file for a section that looks like this:

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.27-7-generic
root=UUID=2ef2c79b-0495-4a52-9d59-a83e5a870371 ro quiet splash
initrd          /initrd.img-2.6.27-7-generic
quiet

*note: the kernel line above is wrapped by mail reader*

At the end of the root= line add the vmalloc=256M setting.

Reboot the machine.[/INDENT]

---

### Post by ian dobson on 2008-11-04
Hi,

good to see the problem is solved. Could you please mark the thread as solved. So anyone else with the same problem will have less problems searching for a solution.

Regards
Ian Dobson

---

