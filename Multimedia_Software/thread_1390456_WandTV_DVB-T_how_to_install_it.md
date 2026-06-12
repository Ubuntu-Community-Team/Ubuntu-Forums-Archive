---
title: "WandTV DVB-T how to install it?"
date: 2010-01-25
forum: Multimedia Software
---

### Post by iosifidis on 2010-01-25
I just bought from E-bay a USB card for digital tv. I didn't searched much since it was very cheap and I plan to give it to my brother (he used windows). I tried to test it with Linux. When I plug it, **lsusb** gives:

```
Bus 001 Device 009: ID 15a4:1001 
```

I checked the cd-rom they sent me and I saw there's a directory linux with the driver (sh file) and directions to install:

> 5.  Package Installation for Linux

    a. Install driver with source code

        Alternatively, you may compile and install the driver source code manually,
        1) Copy the driver folder to your desk.

        2) In the folder 'v9.08.14.1', type the following command to  install af903x DVB-T driver dvb-usb-af903x.ko.
            # sh ITE-Linux-AF903x-v9.08.14.1.sh
            # 1

        3) Plug in the device and check the message to make sure the driver is work normally.
            # cat /var/log/messages
            log messages:
            dvb-usb: found a 'ITEtech USB2.0 DVB-T Recevier' in warm state.
            dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
            dvb-usb: ITEtech USB2.0 DVB-T Recevier successfully initialized and connected.

            #lsmod|more
            Module info:

            Module                  Size  Used by
            dvb_af903x             -----  0 
            dvb_usb                -----  1 dvb_af903x
            dvb_core               -----  1 dvb_usb
            dvb_pll                -----  1 dvb_usb


So here we are. Let's try. 

The installation command gives:

```
ITE-Linux-AF903x-v9.08.14.1.sh: 21: [[: not found
ITE-Linux-AF903x-v9.08.14.1.sh: 30: [[: not found
ITE-Linux-AF903x-v9.08.14.1.sh: 38: [[: not found
1. Install ITEtech AF9035 Driver
2. Remove  ITEtech AF9035 Driver
Please Input Your Choise:
1
Please wait a minute
cp: &#945;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#949;&#954;&#964;&#941;&#955;&#949;&#963;&#951; &#964;&#951;&#962; stat &#963;&#964;&#959; &#945;&#961;&#967;&#949;&#943;&#959; «api/.*.o.cmd»: No such file or directory
make -C /lib/modules/2.6.31-18-generic/build SUBDIRS=/tmp/ite-install/installer/AF903x_SRC modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-18-generic'
  CC [M]  /tmp/ite-install/installer/AF903x_SRC/af903x-core.o
In file included from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/af903x.h:15:21: error: dvb-usb.h: No such file or directory
In file included from /tmp/ite-install/installer/AF903x_SRC/type.h:4,
                 from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/userdef.h:11:1: warning: "NULL" redefined
In file included from include/linux/kernel.h:12,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:6,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
include/linux/stddef.h:10:1: warning: this is the location of the previous definition
In file included from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/type.h:6:1: warning: "IN" redefined
In file included from /tmp/ite-install/installer/AF903x_SRC/type.h:4,
                 from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/userdef.h:21:1: warning: this is the location of the previous definition
In file included from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/type.h:7:1: warning: "OUT" redefined
In file included from /tmp/ite-install/installer/AF903x_SRC/type.h:4,
                 from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/userdef.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/af903x.h:201: error: array type has incomplete element type
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:5: warning: data definition has no type or storage class
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:5: warning: type defaults to ‘int’ in declaration of ‘DVB_DEFINE_MOD_OPT_ADAPTER_NR’
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:5: warning: parameter names (without types) in function declaration
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: In function ‘af903x_probe’:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: implicit declaration of function ‘dvb_usb_device_init’
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: ‘adapter_nr’ undeclared (first use in this function)
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: (Each undeclared identifier is reported only once
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: for each function it appears in.)
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: In function ‘af903x_suspend’:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:51: warning: passing argument 2 of ‘DL_CheckTunerInited’ from incompatible pointer type
/tmp/ite-install/installer/AF903x_SRC/af903x.h:218: note: expected ‘enum Bool *’ but argument is of type ‘bool *’
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:52: warning: passing argument 2 of ‘DL_CheckTunerInited’ from incompatible pointer type
/tmp/ite-install/installer/AF903x_SRC/af903x.h:218: note: expected ‘enum Bool *’ but argument is of type ‘bool *’
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: At top level:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:94: error: ‘dvb_usb_device_exit’ undeclared here (not in a function)
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: In function ‘af903x_module_init’:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:104: error: implicit declaration of function ‘info’
make[2]: *** [/tmp/ite-install/installer/AF903x_SRC/af903x-core.o] Error 1
make[1]: *** [_module_/tmp/ite-install/installer/AF903x_SRC] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-18-generic'
make: *** [default] Error 2
make error

```

