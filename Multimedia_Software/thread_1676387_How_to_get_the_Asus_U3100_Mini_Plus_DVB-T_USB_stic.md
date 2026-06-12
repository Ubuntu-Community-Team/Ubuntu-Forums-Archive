---
title: "How to get the Asus U3100 Mini Plus DVB-T USB stick to install properly?"
date: 2011-01-27
forum: Multimedia Software
---

### Post by snej on 2011-01-27
Hi all,

I am trying to get the Asus "My Cinema-U3100 Mini plus" DVB-T USB stick to work on my lucid 32bit with 2.6.32-27 kernel - with no great success so far. And this despite searching through forums and following the instructions given on **[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)**

The USBID is in fact ```
ID 0b05:1779 ASUSTek Computer, Inc.
```which is exactly the one shown in the list of supported devices on LinuxTV. I have implemented all modifications and corrections to the source files as outlined in the above LinuxTVWiki instructions. I also added the boot option ```
usbhid.quirks=0x0b05:0x1779:0x0004
``` to grub2 in order to overcome the (initial) problem of the tuner being recognised as a HID device. My dmesg output after plugging in the device now shows ```
Jan 27 17:44:50 jens-laptop kernel: [ 1086.358488] usb 2-5: new high speed USB device using ehci_hcd and address 6
Jan 27 17:44:50 jens-laptop kernel: [ 1086.495359] usb 2-5: configuration #1 chosen from 1 choice
```When I try to compile the *af903x* driver using ```
sudo make
``` the response on the screen is ```
make -C /lib/modules/2.6.32-27-generic/build SUBDIRS=/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-27-generic'
  CC [M]  /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.o
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:4,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/userdef.h:11:1: warning: "NULL" redefined
In file included from include/linux/kernel.h:12,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:6,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:1:
include/linux/stddef.h:10:1: warning: this is the location of the previous definition
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:6:1: warning: "IN" redefined
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:4,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/userdef.h:21:1: warning: this is the location of the previous definition
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:7:1: warning: "OUT" redefined
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:4,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/userdef.h:22:1: warning: this is the location of the previous definition
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c: In function ‘af903x_suspend’:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:48: warning: passing argument 2 of ‘DL_CheckTunerInited’ from incompatible pointer type
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:218: note: expected ‘enum Bool *’ but argument is of type ‘bool *’
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:49: warning: passing argument 2 of ‘DL_CheckTunerInited’ from incompatible pointer type
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:218: note: expected ‘enum Bool *’ but argument is of type ‘bool *’
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c: At top level:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/firmware.h:28: warning: ‘Firmware_codes’ defined but not used
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/firmware.h:10388: warning: ‘Firmware_segments’ defined but not used
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/firmware.h:10403: warning: ‘Firmware_new_partitions’ defined but not used
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/firmware.h:10412: warning: ‘Firmware_scriptSets’ defined but not used
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/firmware.h:10417: warning: ‘Firmware_scripts’ defined but not used
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:38: warning: ‘af903x_suspend’ defined but not used
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-core.c:61: warning: ‘af903x_resume’ defined but not used
  CC [M]  /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.o
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:4,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/userdef.h:11:1: warning: "NULL" redefined
In file included from include/linux/kernel.h:12,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:6,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:1:
include/linux/stddef.h:10:1: warning: this is the location of the previous definition
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:6:1: warning: "IN" redefined
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:4,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/userdef.h:21:1: warning: this is the location of the previous definition
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:7:1: warning: "OUT" redefined
In file included from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/type.h:4,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/demodulator.h:5,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x.h:17,
                 from /home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:1:
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/userdef.h:22:1: warning: this is the location of the previous definition
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:157: error: field name not in record or union initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:157: error: (near initialization for ‘af903x_properties[0].devices’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:157: warning: missing braces around initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:157: warning: (near initialization for ‘af903x_properties[0].devices[2]’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:157: warning: initialization makes pointer from integer without a cast
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:158: error: field name not in record or union initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:158: error: (near initialization for ‘af903x_properties[0].devices’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:159: warning: braces around scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:159: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: braces around scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: initialization from incompatible pointer type
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:160: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:161: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:162: warning: braces around scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:162: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:162: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:162: warning: (near initialization for ‘af903x_properties[0].devices[3].name’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:164: warning: initialization from incompatible pointer type
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:165: warning: braces around scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:165: warning: (near initialization for ‘af903x_properties[0].devices[3].cold_ids[1]’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:165: warning: excess elements in scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:165: warning: (near initialization for ‘af903x_properties[0].devices[3].cold_ids[1]’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:166: warning: braces around scalar initializer
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:166: warning: (near initialization for ‘af903x_properties[0].devices[3].cold_ids[2]’)
/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.c:171: error: expected ‘}’ before ‘;’ token
make[2]: *** [/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC/af903x-devices.o] Error 1
make[1]: *** [_module_/home/jens/Desktop/Linux_PC_AF9035_Afatech_2008.12.17/Linux-32bit_AF9035_20081217/AF903x_SRC] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic'
make: *** [default] Error 2
```My knowledge is limited and I have no idea why I am getting all these warnings and finally the error message.

