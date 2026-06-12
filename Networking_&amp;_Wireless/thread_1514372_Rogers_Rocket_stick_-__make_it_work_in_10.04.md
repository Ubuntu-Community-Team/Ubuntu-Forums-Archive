---
title: "Rogers Rocket stick -  make it work in 10.04 ?"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by mrpenguin on 2010-06-20
I have searched everywhere and find it hard to believe that I am the only Rogers Rocket stick user that is using Ubuntu in this world.

My Rogers Rocket stick was able to connect and work perfectly with 9.10 but since the 10.04 update I am not able to keep it connected for longer than a few minutes.

I have done everything ... did a complete fresh install of 10.04
I do not have any weird software on my computer and i dont know enough about linux to have been able to make weird adjustments to it that I should not have done.
I am completely updated with all updates

Its a fresh install ... pop in the Sony Ericsson Rogers Rocker stick and then do the following :

> sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1

sudo gedit /etc/wvdial.conf


[Dialer rogers-nopin]

Phone = *99#

Username = wapuser1

Password = wap

Modem = /dev/ttyACM0

Baud = 460800

Init1 = AT+CPIN?

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = ATX3

Init4 = AT+CFUN=6

ISDN = 0

Modem Type = USB Modem

Init5 =AT +CGDCONT=1,"IP","internet.com","",0,0;

Auto DNS

Check DNS

sudo usb_modeswitch -v 0fce -p d103 -O

sudo wvdial rogers-nopin


This is all I used to have to do with 9.10 to get connected and stay on the internet for hours.
Doing this now after the new update gets me connected after about the 2nd to 5th try and once connected I only stay on for between a minute to 5 minutes before I am disconnected.

There must be somebody that is not having the same problems as me ??

Please help !!!

---

### Post by mrpenguin on 2010-06-21
bump

---

### Post by alexfish on 2010-06-22
hi

Need to clarify :at the foot of the page you are doing a modeswitch "sudo usb_modeswitch -v 0fce -p d103 -O"

before doing the mode switch can you post the results of these commands from the terminal

Code:

ls -al /dev/serial/by-id/usb*


Code:

ls -al /dev/disk/by-id/usb*Mass_Storage*

Code:

lsusb

then use the usb_modeswitch , repeat the above and post any changes between the listings

regards

alexfish

---

### Post by mrpenguin on 2010-06-22
I will post the results as soon as I can stay on the Internet for long enough without getting disconnected.

---

### Post by mrpenguin on 2010-06-22
The one thing I don't understand is that it seems everybody is blaming modeswitch for the problem, if it was modeswitch then it should not switch my rocket stick to act as a modem ! but it does.... The problem is connecting to the Internet and then when it does connect to actually stay connected and not getting kicked off 5 min later 

I don't get that ??

---

### Post by mrpenguin on 2010-06-23
Here is my resluts to the commands you wanted me to run

> jaques@jaques-netbook:~$ sudo ls -al /dev/serial/by-id/usb*
ls: cannot access /dev/serial/by-id/usb*: No such file or directory
jaques@jaques-netbook:~$ sudo ls -al /dev/disk/by-id/usb*Mass_Storage*
ls: cannot access /dev/disk/by-id/usb*Mass_Storage*: No such file or directory
jaques@jaques-netbook:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0fce:d103 Sony Ericsson Mobile Communications AB 
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jaques@jaques-netbook:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: SEMC
 Product String: MMC Flash Card
Revision String:    0
-------------------------

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################
 After 20 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-netbook:~$ sudo ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-06-22 22:41 /dev/serial/by-id/usb-Sony_Ericsson_Sony_Ericsson_MD400g_Mobile_Broadband_USB_Modem_3578660212606100-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2010-06-22 22:41 /dev/serial/by-id/usb-Sony_Ericsson_Sony_Ericsson_MD400g_Mobile_Broadband_USB_Modem_3578660212606100-if03 -> ../../ttyACM1