Then the command **cat /var/log/messages** gives:

```
Jan 25 09:45:02 diamond rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="921" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 25 10:14:36 diamond pulseaudio[2998]: ratelimit.c: 8 events suppressed
Jan 25 12:05:16 diamond kernel: [ 8922.160066] usb 1-5: new high speed USB device using ehci_hcd and address 9
Jan 25 12:05:16 diamond kernel: [ 8922.320097] usb 1-5: configuration #1 chosen from 1 choice
Jan 25 12:05:16 diamond kernel: [ 8922.336277] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.1/input/input6
Jan 25 12:05:16 diamond kernel: [ 8922.336438] generic-usb 0003:15A4:1001.0003: input,hidraw2: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:03.3-5/input1
Jan 25 12:05:42 diamond kernel: [ 8947.462699] usb 1-5: USB disconnect, address 9
Jan 25 12:06:03 diamond kernel: [ 8968.781008] usb 1-5: new high speed USB device using ehci_hcd and address 10
Jan 25 12:06:03 diamond kernel: [ 8968.922673] usb 1-5: configuration #1 chosen from 1 choice
Jan 25 12:06:03 diamond kernel: [ 8968.928136] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.1/input/input7
Jan 25 12:06:03 diamond kernel: [ 8968.928295] generic-usb 0003:15A4:1001.0004: input,hidraw2: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:03.3-5/input1
Jan 25 12:12:38 diamond sudo: pam_sm_authenticate: Called
Jan 25 12:12:38 diamond sudo: pam_sm_authenticate: username = [iosifidis]
Jan 25 12:19:55 diamond kernel: [ 9800.741886] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.741895] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.741904] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.741908] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.741924] __ratelimit: 3 callbacks suppressed
Jan 25 12:19:55 diamond kernel: [ 9800.748820] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.748828] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.748837] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.748840] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.753905] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.753912] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.753920] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.753923] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.759571] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.759579] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.759588] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.759591] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.765860] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.765868] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.765876] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.765879] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.771757] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.771766] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.771776] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.771779] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.776948] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.776956] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.776965] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.776968] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.992499] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.992510] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.992519] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.992523] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:55 diamond kernel: [ 9800.997638] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 12:19:55 diamond kernel: [ 9800.997647] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 12:19:55 diamond kernel: [ 9800.997657] Info fld=0x3f1c, ILI
Jan 25 12:19:55 diamond kernel: [ 9800.997660] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jan 25 12:19:56 diamond kernel: [ 9801.625593] UDF-fs: No VRS found
Jan 25 12:19:56 diamond kernel: [ 9801.625600] UDF-fs: No partition found (1)
Jan 25 12:21:26 diamond kernel: [ 9892.252613] usb 1-5: USB disconnect, address 10
Jan 25 12:23:25 diamond kernel: [10010.928029] usb 1-5: new high speed USB device using ehci_hcd and address 11
Jan 25 12:23:25 diamond kernel: [10011.066629] usb 1-5: configuration #1 chosen from 1 choice
Jan 25 12:23:25 diamond kernel: [10011.070901] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.1/input/input8
Jan 25 12:23:25 diamond kernel: [10011.071029] generic-usb 0003:15A4:1001.0005: input,hidraw2: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:03.3-5/input1

```

By the way, dmesg gives:

```
[18809.780034] usb 1-5: new high speed USB device using ehci_hcd and address 9
[18809.918585] usb 1-5: configuration #1 chosen from 1 choice
[18809.922882] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.1/input/input6
[18809.923010] generic-usb 0003:15A4:1001.0003: input,hidraw2: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:03.3-5/input1
```

Then I searched the net. I found a guy saying:

```
sudo apt-get install dvbscan
sudo apt-get install w-scan
```

then search with Kaffeine and found channels.