I hope some of the pros here can help me with this situation? What can I do next?

Also, is there a way to tell when (or if at all) driver support for this device will be implemented in the Linux kernel?

---

### Post by snej on 2011-01-28
Sorry for the lengthy post above... I could have spared you this if I had found the syntax error I created earlier when adding to the C-struct in the file *af903x-devices.c* as per the instructions (I missed to place a curly bracket '}' where it belonged).

The compilation of the driver seems to work now (even though I am still getting a lot of warnings during the make stage but no error in the end, I have no idea if the warnings are crucial).

But the DVB stick still is not working. After loading the new module with ```
sudo modprobe dvb_af903x
``` my dmesg output now shows 
```
[ 1018.604153] usb 2-5: new high speed USB device using ehci_hcd and address 6
[ 1018.743383] usb 2-5: configuration #1 chosen from 1 choice
[ 1018.743916]         DRIVER_RELEASE_VERSION : v2.0-1
[ 1018.743920]         FW_RELEASE_VERSION     : v8_8_52_0
[ 1018.743924]         API_RELEASE_VERSION    : 200.20081203.0
[ 1018.746743] [Device_init] Error 1
[ 1018.746754] dvb_usb_af903x: probe of 2-5:1.0 failed with error 9
```Can anybody help me out here? What is the reason for the driver to fail now?

Any help is highly appreciated.

---

### Post by snej on 2011-02-05
Hello again,

I believe that I achieved something (better than nothing :)) by following the instructions on **[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)** to install the latest v4l drivers.

In addition I also installed the package **linux-firmware-nonfree**, just in case it is needed.

But the DVB stick still does not work. After a reboot and plugging in the USB stick my dmesg output is now ```
[18055.897860] usb 1-6: new high speed USB device using ehci_hcd and address 2
[18056.035813] usb 1-6: configuration #1 chosen from 1 choice
[18056.161569] dvb_af903x: disagrees about version of symbol dvb_usb_device_init
[18056.161575] dvb_af903x: Unknown symbol dvb_usb_device_init
```This is again not very clear to me. What do the messages in the two last lines mean? And is the device recognised correctly as DVB-T tuner (because what is said in the first line)? What does ehci-hcd mean in this context?

Please, can somebody help me here?[URL="http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers"]
[/URL]

---

### Post by blutter on 2011-03-03
> **snej said:**
> 
```
[18055.897860] usb 1-6: new high speed USB device using ehci_hcd and address 2
[18056.035813] usb 1-6: configuration #1 chosen from 1 choice
[18056.161569] dvb_af903x: disagrees about version of symbol dvb_usb_device_init
[18056.161575] dvb_af903x: Unknown symbol dvb_usb_device_init
```[URL="http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers"]
[/URL]

The code in the link that you provided appears to support kernels up to 2.6.29 but I assume that you are trying to get it to work with a newer one.

Have you tried replacing the kernel headers in the ite-install/installer/AF903x_SRC/v4l subdirectory with the headers that match your kernel?


BTW, I'm trying to get the same USB stick to work with 2.6.35 without any success.

When I load the module I get the following output:

```

[ 2734.489751] AF903X: af903x_module_init
[ 2734.489775]         DRIVER_RELEASE_VERSION : v9.08.14.1
[ 2734.489778]         FW_RELEASE_VERSION     : v8_8_63_0
[ 2734.489780]         API_RELEASE_VERSION    : 200.20090402.0
[ 2734.693176] dvb_usb_af903x: probe of 1-2:1.0 failed with error -12

```If you uncomment the DEBUG macro in src/af903x.h then the module will print some more information:

