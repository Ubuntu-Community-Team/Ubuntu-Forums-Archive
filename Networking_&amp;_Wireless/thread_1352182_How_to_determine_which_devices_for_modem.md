---
title: "How to determine which devices for modem?"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by holy_rainman on 2009-12-11
hello all,

i have a problem where i don't know where is my modem located at. when i typed:

sudo wvdial digi

it states that cannot open /dev/ttyUSB0: no such directory.
i opened the /dev/ttyUSB0 directory and there was nothing. no such file.

then i tried the gnome-ppp where it needs to determine the directory for the device. i tried keyed in /dev/ttyUSB0 until ttyUSB3 and still no modem. 

i have used modeswitch to change my modem from 1c92:f000 to 1c9e:9603 and the wvdial was already setup. how to determine which device is my modem located at? Please someone guide me to the ubuntu way....

---

### Post by gordintoronto on 2009-12-11
Use the command lsusb to see what USB devices exist.

---

### Post by holy_rainman on 2009-12-12
thanks gordin for replying..

i have used lsusb and this is the output

Bus 001 Device 002: ID 1c9e:f000

after changed to modeswitch (sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf), it changed like this:

Bus 001 Device 007: ID 1c9e:9603.

therefore i know it is a mobidata 100HU device.

let me rephrase my question.

i dont know which port my modem is located. i have used (wvdialconf '/dev/wvdial.conf') and it states:

Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
Modem Port Scan<*1>: S0   S1   S2   S3  
Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?
Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

i fon't know hot to use setserial as i am new to ubuntu. please guide me gordin if you know how....

---

### Post by gordintoronto on 2009-12-12
You are sure this computer has a modem?  Can you describe it physically?

---

