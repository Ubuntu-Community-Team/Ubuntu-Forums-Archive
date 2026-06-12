---
title: "Fresh ubuntu install and wireless card issues"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by king0 on 2009-08-22
I'm new to ubuntu/linx, and I just installed ubuntu server 8.04. My wireless card - Dlink dwl-650+ - is not working. From my reading, [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink) it should work out of the box. However, when I go to system > administration > hardware drivers, the console informs me that there no proprietary drivers. Anyone know how have the driver - acx100 - install/load? Thanks.[URL="https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"]
[/URL]

---

### Post by Cuba71 on 2009-08-22
There's information on that driver at [http://acx100.sourceforge.net/]("http://acx100.sourceforge.net/")

---

### Post by king0 on 2009-08-22
I tried following the instructions, however, I continue to not be able to use my wireless card. Anyone know where I went wrong? Thanks.

When I run ```
dmesg | grep acx
``` I get the following -
> dan@devserv:~$ dmesg | grep acx
[ 6330.232036] acx: Loaded combined PCI/USB driver, firmware_ver=default
[ 6330.232043] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[ 6330.232188] acx: found ACX100-based wireless network card at 0000:05:00.0, irq:10, phymem1:0x40010000, phymem2:0x40000000, mem1:0xe09d6000, mem1_size:4096, mem2:0xe0b80000, mem2_size:65536
[ 6330.233221] acx: loading firmware for acx100 chipset with radio ID 0D
[ 6330.254114] acx: firmware image 'acx/default/tiacx100c0D' was not provided. Check your hotplug scripts
[ 6330.259456] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[ 6330.259464] acx: reset_dev() FAILED
[ 6330.273208] acx_pci: probe of 0000:05:00.0 failed with error -5
[ 6330.273285] usbcore: registered new interface driver acx_usb
[17555.838519] acx: found ACX100-based wireless network card at 0000:03:00.0, irq:11, phymem1:0x38010000, phymem2:0x38000000, mem1:0xe0aa6000, mem1_size:4096, mem2:0xe0ce0000, mem2_size:65536
[17555.839551] acx: loading firmware for acx100 chipset with radio ID 0D
[17555.918488] acx: firmware image 'acx/default/tiacx100c0D' was not provided. Check your hotplug scripts
[17555.941331] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[17555.941343] acx: reset_dev() FAILED
[17555.963180] acx_pci: probe of 0000:03:00.0 failed with error -5
[17563.933516] acx: found ACX100-based wireless network card at 0000:05:00.0, irq:10, phymem1:0x40010000, phymem2:0x40000000, mem1:0xe0aa6000, mem1_size:4096, mem2:0xe0ce0000, mem2_size:65536
[17563.934545] acx: loading firmware for acx100 chipset with radio ID 0D
[17563.956525] acx: firmware image 'acx/default/tiacx100c0D' was not provided. Check your hotplug scripts
[17563.975577] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[17563.975590] acx: reset_dev() FAILED
[17563.993140] acx_pci: probe of 0000:05:00.0 failed with error -5
[17571.190200] acx: found ACX100-based wireless network card at 0000:05:00.0, irq:10, phymem1:0x40010000, phymem2:0x40000000, mem1:0xe0aa6000, mem1_size:4096, mem2:0xe0ce0000, mem2_size:65536
[17571.191226] acx: loading firmware for acx100 chipset with radio ID 0D
[17571.243213] acx: firmware image 'acx/default/tiacx100c0D' was not provided. Check your hotplug scripts
[17571.262523] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[17571.262536] acx: reset_dev() FAILED
[17571.279825] acx_pci: probe of 0000:05:00.0 failed with error -5
Running: ```
iwinconfig
``` returns -
> dan@devserv:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.


---