Mine failed (since there wasn't installation)

I didn't search much. But I found couple of sources:

[http://ubuntuforums.org/showthread.php?t=1364396](http://ubuntuforums.org/showthread.php?t=1364396)
[http://forum.sabayon.org/viewtopic.php?f=59&t=19383](http://forum.sabayon.org/viewtopic.php?f=59&t=19383)

NOTE: I'm not familiar with scripts etc. I need help how to do them. I have installed ubuntu 9.10

Thanks for your help.

---

### Post by Nightgoblin on 2010-01-26
Hi I'm running Debian Lenny with kernel 2.6.30 from backports and I have almost identical problem. In my case the product is labeled "ezcap USB 2.0 DVB-T Stick". Here's the output from running installer.sh:

```
1. Install ITEtech AF9035 Driver
2. Remove  ITEtech AF9035 Driver
Please Input Your Choise:
1
Please wait a minute
cp: cannot stat `api/.*.o.cmd': No such file or directory
make -C /lib/modules/2.6.30-bpo.2-686/build SUBDIRS=/home/nightgoblin/v9.08.14.1/AF903x_SRC modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-bpo.2-686'
  CC [M]  /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.o
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:15:21: error: dvb-usb.h: No such file or directory
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/type.h:4,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/demodulator.h:5,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:17,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/userdef.h:11:1: warning: "NULL" redefined
In file included from /usr/src/linux-headers-2.6.30-bpo.2-common/include/linux/kernel.h:12,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:6,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/usr/src/linux-headers-2.6.30-bpo.2-common/include/linux/stddef.h:10:1: warning: this is the location of the previous definition
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/demodulator.h:5,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:17,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/type.h:6:1: warning: "IN" redefined
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/type.h:4,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/demodulator.h:5,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:17,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/userdef.h:21:1: warning: this is the location of the previous definition
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/demodulator.h:5,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:17,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/type.h:7:1: warning: "OUT" redefined
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/type.h:4,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/demodulator.h:5,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:17,
                 from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/userdef.h:22:1: warning: this is the location of the previous definition
In file included from /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:1:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x.h:201: error: array type has incomplete element type
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:5: warning: data definition has no type or storage class
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:5: warning: type defaults to ‘int’ in declaration of ‘DVB_DEFINE_MOD_OPT_ADAPTER_NR’
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:5: warning: parameter names (without types) in function declaration
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c: In function ‘af903x_probe’:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:34: error: implicit declaration of function ‘dvb_usb_device_init’
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:34: error: ‘adapter_nr’ undeclared (first use in this function)
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:34: error: (Each undeclared identifier is reported only once
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:34: error: for each function it appears in.)
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c: In function ‘af903x_suspend’:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:51: warning: passing argument 2 of ‘DL_CheckTunerInited’ from incompatible pointer type
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:52: warning: passing argument 2 of ‘DL_CheckTunerInited’ from incompatible pointer type
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c: At top level:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:94: error: ‘dvb_usb_device_exit’ undeclared here (not in a function)
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c: In function ‘af903x_module_init’:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:104: error: implicit declaration of function ‘info’
make[4]: *** [/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.o] Error 1
make[3]: *** [_module_/home/nightgoblin/v9.08.14.1/AF903x_SRC] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-bpo.2-686'
make: *** [default] Error 2
make error
```

Did you make any progress on resolving this? Thanks.

---

### Post by iosifidis on 2010-01-26
I posted to local Ubuntu forum. A guy checked the chip and asked directly the company. The company replied that it plays with older kernel. 

Didn't have time to search it more. I take exams at the uni this period.

---

### Post by staticx1 on 2010-05-11
any progress on this one?

---

### Post by iosifidis on 2010-05-11
Actually no. I found out that I have the new chip and it's not supported.

---

### Post by amoyse on 2010-06-26
try this [http://southern-fish.blogspot.com/2010/05/installing-af9035-dvb-t-usb-tuner-on.html]("http://southern-fish.blogspot.com/2010/05/installing-af9035-dvb-t-usb-tuner-on.html")

---

### Post by riktek on 2010-10-07
> **iosifidis said:**
> Actually no. I found out that I have the new chip and it's not supported.
bought wandtv stick, after hours searching found ITE drivers, does work although wont show up with modprobe, installed drivers and installed METV from repo and away it went. achieved this on EEEPC 701 ubuntu 9.04,has ITE9135 chip IT9135 BDA device file is it913x.linux.PC.dvb-tv9.12.18.1.zip will try to find where I got it from online,have to search history of visited threads. file at depositfiles.com/en/files/6h8rk5c63. lots of luck to you

---

### Post by kuro_man on 2010-11-27
> /home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:51: warning: passing argument 2 of &#8216;DL_CheckTunerInited&#8217; from incompatible pointer type
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:52: warning: passing argument 2 of &#8216;DL_CheckTunerInited&#8217; from incompatible pointer type
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c: At top level:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:94: error: &#8216;dvb_usb_device_exit&#8217; undeclared here (not in a function)
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c: In function &#8216;af903x_module_init&#8217;:
/home/nightgoblin/v9.08.14.1/AF903x_SRC/af903x-core.c:104: error: implicit declaration
 
edit AF903x_SRC/*.c files, change all references of "Bool" to "bool" for function DL_CheckTunerInited - this compile it for me although I never got it to load

---

### Post by publicidadno on 2011-05-14
This is for AF9015:

[http://ubuntuforums.org/showpost.php?p=10816855&postcount=6](http://ubuntuforums.org/showpost.php?p=10816855&postcount=6)

Hugo

---

### Post by TopEnder on 2011-05-16
Scott, I would not proceed any further trying to install the DVB USB Stick using the above posts for (AF9015 etc) because from your previous posts your USB stick has the following chipset:
ID 18b4:1001 e3C Technologies DUTV007, and so far there does not seem to be any drivers that will work with Ubuntu (Linux), I'vd tried a few recommendations but so far no luck.  I'll Private Message you in a day or two with a possible solution.  TopEnder

---

### Post by dmrkonjic on 2011-08-14
It WORKS NOW for me...  Ez Cap DVB-T USB in Ubuntu 10.04 on kernel 

following the procedure on  [http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)

I made several mistakes in first attempts:

- didn't change kernel in commands :
ln -s /usr/src/linux-source-2.6.35/drivers/media/dvb/frontends/*.h .
ln -s /usr/src/linux-source-2.6.35/drivers/media/dvb/dvb-core/*.h .
ln -s /usr/src/linux-source-2.6.35/drivers/media/dvb/dvb-usb/*.h .

also it is necesary to repeat every ln -s... tvice (with arrow up)
(I do not know why - but gives different feedback)

- DVB-T USB have to be out (i think) during instalation
now, on dmesg it is giving me
 
[   34.669357] dvb-usb: found a 'ITEtech USB2.0 DVB-T Recevier' in warm state.
[   34.757364] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   34.757731] DVB: registering new adapter (ITEtech USB2.0 DVB-T Recevier)
[   34.758020] DVB: registering adapter 0 frontend 0 (AF903X USB DVB-T)...
[   34.772614] dvb-usb: ITEtech USB2.0 DVB-T Recevier successfully initialized and connected.

After reboot Kaffeine is scanning  programs...

---

### Post by dmrkonjic on 2011-08-14
And...  I added lines 
options usbhid quirks=0x15a4:0x1001:0x0004
usbhid.quirks=0x15a4:0x1001:0x0004

and rebooted before last (successful) attempt of instalation

---

### Post by budhus on 2012-04-09
I am a newbie to linux and using Ubuntu 11.10. Initially I couldn't find a solution as many of the steps are different in 11.10. After many days of search I found this page which helped me a lot. Hopefully, this will help others as well.

**[http://askubuntu.com/questions/70382/installing-dvb-t-afatech-af9035]("http://askubuntu.com/questions/70382/installing-dvb-t-afatech-af9035")**

By the way I am using 9035 driver for WandTV which also shows as Afatech.


**Suggestion:** Forum members who have requisite coding skills should try and write/update codes for this brand of TV tuners so that other newbies don't face such problems when trying out Linux for the first time.

Thanks

---

### Post by Amraks on 2012-05-14
are you having the same trouble I am having?

```

[   24.360480] dvb_usb_af903x: 
probe of 1-4:1.0 failed with error -12
[   24.584372] dvb_usb_af903x: 
probe of 1-4:1.1 failed with error -12

```
had this working perfect until I updated from 3.0.0 to kernel 3.2.0

---

### Post by budhus on 2012-10-30
Hello Amraks!

My appologies for writing this reply so late! I upgraded to Ubuntu 12.04 from 11.10 and I faced the same problem. Now I have installed Linux Mint 13 and the problem still persist. Hope some kind soul out there can help us!


Anybody....

---

