---
title: "ATI Switchable graphics"
date: 2010-05-09
forum: Multimedia Software
---

### Post by Bernardobr on 2010-05-09
Hello, I have an Acer 3280TG which has ATI Switable Graphics, intel integrated graphics card and ATI HD5650. 
I would like to -always- use intel integrated on linux and apparently I'm using the HD5650 because my battery is taking a major hit, only lasting 2h10 instead of 4h on windows. Plus, even though the brightness key commands work, there is no difference in the screen real brightness. I can set brightness to the minimum and it will be at the maximum. Any ideas?

By the way, after installing the ATI proprietary drivers I get a black screen after the splash screen of ubuntu, to get ubuntu back I have to delete the X11 conf file.

Thanks in advance


> bernardo@bernardo:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: afe00000-afefffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 0365
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0804000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0806000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000f0a00000-00000000f0bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0500000-f05fffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000a01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0807000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0f, subordinate=0f, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 31
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 1820 [size=32]
	Memory at f0808000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: medium devsel, IRQ 10
	Memory at f0809000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1840 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: fast devsel, IRQ 10
	Memory at f080a000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
	Subsystem: Acer Incorporated [ALI] Device 0365
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at b0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Memory at afee0000 (64-bit, non-prefetchable) [disabled] [size=128K]
	I/O ports at 2000 [disabled] [size=256]
	[virtual] Expansion ROM at afe00000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
	Subsystem: Acer Incorporated [ALI] Device 0365
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at afedc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]
	Capabilities: <access denied>

05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e01f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0500000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0


---

### Post by tschinz on 2010-06-21
Hi Bernard,

perhaps it a late respond but i got the same laptop with the same problem. And i found out that you can choose between switchable and discrete graphic mode ind the bios. If you activate Discrete it works in ubuntu with ati drivers. The problem is that on windows you cant use the I5 graphic card anymore..

do you have found a better solution?

Thanks in advance

tschinz

---

### Post by adpads on 2010-09-13
Hi guys,
I know this post is months old, but I just came across it. I got the same laptop a few weeks ago, and I have been a little more successful in getting it to work. I have been meaning to post a howto to help others but haven't gotten around to it yet.

1) For the switchable graphics issue, I used a modified version of a kernel module originally written for a Lenovo with switchable graphics. The module uses ACPI calls to cut the power to the discrete graphics card. This manages to reduce my power consumption from 30-36 watts to about 12-18 watts, but then you can't use the ATI's sound card either and have to go with the analogue sound in and out.
I found the code for the module in this thread: [http://ubuntuforums.org/showthread.php?t=1242590&page=7]("http://ubuntuforums.org/showthread.php?t=1242590&page=7")

Here is the module:
```
/* 
 * timelinex_acpi.c
 * 
 * Linux kernel module that disables the discrete graphics board for Acer
 * Aspire TimelineX 3820TG (Core i5). Other TimelineX laptops could work, but I don't know.
 *
 * Based on the original lenovo_acpi.c by Sylvain Joyeux <sylvain.joyeux@m4x.org>, 2009
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle); //     status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("timelinex_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("timelinex_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 0; //     atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("timelinex_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("timelinex_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy); 
```
And the makefile:
```
ifneq ($(KERNELRELEASE),)
  obj-m := timelinex_acpi.o
else
  KERNELDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif
```
-Save the files in the same directory; navigate to the directory in terminal.
Then issue these commands:
make
sudo cp timelinex_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod
echo timelinex_acpi | sudo tee -a /etc/modules > /dev/null

and reboot.
Some people using variants of this method report that they get a blank screen at boot before the login screen. I get this sometimes, but then a reboot solves it, so I guess there is some kind of race condition whereby the Intel card doesn't always get control of the screen before the module shuts off the Radeon card.

2) for the brightness issue: 
I found some various approaches to this issue in the following thread:
[http://ubuntuforums.org/showthread.php?t=1481995&highlight=3820TG]("http://ubuntuforums.org/showthread.php?t=1481995&highlight=3820TG")

The one which worked for me was:

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX="" into

GRUB_CMDLINE_LINUX="acpi_osi=Linux"

then run

sudo update-grub

I did a little monkeying around with putting that in various places in the grub; for me, putting it in the GRUB_CMDLINE_LINUX_DEFAULT= line did not work.

I will eventually write a HOWTO for others with this laptop.
Hope it helps!

---