lrwxrwxrwx 1 root root 13 2010-06-22 22:41 /dev/serial/by-id/usb-Sony_Ericsson_Sony_Ericsson_MD400g_Mobile_Broadband_USB_Modem_3578660212606100-if09 -> ../../ttyACM2
jaques@jaques-netbook:~$ sudo ls -al /dev/disk/by-id/usb*Mass_Storage*
ls: cannot access /dev/disk/by-id/usb*Mass_Storage*: No such file or directory
jaques@jaques-netbook:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0fce:d103 Sony Ericsson Mobile Communications AB 
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jaques@jaques-netbook:~$ 



---

### Post by mrpenguin on 2010-06-23
this is the results of what happens after i did the modeswitch

> jaques@jaques-netbook:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&Od1(U]~
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&Od1(}90~
--> PPP negotiation detected.
--> Starting pppd at Tue Jun 22 22:43:45 2010
--> Pid of pppd: 2000
--> Using interface ppp0
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> pppd: &#65533;Hj &#65533;Qj [18]Ij hIj &#65533;Ij &#65533;Ij 
--> Disconnecting at Tue Jun 22 22:43:46 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&2'yQO"~
CONNECT
--> Carrier detected.  Waiting for prompt.



This usualyy goes on for about 5 or 6 tries before it finally connects but then i stay connected for only about 1 minute to 10 minutes at the most before it disconnects me

---

### Post by alexfish on 2010-06-23
Hi

seems the modeswitch is working

so the only problem now is a configuration one

try these


Stupid Mode = 1

Auto DNS = 0

ISDN = 0

also try  different tty modem ports and see what happens ,

---

### Post by mrpenguin on 2010-06-23
> **alexfish said:**
> Hi

seems the modeswitch is working

so the only problem now is a configuration one

try these


Stupid Mode = 1

Auto DNS = 0

ISDN = 0

also try  different tty modem ports and see what happens ,

Do you mean change that in the wvdail config ? 
I don't see anything about a stupid mode
I did change auto dns and added the 0
Isdn already had the 0

Do you know why I can sometimes get connected but then get disconnected again 2 min later ??

---

### Post by mrpenguin on 2010-06-23
This is my wvdial config settings

> [Dialer rogers-nopin]

Phone = *99#

Username = wapuser1

Password = wap

Modem = /dev/ttyACM0

Baud = 460800

Init1 = AT+CPIN?

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = ATX3

Init4 = AT+CFUN=6

ISDN = 0

Modem Type = USB Modem

Init5 =AT +CGDCONT=1,"IP","internet.com","",0,0;

Auto DNS

Check DNS


I still dont know understand why I can sometimes get connected right away, other times only after the 10th try, sometimes get disconnected after 2 minutes and sometimes get disconnected after 10 minutes

---

### Post by mrpenguin on 2010-06-23
This is what a successful connection looks like

> jaques@jaques-netbook:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 002 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: SEMC
 Product String: MMC Flash Card
Revision String:    0
-------------------------

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
#####################
 After 21 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-netbook:~$ sudo usb_modeswitch -v 0fce -p d103 -O

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 001 ...
Not a storage device, skipping SCSI inquiry

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-netbook:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&:F[7f]}0[1f]}7~
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&:F[7f]}0Sz~
--> PPP negotiation detected.
--> Starting pppd at Wed Jun 23 23:21:06 2010
--> Pid of pppd: 1866
--> Using interface ppp0
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> local  IP address 10.196.113.48
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> primary   DNS address 64.71.255.198
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]
--> secondary DNS address 64.71.255.253
--> pppd: &#65533;&#65533;Z[08]&#65533;&#65533;Z[08][08]




now the question is how long before I get disconnected again and why does it happen ?

---

### Post by alexfish on 2010-06-24
Hi

there is a possibility the device may at times be configuring   and then sometimes not , you are also using an older version of the modeswitch

