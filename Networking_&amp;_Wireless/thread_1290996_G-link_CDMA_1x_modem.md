---
title: "G-link CDMA 1x modem"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by chitragurung on 2009-10-14
I was using above device to connect internet when I was using windows. In my new Dell Inspiron mini I have Ubuntu. Now I want to use same device to connect internet. I do not know how to install driver and set it up ?

I did several attempts to configure my GLINK USB modem to browse and found following results but still I am being unable to browse the internet.

chitra@chitra:~$ modprobe cdc_acm
chitra@chitra:~$ dmesg | tail
[ 1682.245863] usb 4-2: configuration #1 chosen from 1 choice
[ 1682.436366] usbcore: registered new interface driver usbserial
[ 1682.439336] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1682.445234] usbcore: registered new interface driver usbserial_generic
[ 1682.445297] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 1682.475501] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[ 1682.481382] pl2303 4-2:1.0: pl2303 converter detected
[ 1682.484303] usb 4-2: pl2303 converter now attached to ttyUSB0
[ 1682.486810] usbcore: registered new interface driver pl2303
[ 1682.486829] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
chitra@chitra:~$ modprobe -acm
modprobe: invalid option -- m
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
chitra@chitra:~$ modprobe acm
FATAL: Module acm not found.
chitra@chitra:~$ modprobe cdc-acm
chitra@chitra:~$ cat /proc/modules | grep 'acm'
cdc_acm 18848 0 - Live 0xf8b16000
chitra@chitra:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
chitra@chitra:~$ wvdial
--> Ignoring malformed input line: "**"
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
chitra@chitra:~$ 

chitra@chitra:~$ dmesg | grep tty
[    8.559282] console [tty0] enabled
[   12.594206]   hash matches device ttyt5
[ 1682.484303] usb 4-2: pl2303 converter now attached to ttyUSB0
[ 2083.225993] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 2085.972554] usb 4-2: pl2303 converter now attached to ttyUSB0
chitra@chitra:~$ sudo wvdial
[sudo] password for chitra: 
--> Ignoring malformed input line: "**"
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
chitra@chitra:~$

---

