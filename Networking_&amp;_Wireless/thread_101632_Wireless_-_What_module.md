---
title: "Wireless - What module?"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by martymart on 2005-12-10
I install Ubuntu and it found and installed the correct modules, and my wireless card worked fine.
After a few days my wireless card stopped working! I ran the following commands and it seems that the module is no longer running.

sudo lshw -C network:
	network:0 UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: a
       bus info: pci@00:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: ioport:d000-d01f iomemory:dfffe000-dfffefff iomemory:dffe0000-dffeffff irq:10

lspci -v:
	0000:00:0a.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
        Subsystem: Global Sun Technology Inc: Unknown device 8501
        Flags: medium devsel, IRQ 10
        I/O ports at d000 [size=32]
        Memory at dfffe000 (32-bit, non-prefetchable) [size=4K]
        Memory at dffe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>
lscpi -n:
	0000:00:0a.0 0280: 104c:8400 - Note that there is no rev num.

As you can see that the card has been detected but no module is loaded! The wireless card is an ACX100 base card, which I have also had working in Slackware. I tried sudo modprobe acx100, but Fatal: Module acx100 not found, is returned. Now I just guessed at the module name, so this is most probably wrong, but if it is not wrong how to I get the module and install it? I also tried sudo modprobe PCI : acx100_pci.o, but that did not work either.

I also check etc/modules which only contains:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

Any help as what to do next would be most helpfull.

Thanks Martin

---

### Post by Lambert on 2005-12-10
try

sudo modprobe acx_pci

---

### Post by martymart on 2005-12-10
The command works fine thanks. But iwconfig shows no wireless devices. dmesg | grep acx gives me the following errors:
[4294701.586000] acx100: It looks like you've been coaxed into buying a wireless network card
[4294701.586000] acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
[4294701.586000] acx100: You should better have bought e.g. a PRISM(R) chipset based card,
[4294701.586000] acx100: since that would mean REAL vendor Linux support.
[4294701.586000] acx100: Given this info, it's evident that this driver is still EXPERIMENTAL,
[4294701.586000] acx100: thus your mileage may vary. Reading README file and/or Craig's HOWTO is
[4294701.586000] recommended, visit [http://acx100.sf.net](http://acx100.sf.net) in case of further questions/discussion.
[4294701.586000] acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode
[4294701.586000] acx_init_module: dev_info is: TI acx_pci
[4294701.586000] acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 driver initialized, waiting for cards to probe...
[4294701.595000] acx_select_io_register_set: using ACX100 io resource addresses (size: 56)
[4294701.595000] acx_probe_pci: TI acx_pci: Using IRQ 10
[4294701.595000] acx_reset_mac: enable soft reset...
[4294701.595000] acx_reset_mac: disable soft reset and go to init mode...
[4294701.771000] acx_read_fw FAILED
[4294701.771000] acx_reset_dev: Failed to upload firmware to the ACX1xx
[4294701.771000] acx_probe_pci: TI acx_pci: MAC initialize failure!
[4294701.799000] acx_probe_pci: TI acx_pci.o: Ver 0.2.0pre8 loading FAILED
[4294701.799000] acx_pci: probe of 0000:00:0a.0 failed with error -5

The card does not show up on the ifconfig either. sudo lshw -C network
 still says that the card is not claimed.

sudo lsmod |grep acx gives me:

acx_pci               122752  0
firmware_class          9472  1 acx_pci

There are no modules listed in the blacklist file. I have just added acx_pci to 
/etc/modules and am going to restart now to see if this helps.

Any other advice guys and girls?

Thanks Martin.

---

### Post by Lambert on 2005-12-10
This chipset and driver does seem to have problems in linux. Look here to see if you can find anymore help.

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

### Post by altu on 2008-01-17
I have the same exact card and I couldn't get it to run no matter what I did, the information on [http://acx100.sourceforge.net/wiki](http://acx100.sourceforge.net/wiki) is quite limited. Does anybody know of a step by step guide anywhere for installing this card?

---

