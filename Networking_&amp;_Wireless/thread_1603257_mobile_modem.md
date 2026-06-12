---
title: "mobile modem"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by saman6015 on 2010-10-22
Hello every one i am posting this as fifth time 

[SIZE=3]i don't know how to connect Internet using samsung mobile S3310 i connected with nokia it's worked,but in samsung mobile it is not connecting [/SIZE].

i searched full of this Ubuntu forum related to this problem, i got some of threats in that too there is no solution 

main thing is device is identified by USB but not by network manager.

i did 

administrator@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
administrator@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
administrator@ubuntu:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   ACM1 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

administrator@ubuntu:~$ sudo apt-get install usb-modeswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
usb-modeswitch is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


i dont know ,what i have do ,
last few days i was tried i didn't get the solution,i got so much disappointment if i get simple idea related to this problem i will be very happy

please,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

thanks in advance

---

### Post by Megaptera on 2010-10-22
This thread is marked as "Solved" - is it or do you still need help? If the latter you need to mark it "Unsolved"

---

