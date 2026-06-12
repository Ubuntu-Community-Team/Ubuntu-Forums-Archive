---
title: "Thinkpad X201i WWAN 3G Card"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by nukleuzN on 2011-05-29
Hi,

As mentioned; I have a Thinkpax X201i, and i assume that the 3G card that is installed is a GOBI 2000. That is what "Google told me" ;)

Just installed Ubuntu **11.04** - again - after several different try-outs from the *worldwideweb*, on how to fix the drivers.

 - Without any luck. :-(

I have read that the driver has been broken, or something, since Ubuntu 10.10 (or was it 10.04?). That I dont know for sure, because I never tried to fix this problem in that version.

-

Now I need help to get this fixed. Just bougth a Broadband 3G SIM.

Since I have tried several solutions, with no luck, I now have a clean Ubuntu install. Which means that I haven't installed any *Windows drivers from Lenovo Support* etc, yet.

Here are some outputs!

> **"$ lsusb said:**
> 
```
Bus 002 Device 003: ID 04fc:05da Sunplus Technology Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 1004:618e LG Electronics, Inc. 
Bus 001 Device 004: ID 17ef:4816 Lenovo 
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```


> **"$ ls /dev/tty*"]
```
/dev/tty    /dev/tty23  /dev/tty39  /dev/tty54      /dev/ttyS1   /dev/ttyS25
/dev/tty0   /dev/tty24  /dev/tty4   /dev/tty55      /dev/ttyS10  /dev/ttyS26
/dev/tty1   /dev/tty25  /dev/tty40  /dev/tty56      /dev/ttyS11  /dev/ttyS27
/dev/tty10  /dev/tty26  /dev/tty41  /dev/tty57      /dev/ttyS12  /dev/ttyS28
/dev/tty11  /dev/tty27  /dev/tty42  /dev/tty58      /dev/ttyS13  /dev/ttyS29
/dev/tty12  /dev/tty28  /dev/tty43  /dev/tty59      /dev/ttyS14  /dev/ttyS3
/dev/tty13  /dev/tty29  /dev/tty44  /dev/tty6       /dev/ttyS15  /dev/ttyS30
/dev/tty14  /dev/tty3   /dev/tty45  /dev/tty60      /dev/ttyS16  /dev/ttyS31
/dev/tty15  /dev/tty30  /dev/tty46  /dev/tty61      /dev/ttyS17  /dev/ttyS4
/dev/tty16  /dev/tty31  /dev/tty47  /dev/tty62      /dev/ttyS18  /dev/ttyS5
/dev/tty17  /dev/tty32  /dev/tty48  /dev/tty63      /dev/ttyS19  /dev/ttyS6
/dev/tty18  /dev/tty33  /dev/tty49  /dev/tty7       /dev/ttyS2   /dev/ttyS7
/dev/tty19  /dev/tty34  /dev/tty5   /dev/tty8       /dev/ttyS20  /dev/ttyS8
/dev/tty2   /dev/tty35  /dev/tty50  /dev/tty9       /dev/ttyS21  /dev/ttyS9
/dev/tty20  /dev/tty36  /dev/tty51  /dev/ttyACM0    /dev/ttyS22
/dev/tty21  /dev/tty37  /dev/tty52  /dev/ttyprintk  /dev/ttyS23
/dev/tty22  /dev/tty38  /dev/tty53  /dev/ttyS0      /dev/ttyS24
```
[/QUOTE]

[QUOTE="$ cat /sys/class/tty/*/device/modalias|uniq"]
```
usb:v1004p618Ed9999dcE0dsc00dp00ic02isc02ip01
platform:serial8250
```
[/QUOTE]

[QUOTE="$ ls /sys/devices/platform/qcserial"]
```
ls: cannot access /sys/devices/platform/qcserial: No such file or directory
```
[/QUOTE]

[QUOTE="$ find /sys/module/qcserial/"]
```
find: `/sys/module/qcserial/': No such file or directory
```
[/QUOTE]

[QUOTE="$ dmesg|grep qcserial"]// returns nothing[/QUOTE]
[QUOTE="$ lsusb | grep -i 5c6"]// returns nothing[/QUOTE]
[QUOTE="$ sudo rmmod qcserial said:**
> 
```
ERROR: Module qcserial does not exist in /proc/modules
```

[QUOTE="$ dmesg - |grep qcserial"]
```
[ 3426.019268] usbcore: registered new interface driver qcserial
```[/QUOTE]

[QUOTE="$ sudo apt-cache search gobi"]
```
gobi-loader - Firmware loader for Qualcom GobiUSB chipsets
ggobi - Data visualization system for high-dimensional data
r-cran-rggobi - GNU R package for the GGobi data visualization system
```
[/QUOTE]

I have tried to install  the gobi_loader, with no luck. Have also tried out *gobi_loader-tp* from *linrunner's repo*, within the *thinkpad-extras pack*.

I can mention that this solutions is followed:
[LIST=1]
[*][http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000](http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000)
[*][http://ubuntuforums.org/showthread.php?t=1593581](http://ubuntuforums.org/showthread.php?t=1593581)
[/LIST]

Anyone with some ideas how to fix this?

---

