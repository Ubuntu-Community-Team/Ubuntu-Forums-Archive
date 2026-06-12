---
title: "usb modem not connected"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by afss on 2010-03-22
i am trying to connect to internet via wll wireless phone.i was able to connect through xp..i am new to ubuntu and know very less of it.
i think ubuntu dont detect my modem.
this is my lsusb output

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 109b:3197  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0421:002f Nokia Mobile Phones 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

this is my wvdial output

Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check Def Route"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

can any1 tell me what the problem is

---

### Post by mindgap on 2010-03-22
Hi Mate!

Can you link the proper wvdial.conf , I would like to see what is inside the config.

But first times check the following thing:

Did you load the ppp driver? If not: 

sudo /sbin/modprobe ppp_generic

I waiting for your wvdial.conf

---

### Post by pdc on 2010-03-23
hi afss;

you say

> i think ubuntu dont detect my modem.

but in lsusb I note

> Bus 005 Device 002: ID 0421:002f Nokia Mobile Phones 

could this be the

> wireless phone

you wish to connect to the internet with?

some wvdial scripts work with ttyUSB1 or ttyUSB2 and by changing these values, one can look to see what happens

---

### Post by afss on 2010-03-23
thanx for uy reply
output for sudo /sbin/modprobe ppp_generic is
FATAL: Module ppp_generic not found.

output for wvdialconf is
Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
ttyACM0<Info>: Device or resource busy
Modem Port Scan<*1>: ACM0 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

---

