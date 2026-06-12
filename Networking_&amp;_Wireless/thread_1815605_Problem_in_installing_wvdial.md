---
title: "Problem in installing wvdial"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by tusharkoshti on 2011-07-31
Hello guys, 
I m using Ubuntu 11.04. I have USB modem MMX 300C HSIA Rev.A  (BSNL) 
I m getting problem in installing wvdial. I have done following steps : 
1) I have installed following packages in that same order:

libxplc0.3.13
libwvstreams4.4-base
libwvstreams4.4-extras
libuniconf4.4
wvdial_1.60.1+nmu2_i386

2) Then I run wvdial command but getting following o/p 
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

3)  I tried to configure wvdial.conf and run 
     sudo wvdialconf 
 and the o/p is :

[sudo] password for tushar: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8   
Modem Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16  
Modem Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24  
Modem Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

Can anyone help me in this ?

---

### Post by dineshs on 2011-08-03
What do you get for ```
lsusb
cat /etc/wvdial.conf
```please post results.Also see
[http://ubuntuforums.org/showthread.php?t=1365524](http://ubuntuforums.org/showthread.php?t=1365524)

---