```

[ 3773.947385] ===af903x usb device pluged in!! ===
[ 3773.947390] - Enter Device_init Function -
[ 3773.947395]         DRIVER_RELEASE_VERSION : v9.08.14.1
[ 3773.947400]         FW_RELEASE_VERSION     : v8_8_63_0
[ 3773.947406]         API_RELEASE_VERSION    : 200.20090402.0
[ 3773.947412] USB mode= 0x200
[ 3773.947416] - Enter DRV_SetBusTuner Function -
[ 3773.947422] busId = 0x2, tunerId =0xff
[ 3773.949904] - Enter DRV_SetBusTuner Function -
[ 3773.949911] busId = 0x2, tunerId =0xff
[ 3773.950700] - Enter DRV_GetEEPROMConfig Function -
[ 3773.951075] EEPROM_IRMODE = 0x01, 
[ 3773.951080] bIrTblDownload ON
[ 3773.951449] EEPROM_TSMODE = 0x00
[ 3773.951453] TSMode = TS1 mode
[ 3773.951458] - Enter DRV_GetEEPROMConfig2 Function -
[ 3773.951826] EEPROM_TUNERID0  = 0x32
[ 3773.951831] - Enter DRV_SetBusTuner Function -
[ 3773.951837] busId = 0x2, tunerId =0x32
[ 3773.960577] - Enter DRV_TunerWakeup Function -
[ 3773.961318] - Enter DRV_Initialize Function -
[ 3773.962068]  Fw version is the same!
[ 3774.053204]     Device initialize Ok!!
[ 3774.053950]     FwVer OFDM = 0x5420C00, 
[ 3774.054706] FwVer LINK = 0xB160C00
[ 3774.054712] - Enter DRV_IrTblDownload Function -
[ 3774.161431] - Enter DRV_ApCtrl Function -
[ 3774.161442]  ucSlaveDemod = 0, bOn = OFF 
[ 3774.161447] - Enter DRV_TunerPowerCtrl Function -
[ 3774.161452] chip = 0
[ 3774.172459]  Device_init success!! 
[ 3774.172484] dvb_usb_af903x: probe of 1-2:1.1 failed with error -12

```So the function af903x_probe in src/af903x-core.c thinks it has successfully initialized the device but it still returns -ENOMEM (-12) for some reason.

---

### Post by blutter on 2011-03-04
[FONT=Verdana][SIZE=2]Okay, I sorted out m[/SIZE][/FONT][FONT=Verdana][SIZE=2]y problem.

[COLOR=#000000][FONT=Arial]When initializing the device it was calling dvb_usb_device_init which was returning -19 (ENODEV).[/FONT][/COLOR][[COLOR=#000099][FONT=Arial]__[/FONT][/COLOR]]("http://lxr.free-electrons.com/source/drivers/media/dvb/dvb-usb/dvb-usb-init.c#L218")[/SIZE][/FONT][SIZE=2]

It turned out that I hadn't made all the necessary code changes. I hadn't made this change:
[/SIZE][SIZE=2]                .num_device_descs = 2, [/SIZE][SIZE=2]so it wasn't looking up the USB vendor/device ID for the Asus variant.[/SIZE] 
[SIZE=2]
That's all that I had to do. Right now it is scanning for channels using w_scan.[/SIZE] 

[SIZE=2]The driver code is a bit of a dog's breakfast so I wonder if the alternate af903x drivers at [http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick) will be better in the longer term.
[/SIZE]

---

### Post by topnobau on 2011-09-03
how did you uncomment the debug code? I thought i had found it but I still get the same error

[ 4576.009685] dvb_usb_af903x: disagrees about version of symbol dvb_usb_device_init
[ 4576.009706] dvb_usb_af903x: Unknown symbol dvb_usb_device_init
v

i've also tried with the older tar to no avail.

---

### Post by blutter on 2011-09-03
> **topnobau said:**
> how did you uncomment the debug code? I thought i had found it but I still get the same error

There's a DEBUG macro in src/af903x.h that is commented out. I don't have the code in front of me but look for something like:

//#define DEBUG 1

Then uncomment this line to give more diagnostic output.

The source of my problem was that I hadn't made all of the changes in af903x-devices.c

---

