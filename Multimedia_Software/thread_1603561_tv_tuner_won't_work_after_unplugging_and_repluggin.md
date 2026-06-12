---
title: "tv tuner won't work after unplugging and replugging"
date: 2010-10-22
forum: Multimedia Software
---

### Post by parminides on 2010-10-22
After much effort I got mythtv to work on my HP TouchSmart. Then I decided to install it on my laptop before I forgot all the troubleshooting tricks.

So I unplugged my Hauppauge WinTV-HVR 850 from the TouchSmart and plugged it in the laptop. I was successful getting mythtv running on the laptop so I returned the tv tuner to the TouchSmart.

Much to my dismay, mythtv no longer worked on the TouchSmart. I moved the tuner to the laptop again to see if mythtv worked. It didn't. Apparently, the act of unplugging the tuner and plugging it back in broke something.

For usb hard drives and cameras, an icon appears on the desktop that allows me to right click and choose to safely remove the device. I had no idea that unplugging a usb device without such an icon would cause any problems.

Initially, the problem seemed to be with mythtv as I was able to successfully execute the following commands:

```

scan -x0 /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
mplayer dvb://WTVF-HD

```

Unfortunately, mythtv still didn't work. Maybe I unplugged it and plugged it in once or twice more, I don't remember. I rebooted several times. In the end, the tuner became completely inaccesible. For instance,

```

[~] $ mplayer dvb://WTVF-HD
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://WTVF-HD.
ERROR OPENING FRONTEND DEVICE /dev/dvb/adapter0/frontend0: ERRNO 16
DVB_SET_CHANNEL2, COULDN'T OPEN DEVICES OF CARD: 0, EXIT
ERROR, COULDN'T SET CHANNEL  25: Failed to open dvb://WTVF-HD.

```

and

```

[~] $  scan -x0 /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

```

There's no problem with the tuner in the Windows partition of the same machine.

Following [http://ubuntuforums.org/archive/index.php/t-1233131.html](http://ubuntuforums.org/archive/index.php/t-1233131.html), I generated the following messages for your viewing pleasure:

```

[~] $ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:140c Hewlett-Packard 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1926:0003  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 2040:7240 Hauppauge 
Bus 002 Device 003: ID 04f2:b056 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1934:0602  
Bus 001 Device 004: ID 0424:2507 Standard Microsystems Corp. 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and

```

[~] $ dmesg|grep usb
[    0.376624] usbcore: registered new interface driver usbfs
[    0.376636] usbcore: registered new interface driver hub
[    0.376664] usbcore: registered new device driver usb
[    0.460176] usb usb1: configuration #1 chosen from 1 choice
[    0.490172] usb usb2: configuration #1 chosen from 1 choice
[    0.490564] usb usb3: configuration #1 chosen from 1 choice
[    0.490817] usb usb4: configuration #1 chosen from 1 choice
[    0.491056] usb usb5: configuration #1 chosen from 1 choice
[    0.491308] usb usb6: configuration #1 chosen from 1 choice
[    0.491547] usb usb7: configuration #1 chosen from 1 choice
[    0.900034] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.052414] usb 1-2: configuration #1 chosen from 1 choice
[    1.059436] usbcore: registered new interface driver usb-storage
[    1.059444] usb-storage: device found at 3
[    1.059446] usb-storage: waiting for device to settle before scanning
[    1.170043] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    1.320508] usb 1-4: configuration #1 chosen from 1 choice
[    1.560042] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    1.747813] usb 2-2: configuration #1 chosen from 1 choice
[    1.860038] usb 2-3: new high speed USB device using ehci_hcd and address 4
[    2.032510] usb 2-3: configuration #1 chosen from 1 choice
[    2.390047] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.571702] usb 3-1: configuration #1 chosen from 1 choice
[    2.860037] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.052182] usb 5-1: configuration #1 chosen from 1 choice
[    3.067943] usbcore: registered new interface driver hiddev
[    3.072150] input: NextWindow Touchscreen as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input3
[    3.072325] input: NextWindow Touchscreen as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input4
[    3.072423] generic-usb 0003:1926:0003.0001: input,hidraw0: USB HID v1.00 Keyboard [NextWindow Touchscreen] on usb-0000:00:1d.0-1/input0
[    3.075160] generic-usb 0003:1926:0003.0002: hiddev96,hidraw1: USB HID v1.00 Device [NextWindow Touchscreen] on usb-0000:00:1d.0-1/input1
[    3.084115] input: NextWindow Touchscreen as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.2/input/input5
[    3.084284] input: NextWindow Touchscreen as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.2/input/input6
[    3.084390] generic-usb 0003:1926:0003.0003: input,hiddev97,hidraw2: USB HID v1.00 Mouse [NextWindow Touchscreen] on usb-0000:00:1d.0-1/input2
[    3.084419] usbcore: registered new interface driver usbhid
[    3.084422] usbhid: v2.6:USB HID core driver
[    3.340057] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    3.522381] usb 6-2: configuration #1 chosen from 1 choice
[    3.537485] input: HP HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input7
[    3.537574] generic-usb 0003:03F0:140C.0004: input,hidraw3: USB HID v1.11 Keyboard [HP HP Wireless Keyboard Kit] on usb-0000:00:1d.1-2/input0
[    3.574672] input: HP HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input8
[    3.574790] generic-usb 0003:03F0:140C.0005: input,hiddev98,hidraw4: USB HID v1.11 Mouse [HP HP Wireless Keyboard Kit] on usb-0000:00:1d.1-2/input1
[    3.650138] usb 1-4.3: new full speed USB device using ehci_hcd and address 5
[    3.762027] usb 1-4.3: configuration #1 chosen from 1 choice
[    6.052705] usb-storage: device scan complete
[   17.218700] usbcore: registered new interface driver btusb
[   17.272294] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   17.272297] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   17.280462] input: CNF7042 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input9
[   17.280570] usbcore: registered new interface driver uvcvideo
[   17.358743] usb 1-4.3: reset full speed USB device using ehci_hcd and address 5
[   17.481756] lirc_mceusb[5]: FINTEK eHome Infrared Transceiver on usb1:5
[   17.481978] usbcore: registered new interface driver lirc_mceusb
[   17.995126] usbcore: registered new interface driver au0828
[   18.135077] usbcore: registered new interface driver snd-usb-audio
[   22.356731] usb 2-3: firmware: requesting dvb-fe-xc5000-1.6.114.fw

```

After unplugging and plugging it back in, those messages disappeared completely!

```

[~] $ dmesg|grep usb
[~] $ lsusb

```

The second command is especially bizarre. The prompt doesn't return, not even with a ctrl-c and a ctrl-z. In other words, the lsusb command hangs the terminal!

Please help. I am extremely frustrated to get mythtv working and then break the whole thing by unplugging the tv tuner.

---

### Post by parminides on 2010-10-22
I was able to fix my problem. The key seemed to be shutting the computer down, unplugging the tuner, rebooting without the tuner, then plugging in the tuner. After all that, it worked!

---

