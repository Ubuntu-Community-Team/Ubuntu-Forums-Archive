---
title: "Usb dvb-t tuner captured as keyboard"
date: 2012-07-07
forum: Mythbuntu
---

### Post by donkeyX on 2012-07-07
Hey Guys, 

I have been reading many forums and tried a few things but still no luck basically because I have no idea what I am doing ;). Anyway, as far as I can tell my usb ITE tuner is being recognized as a keyboard. This is a message from my dmesg output and I have tried adding the quirks to grub and the usbhid.conf file with no luck. The last attempt was 10-lirc.rules which did not work either. I am suspecting that I am just missing something simple but have had no luck finding it, that is why I am here. 

tried. 
```
vi /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="usbhid.quirks=0x048D:0x9006:0x0004" #quiet splash"

```

tried. 
```
vi /etc/modprobe.d/usbhid.conf
options usbhid quirks=0x048D:0x9006:0x0004

```

latest
```
cat /etc/udev/rules.d/10-lirc.rules
ATTRS{idVendor}=="048D", ATTRS{idProduct}=="9006", OPTIONS=="ignore_device"

```

message seems the same every time I restart.
```

[    2.836158] input: ITE Technologies, Inc. DVB-T TV Stick as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.1/input/input3
[    2.836278] generic-usb 0003:048D:9006.0002: input,hidraw1: USB HID v1.01 Keyboard [ITE Technologies, Inc. DVB-T TV Stick] on usb-0000:00:12.2-5/input1

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 048d:9006 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 048d:9006 Integrated Technology Express, Inc. 
Bus 003 Device 002: ID 2040:9950 Hauppauge WinTV Nova-T-500
Bus 006 Device 002: ID 15c2:0038 SoundGraph Inc. GD01 MX LCD Display/IR Receiver
Bus 007 Device 002: ID 045e:00e3 Microsoft Corp. 

```
```

uname -a
Linux myth 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Any help would be appreciated or even a point in the right direction.

---

### Post by bo.vestergaard on 2013-07-02
I have the same problem. Here is the output from dmesg.

bo@Compaq-laptop:~$ dmesg | grep -i dvb
[  171.071649] input: ITE Technologies, Inc. DVB-T TV Stick as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.1/input/input10
[  171.071827] generic-usb 0003:048D:9006.0001: input,hidraw0: USB HID v1.01 Keyboard [ITE Technologies, Inc. DVB-T TV Stick] on usb-0000:00:1d.7-3/input1
bo@Compaq-laptop:~$ 

Even if I manually copy the firmware file into /lib/firmware it does not load it because it thinks it is a keyboard.

Any suggestions would be appreciated.

---

### Post by BicyclerBoy on 2013-07-02
You need kernel 3.3 or later
[http://www.linuxtv.org/wiki/index.php/ITE_IT9135](http://www.linuxtv.org/wiki/index.php/ITE_IT9135)

You can upgrade the kernel in your *buntu without having to upgrade disto etc.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

_Or_ you have to build v4l-dvb module (only).
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
follow the basic novice instructions.

The OP should purge the changes made to grub/modprobe.d files etc..

---

