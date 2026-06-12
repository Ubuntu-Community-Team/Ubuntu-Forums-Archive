---
title: "connect internet Mobidata MBD-100EU"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by tedora on 2009-11-22
i wish to completely migrate from Windows to Ubuntu.but now this obstacle is hampering me from enjoying Ubuntu.

my Ubuntu is brand new Ubuntu9.10 i.e. Karmic Koala.
i installed it from a live CD.

reyas19@ubuntu:~$[SIZE=3]** [SIZE=2]uname -a[/SIZE]**[/SIZE]
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

my modem is Mobidata.it detects as below,

reyas19@ubuntu:~$**[SIZE=2] lsusb [/SIZE]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 10ce:ea6a Silicon Labs MobiData EDGE USB Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

reyas19@ubuntu:~$ **[SIZE=2]dmesg | grep usb[/SIZE]**
[    0.246202] usbcore: registered new interface driver usbfs
[    0.246248] usbcore: registered new interface driver hub
[    0.246318] usbcore: registered new device driver usb
[    1.176232] usb usb1: configuration #1 chosen from 1 choice
[    1.177013] usb usb2: configuration #1 chosen from 1 choice
[    1.177599] usb usb3: configuration #1 chosen from 1 choice
[    1.178165] usb usb4: configuration #1 chosen from 1 choice
[    1.178708] usb usb5: configuration #1 chosen from 1 choice
[    1.888098] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.079349] usb 3-2: configuration #1 chosen from 1 choice
[    9.994153] usbcore: registered new interface driver usbserial
[    9.994250] usbcore: registered new interface driver usbserial_generic
[    9.994256] usbserial: USB Serial Driver core
[   10.113781] usb 3-2: reset full speed USB device using uhci_hcd and address 2
[   10.274233] usb 3-2: cp210x converter now attached to ttyUSB0
[   10.274278] usbcore: registered new interface driver cp210x


neither wvdial works for it. i've use internet via this modem in this Ubuntu for 3 days.
now it shows this messages below.....

reyas19@ubuntu:~$ **[SIZE=2]gnome-ppp [/SIZE]**
WVCONF: /home/reyas19/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM0L0DT*99***1#
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM0L0DT*99***1#
GNOME PPP: STDERR: CONNECT
GNOME PPP: STDERR: ~[7f]}#@!}!(} }<}!}$}&@}#}$@#}%}&_8^G}"}&} } } } }'}"}(}"ep~
~[7f]}#@!}%}.} }=Normal Termination by NCPQ ~~[7f]}#@!}%}/} }5
Timeout: Retrying[07]%~~[7f]}#@!}!)} }<}!}$}&@}#}$@#}%}&_8^G}"}&} } } } }'}"}(}"-"~~~
GNOME PPP: STDERR: --> Carrier detected.  Starting PPP immediately.
GNOME PPP: STDERR: --> Starting pppd at Mon Nov 23 01:41:26 2009
GNOME PPP: STDERR: --> Pid of pppd: 2852
GNOME PPP: STDERR: --> Disconnecting at Mon Nov 23 01:41:27 2009
GNOME PPP: STDERR: --> The PPP daemon has died: pppd options error (exit code = 2)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> I guess that's it for now, exiting
GNOME PPP: STDERR: --> The PPP daemon has died. (exit code = 2)

i've also tryed with sudo.but result is same. 
some time give a message with "(exit code = 16)"

i also need the file permission for /etc/ppp/

---

### Post by tedora on 2009-12-09
i just create a new user and browsing the net with gnome-ppp

---

