---
title: "reliance netconnect zte ac8710"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by ankscorek on 2009-06-12
helo humans i am using amd64 on hp laptop and i have a zte ac 8710 evdo dongle..here r the various things i tried and finally i am stuck up for want of a driver..i guess so..al experts are invited for their opinions..

[B]root@skal-laptop:/# wvdialconf
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

If you still have problems, send mail to <wvdial-list@lists.nit.ca>


root@skal-laptop:/# lsusb
Bus 002 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 19d2:fff6  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@skal-laptop:/# tail -f /var/log/messages
Jun 12 17:56:09 skal-laptop -- MARK --
Jun 12 18:16:09 skal-laptop -- MARK --
Jun 12 18:36:09 skal-laptop -- MARK --
Jun 12 18:36:54 skal-laptop kernel: [14463.333078] usb 3-2: new full speed USB device using ohci_hcd and address 3
Jun 12 18:36:55 skal-laptop kernel: [14463.550241] usb 3-2: configuration #1 chosen from 1 choice
Jun 12 18:36:55 skal-laptop kernel: [14463.560235] usbserial_generic 3-2:1.0: generic converter detected
Jun 12 18:36:55 skal-laptop kernel: [14463.560444] usb 3-2: generic converter now attached to ttyUSB0
Jun 12 18:36:55 skal-laptop kernel: [14463.663215] Initializing USB Mass Storage driver...
Jun 12 18:36:55 skal-laptop kernel: [14463.663405] usbcore: registered new interface driver usb-storage
Jun 12 18:36:55 skal-laptop kernel: [14463.663413] USB Mass Storage support registered.

root@skal-laptop:/# usb_modeswitch -v 0x19d2 -p 0xfff6 -V 0x19d2 -P 0xfff1 -M 5553424312345678c00000008000069f030000000000000000000000000000

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 003 on bus 003 ...
No MessageEndpoint given. Trying to autodetect ...
 OK, using endpoint 0x0a
Looking for active driver ...
 OK, driver found ("usbserial_generic")
 OK, driver "usbserial_generic" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x0a ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye
[/B]

as one can see product id=fff6 and target id =fff1

please i think i am only in need of a driver

any help is appreciable

i did a usb snoop for this device from a windows box..in other words a different machine..as i am only using  a linux box..so will the message captured from there do something here?

[COLOR="Red"]MessageContent="55 53 42 43 d0 88 36 84 00 08 00 00 80 00 0a 28 00 00 00 00 48 00 00 04 00 00 00 00 00 00 00
"[/COLOR]

---

### Post by ankscorek on 2009-06-13
for the benefit of people who could not pull it out here is a solution i worked out for ubuntu jaunty

[B][COLOR="Orange"]i added the target vendor and product id to my menu.1st file

then used this command

/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch_zte_mf627.conf

that was it was up and working..

to be noted the command is to be issued as soon as u plug in the modem ..u might have to issue this command two to three times or more ..wvdialconf will detect ur modem at 9600bps[/COLOR][/B]

i know this is a crude method but with jaunty buliding in usbserial module i had no choice left and hence had to go this way
the method i wrote on top had given no success by anyone..

any better solutions are invited please

---

### Post by musical-poet on 2009-09-12
> **ankscorek said:**
> helo humans i am using amd64 on hp laptop and i have a zte ac 8710 evdo dongle..here r the various things i tried and finally i am stuck up for want of a driver..i guess so..al experts are invited for their opinions..

[B]root@skal-laptop:/# wvdialconf
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

If you still have problems, send mail to <wvdial-list@lists.nit.ca>


root@skal-laptop:/# lsusb
Bus 002 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 19d2:fff6  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@skal-laptop:/# tail -f /var/log/messages
Jun 12 17:56:09 skal-laptop -- MARK --
Jun 12 18:16:09 skal-laptop -- MARK --
Jun 12 18:36:09 skal-laptop -- MARK --
Jun 12 18:36:54 skal-laptop kernel: [14463.333078] usb 3-2: new full speed USB device using ohci_hcd and address 3
Jun 12 18:36:55 skal-laptop kernel: [14463.550241] usb 3-2: configuration #1 chosen from 1 choice
Jun 12 18:36:55 skal-laptop kernel: [14463.560235] usbserial_generic 3-2:1.0: generic converter detected
Jun 12 18:36:55 skal-laptop kernel: [14463.560444] usb 3-2: generic converter now attached to ttyUSB0
Jun 12 18:36:55 skal-laptop kernel: [14463.663215] Initializing USB Mass Storage driver...
Jun 12 18:36:55 skal-laptop kernel: [14463.663405] usbcore: registered new interface driver usb-storage
Jun 12 18:36:55 skal-laptop kernel: [14463.663413] USB Mass Storage support registered.

root@skal-laptop:/# usb_modeswitch -v 0x19d2 -p 0xfff6 -V 0x19d2 -P 0xfff1 -M 5553424312345678c00000008000069f030000000000000000000000000000

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 003 on bus 003 ...
No MessageEndpoint given. Trying to autodetect ...
 OK, using endpoint 0x0a
Looking for active driver ...
 OK, driver found ("usbserial_generic")
 OK, driver "usbserial_generic" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x0a ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye
[/B]

as one can see product id=fff6 and target id =fff1

please i think i am only in need of a driver

any help is appreciable

i did a usb snoop for this device from a windows box..in other words a different machine..as i am only using  a linux box..so will the message captured from there do something here?

[COLOR=Red]MessageContent="55 53 42 43 d0 88 36 84 00 08 00 00 80 00 0a 28 00 00 00 00 48 00 00 04 00 00 00 00 00 00 00
"[/COLOR]


Hello ankscorek,

I am facing exactly the same issue u have described here! I though have a different modem ZTE AC2726. Please tell me what u did to solve this problem. 

My modem is also not getting detected. Please help me...

Thanks
Bhaskar

---

