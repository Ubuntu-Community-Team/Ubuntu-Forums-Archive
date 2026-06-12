---
title: "USB Modem not detecting"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by rk.jha on 2011-01-30
Hi All,

I have a USB modem working in windows. But no luck to connect using Ubuntu 10.04.

I have setup usb-modeswitch and other stuff. The modem is attached to port ttyUSB0. But when i run "sudo wvdialconf" it displays message like this.

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.


Please somebody help, i love ubuntu and i need to setup modem.


Thanks,

Ritesh

---

### Post by P4man on 2011-01-30
Many of those USB modems are called winmodems, and for a reason Im afraid. Perhaps you can give us the exact type of modem ? You may have seen it, but if not, check this:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Frankly though, unless you get lucky with the type of modem,  your best bet would probably be finding a hardware modem (USB one's are really rare, go for a serial port modem assuming your pc still has a serial port).

---

### Post by rk.jha on 2011-01-30
Hi P4man,

Thanks for your reply. I have checked DialupModemHowTo link and visited lots of forum but didn't solve my problem. Finally i have create this thread. here is the output of "lsusb"

rkj@rkj-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 21f5:1000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have also attached scanModem output.

Thanks,
RKJ

---