try installing the latest packages from

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

regards

alexfish

---

### Post by mrpenguin on 2010-06-25
Here is one thing I didnt mention ... One of my computers is a Asus Aspire one with Ubuntu Remix 10.04 on it and i have the most problems with it ... 

Ok .. I am about to loose it !!!
I have been using Ubuntu for a year now and do not wish to go to something else but i cant take this anymore ..

I just did a complete fresh install of Ubuntu remix 10.04 on my netbook and installed the latest modeswitch and no freaking difference at all !!!!!!!

It takes me about 5 tries before it finally connects and then cant stay connected for longer than 5 min

also on the top of the screen where the network connections is ... the broadband is not enabled ... if i click on it nothing happens
When i get connected trough wvdial then it finally comes on

I really need help !!

is this maybe a Remix broadband problem ???????????????

---

### Post by mrpenguin on 2010-06-27
bump

---

### Post by alexfish on 2010-06-28
Hi


Can you confirm that the device is not recognised by the Network Manager after doing the modeswitch , also when in this state you can sometimes connect via wvdial

if this been the case can you try removing the Modem Manager , "**don't** mark it for complete removal , then see what happens

also need to check ppp options

Code:

egrep -v '#|^ *$' /etc/ppp/options

ADDED: according to info this device takes around 25 seconds to switch ; so you must allow this lenght of time + a bit more for the drivers to configure; so from reading the info , once the device has switched then the possibly problems can be with the modem manager or the ppp options ; according to other info there is a git version of Modem Manager ; but will post details of this later:

