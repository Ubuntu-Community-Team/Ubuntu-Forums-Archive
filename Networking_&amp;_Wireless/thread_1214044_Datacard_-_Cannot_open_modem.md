---
title: "Datacard - Cannot open modem"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by sundar261 on 2009-07-15
Hi,

I am having issues with my internet connectivity through datacard. I have USB modem (Huawei Technologies Co., Ltd. E620 USB Modem). I connect to internet through Gnome PPP utility. The connection works fine when I connect it for the first time. But have a problem when it disconnects due to poor signal. When I reconnect I get a message "Cannot open modem". Even removing the modem and putting it back after some time does not help. The problem is solved only when I restart the laptop.

Any pointer in resolving the issue will be of great help to me.

To me it looks like a Linux problem with the usb modem. Not sure the resources are held when the first failure happens and is not cleared properly. I would get the same error message if I have a PPP connection and try to connect again.

I am running it on a Lenovo N100 laptop with Ubuntu 8.04.

-Sundar

---

### Post by ramnarayan on 2009-07-15
see
[http://freedomyug.wordpress.com/2008/08/15/setting-up-reliance-usb-modem-huawei-technologies-co-ltd-e620-usb-modem-on-ubuntu-84-lts-%E2%80%9Chardy-heron%E2%80%9D/](http://freedomyug.wordpress.com/2008/08/15/setting-up-reliance-usb-modem-huawei-technologies-co-ltd-e620-usb-modem-on-ubuntu-84-lts-%E2%80%9Chardy-heron%E2%80%9D/)

however it depends on what version of Ubuntu you have -

** i have a usb cdma data card and this is my how to for a similar device

this is what i do (yes even on 9.04)
Quick Guide to ZT 880 Reliance Data card on Linux Ubuntu 8.10

A simple how to setup a reliance ZT 880 usb data card on Ubuntu 8.10 (the guide should work for anything from Ubuntu 7.04 upwards)

This howto has been adapted from other howto's to setup similar USB Data Cards, there are no gaurantees and warranties – this works for me and I have had no negatives so far. Alss don't expect support from Reliance for this. If you want another solution run a search for Ubuntu+zt 880 + India you should get other usable results.


So Here goes

Open a terminal and run the following (copy and paste the command after -$ or type them out carefully) 

1. mknod's (it might already be there but making it again won't do anything)

-$ mknod /dev/ttyUSB0 c 188 0
-$ mknod /dev/ttyUSB1 c 188 1
2. load usb serial driver
~$ ls 
(to know if the id and vendor is correct or same on your device) do lsusb -v and see the appropriate entry) the above one is correct since I did it on my machine
$ lsusb -v 
snipped (and key parts bolded for your reference)
Bus 001 Device 003: ID 19d2:fffd  
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.01 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16 
  idVendor           0x19d2 
  *idProduct          0xfffd *
  bcdDevice            0.00 
  iManufacturer           1 ZTE, Incorporated 
  iProduct                2 ZTE CDMA Tech 
  iSerial                 3 Serial Number
3. Run “dmesg” to see if the device is attached to usb port
-$ dmesg 
[  570.256642] usbcore: registered new interface driver usbserial 
[  570.256670] usbserial: USB Serial support registered for generic 
[  570.256689] usbserial_generic 1-1:1.0: generic converter detected 
[  570.256878] usb 1-1: generic converter now attached to ttyUSB0 
[  570.256888] usbserial_generic 1-1:1.1: generic converter detected 
[  570.256962] usb 1-1: generic converter now attached to ttyUSB1 
[  570.256972] usbserial_generic 1-1:1.2: generic converter detected 
[  570.257050] usb 1-1: generic converter now attached to ttyUSB2 
[  570.257076] usbcore: registered new interface driver usbserial_generic 
[  570.257080] usbserial: USB Serial Driver core 
to be clear remove device and run sudo dmesg -c – see output then attach device and run sudo dmesg -c again 
dmesg -c  clears the ring buffer and shows only latest changes.

4. SETUP wvdial
~$ sudo gedit /etc/wvdial.conf 
copy and paste the below into your wvdial.conf file
[Modem0] 
Modem = /dev/ttyUSB0 
Baud = 115200 
SetVolume = 0 
Dial Command = ATDT 
Init1 = ATZ 
FlowControl = Hardware (CRTSCTS) 

[Dialer zt880] 
Username = yourphonenumber
Password = yourphonenumber 
Phone = #777 
Stupid Mode = 1 
Inherits = Modem0 

save and exit

5. Unplug and replug the USB device 
you can run dmesg -c to know whats happening

6. FINALLY
~$ sudo wvdial zt880 
which should result in:

--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Modem initialized. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
CONNECT 
--> Carrier detected.  Starting PPP immediately. 
--> Starting pppd at Tue Dec  9 13:06:48 2008 
--> Pid of pppd: 11812 
--> Using interface ppp0 
--> pppd: &#65533;_[07] 
--> pppd: &#65533;_[07] 
--> pppd: &#65533;_[07] 
--> pppd: &#65533;_[07] 
--> local  IP address 220.226.82.219 
--> pppd: &#65533;_[07] 
--> remote IP address 220.224.135.75 
--> pppd: &#65533;_[07] 
--> primary   DNS address 202.138.103.100 
--> pppd: &#65533;_[07] 
--> secondary DNS address 202.138.96.2 
--> pppd: &#65533;_[07] 

7. Exiting
Control C in the terminal and the connection should close

Happy Surfing

Other Minor tips
1. to copy or paste from or into a terminal use shift+control+ c or v
2. terminal means a command line interface tool (can be accessed by Applications &#8594; Accessories &#8594; terminal)
3. f you don't understand what a command does run -$ man “command” this should show you the man pages of this command
4. You can rename the wvdial dialer name “zt880” to anything you like and when running wvdial remember the name you chose and run -$ wvdial “yourchosenname” to access the internet

---

### Post by pradeepthundiyil on 2010-05-14
Hi,

I was using gnome-ppp in ubuntu 9.10 to connect my reliance datacard. Recently I installed Ubuntu 10.04  and I tried the same procedure with Ubuntu 10.04, but unfortunately I 'm getting an error. Kindly have a look into it.. Expecting your valuable suggestions.. Thank you..

I'm pasting the **Dialer Log** here
*****************************************************************************************************
                                                                        **DIALER LOG**
*****************************************************************************************************
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
CONNECT 230400
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Fri May 14 06:32:00 2010
--> Pid of pppd: 1592
--> Disconnecting at Fri May 14 06:32:00 2010
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

---

### Post by ramnarayan on 2010-05-20
[QUOTE=pradeepthundiyil;9296510]Hi,
                                                                        **DIALER LOG**
*****************************************************************************************************
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"

There is an error in your wvdial.conf (i think) so can you post your wvdial.

--> Carrier detected.  Waiting for prompt.
this means your device is working and the problem is else

--> The PPP daemon has died: pppd options error (exit code = 2)

the error is 
 2      An error was detected in processing the options given,  such  as
              two mutually exclusive options being used.

so there is a conflict in the options provided by you.

Kindly post your wvdial , and also check your options 

second kindly confirm what device you are using.

use
lsusb -v in your terminal and find the section which refers to your device and post the details as below

idVendor, idProduct        

this will help know what is wrong

ram

---