Further Just checked my system and the modem manager shows Version 0.3 " Lucid" as in previous versions of Ubuntu 9.10 the NM and MM were both  0.8 : 
[https://launchpad.net/ubuntu/lucid/+source/modemmanager](https://launchpad.net/ubuntu/lucid/+source/modemmanager)

So this counters the posting where it has been suggested using the git version of 0.3 : This leads me to Thinking of installing MM 0.8 as in the version with Ubuntu 9.10 :

---

### Post by mrpenguin on 2010-06-29
I really dont understand anything about what you are talking about...
This is what happens when i connect to the internet ...

> jaques@jaques-netbook:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: SEMC
   Model String: MMC Flash Card
Revision String:    0
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################
 After 20 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-netbook:~$ sudo usb_modeswitch -v 0fce -p d103 -O

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 004 on bus 001 ...
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-netbook:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&x"$oWG~
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&x"$o};*~
--> PPP negotiation detected.
--> Starting pppd at Tue Jun 29 22:04:06 2010
--> Pid of pppd: 1534
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> local  IP address 10.196.29.122
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> primary   DNS address 64.71.255.198
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> secondary DNS address 64.71.255.253
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> Connect time 6.3 minutes.
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; 


Those last pppd: &#65533;&#65533;&#65533; &#65533;&#65533;&#65533; [18]&#65533;&#65533; h&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533;  means I am connected and can go on the internet ... but 2 - 10 min later i get disconnected again

Also my Network connections say that I am not connected to the internet ... it say No Network connection.
Every now and then .. I would say 2 out of 10 times it actually does say that I am connected to a network 

modeswitch does work !!! vwdial does work !!
I am still saying this is a Ubuntu Remix 10.04 Broadband issue !!!

---

### Post by mrpenguin on 2010-06-29
> jaques@jaques-netbook:~$ egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx
jaques@jaques-netbook:~$ 


I got that info wile being connected to the internet with my rogers rocket stick

---

### Post by mrpenguin on 2010-07-01
Did a big 105mb update on remix today .... It's even worse now ! Been trying to connect my broadband for the last hour with no luck at all !!!
Yesterday I connected but was disconnected after 5 min as usual !

Today it connects and disconnect 1 second later

---

### Post by mrpenguin on 2010-07-01
After an hour of connecting and then disconnecting right way it finally connected .... this is also one of those 2 out of 10 times that Network manager actually shows I am connected ... the other 8 out of 10 times when I am connected it shows no network connection.

---

### Post by mrpenguin on 2010-07-01
Ok so I have 3 different network manager bars when I am connected. 

1 : gray radar bar with red exclamation point ( suppose to show no connection but lots of times I am connected )

2 : green radar bar when I connect

3 : white bars like the ones I have on my phone to show connection strength 

I seriously don't understand why it shows one of 3 different things

---

### Post by alexfish on 2010-07-02
Hi

Are you alternating between the network manager and wvdial is so try to get one connection working first , for now I suggest wvdial since you have shown the device to use specific AT commands.

ATX3
AT+CFUN=6

I could suggest leaving these out of wvdial and see what happens also try the ATZ as the first init code

Added:
For New Install of 10.04 : wvdial also check out : Post #6  by GeorgeVita
 
[How To : Mobile Broadband Connections  [  Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

---

### Post by mrpenguin on 2010-07-04
ok... i think I might have figuured it out from one of the posts I read.
I have to exit AND remove the Rogers Rocket stick before doing the modem modeswitch

---

### Post by JackAbear on 2010-07-07
Mr.penguin,
Here are some thought that might be worth considering:
I have a rogers mf668 mobile on my home desktop for lack of any other service except 56k dial up in my area.
On some good days there are times in the day I get from 400kb/s up two 2mb/s .
Other days the signal barely reaches me and I get what the average 56k hookup gets,
about 5 to 50 kb/s, with frequent dropouts where I can barely get my e-mail, or have to wait later in the day to try again.
And this is with my well installed ( virus free ) hook-up on my PC with windows XP, and win 7 64 on seperate drives.
Two weeks ago Rogers even went out completely part of the day after we had a 5.1 earthquake and was useless all afternoon and night in this area on father's day. So please consider that sometimes it might be dropping out just because it really is dropping out.
Just to say that broadband is broadband, ...not cable.

I have been browsing your posts old and new all this week trying to set up this rocket stick with my new installation of 10.04 lucid Studio.
And yes!... I've been having basically the same problems.
then I would put the stick back in my XP set up to download Mod switch or dependencies and find out there's no signal there for half an hour, then whoops, 1.3mb/s.
I admit it's very difficult to set something up blind with uncontrolable variables such as these.
But I'm pretty certain that your posts with all the replies provide enough clues that will enable me to succeed.
I have a few ideas to try based mostly on info found in your threads, and if I succeed be assured, I will come back and post it here.
But I'm a brand new "newb" to linux and that's all I have for now (joined forum yesterday)
I hope this helps you in some way...man! you are so close...unless the kernel is the problem!.

C U later

Jack A bear

N.B. Oh! and make sure the PC's time/date/location is set-up right or rogers refuses to hook up anyway! that happened to me when I had just finished installing XP.
JackAbear is online now Report Post       Edit/Delete Message

---

### Post by mrpenguin on 2010-07-08
Hope you have been able to figure it out .... I do think now that a poor signal might have been one of the big problems ....
10.04 was for sure a problem but after a few updates it has been fixed because 4 weeks ago I was not able to connect at all.




Here is what works for me now :
I do this everytime I need to connect my rogers rocket stick

> Steps to connect Rogers Rocket stick

sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1

sudo usb_modeswitch -v 0fce -p d103 -O

sudo wvdial rogers-nopin


and this is my wdial config file
> sudo gedit /etc/wvdial.conf

you only need to do this once

> 


[Dialer rogers-nopin]

Phone = *99#

Username = wapuser1

Password = wap

Modem = /dev/ttyACM0

Baud = 460800

Init1 = AT+CPIN?

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = ATX3

Init4 = AT+CFUN=6

ISDN = 0

Modem Type = USB Modem

Init5 =AT +CGDCONT=1,"IP","internet.com","",0,0;

Auto DNS

Check DNS



Here is a successful connection ....

> jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 002 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: SEMC
   Model String: MMC Flash Card
Revision String:    0
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################
 After 20 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0fce -p d103 -O

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 003 on bus 002 ...
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: Sony Ericsson MD400g Mobile Broadband USB Modem
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
######
 After 6 seconds: device came back, proceeding
Sending Sony control message again ...
 OK, control message sent
-> device should be stable now. Bye.

jaques@jaques-laptop:~$ sudo wvdial rogers-nopin
--> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check DNS"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN?
AT+CPIN?
+CPIN: READY
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+CFUN=6
AT+CFUN=6
OK
--> Sending: AT +CGDCONT=1,"IP","internet.com","",0,0;
AT +CGDCONT=1,"IP","internet.com","",0,0;
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&[15]}-] }.[1c]~
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&[15]}-] Bq~
--> PPP negotiation detected.
--> Starting pppd at Thu Jul  8 13:11:45 2010
--> Pid of pppd: 1883
--> Using interface ppp0
--> pppd: &#65533;X
-->  &#65533;a
-->  [18]Y
-->  hY
-->  &#65533;Y
-->  &#65533;Y
-->  
--> pppd: &#65533;X
-->  &#65533;a
-->  [18]Y


---

### Post by JackAbear on 2010-07-09
Thank you very much,
 I will certainly keep this as my main reference to check my results, knowing we're in the same province, same provider.
Don't forget I'm in my second week with all this, and the learning curve at the moment seems extremely steep for the newb...though not impossible...making some small progress I finally just got** lsusb** to show the stick as a 2000 usb memory stick after three days of trying. so I must have done something right at some point. lol


However my R-stick is the Rogers mf668.(ONDA communications)
 I wonder if there would be slight differences in the settings or if the MODEM side of the stick would still be "0017" regardless of wether it be a 627, 636, 668 or sony erickson 400?
I wonder if the** 0017** for modem side has anything to do with the country we are in and would be different in another country?
Need some clarification on  where the 103 came from, and what it means in** sudo usb_modeswitch -v 0fce -p d103 -O**
Should my commands also use 103 or be different for the 668?
As you can see I wonder a lot!

But my **main problem** at the moment is that I'm looking for the right Gnome network** manager** that includes **Broadband wireless**, since the one included in UbuntuStudio 10.04  is called Network admin and doesn't include it, I know I must change that, but packages all seem to call it Network **admin** rather than **manager**?... a little confused with that!  are they one and the same thing?
Which package version(deb) am I supposed to be looking for that includes Broadband( keeping in mind I cannot get  auto updates until the dongle connects.)
I think that is the main hurdle before I can connect.
Any clarification would help me sort this out
Merci beaucoups.
Jack A bear  (Jacques)

---

### Post by mrpenguin on 2010-07-11
I really have no idea about any of that ... I only use Modeswitch and wvdial to connect my rogers rocket stick, nothing else.

---

### Post by JackAbear on 2010-07-11
bump
see next post below

---

### Post by JackAbear on 2010-07-15
Y'all check out my new POST below,  explains the procedure I came up with, that actually works as good as with windows really!

[http://ubuntuforums.org/showthread.php?p=9593938#post9593938](http://ubuntuforums.org/showthread.php?p=9593938#post9593938)

Even though the method is good, Rogers stick is extremely intermitent in  my area, and cuts out often even on the Windhose XP setup, and when it  cuts out  it remains at zero kb/s and you cannot browse, until you shut  down it's software, re-load the software, and hope it will connect the  next time. sometime you have to wait a few hours and try again, 
You can can expect the same thing with Ubuntu, not Ubuntu's fault in  most  cases...and restarting Ubuntu is the equivalent of re-loading the  software in a windows set-up. I would have had to write another three  pages to cover all that in detail...And  the stick slows down when hot,  and shuts off when too hot...so put a fan on it if you download long  updates.and stuff..
Hope this helps also!

---

