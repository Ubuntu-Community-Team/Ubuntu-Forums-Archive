---
title: "Huawei ETS 2288 CDMA phone on Ubuntu 9.04 (not working)"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by ramnarayan on 2009-06-14
Hi

recentlHave unsuccessfully tried to get the Huawei ETS 2288 CDMA (fixed Wireless Phone)  not working on Ubuntu 8.04 and 8.10.

Since then managed to lay hands on Ubuntu 9.04 and wanted to see if it
fared any better.

It did in one sense which makes me hopeful that it will work but
somewhere down the line something is still amiss and i think some of
you folks mught to able to help crack this one.

Ok so the details are

Post Fresh Installation of Ubuntu 9.04 (Jaunty Jackalope)

On Plugging the device in
:~$ lsusb
Bus 002 Device 005: ID 0451:3410 Texas Instruments, Inc. TUSB3410
Microcontroller

:~$ sudo dmesg -c
[  977.188070] usb 2-2: new full speed USB device using uhci_hcd and address 6
[  977.435283] usb 2-2: configuration #1 chosen from 1 choice
[  977.438219] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter
converter detected
[  977.438230] usb 2-2: firmware: requesting ti_usb-v0451-p3410.fw
[  977.443570] usb 2-2: firmware: requesting ti_3410.fw
[  978.088081] usb 2-2: reset full speed USB device using uhci_hcd and
address 6
[  978.288143] usb 2-2: device firmware changed
[  978.288182] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[  978.288400] usb 2-2: USB disconnect, address 6
[  978.400091] usb 2-2: new full speed USB device using uhci_hcd and address 7
[  978.675286] usb 2-2: configuration #1 chosen from 2 choices
[  978.683422] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter
converter detected
[  978.683442] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[  978.687218] ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter
converter detected
[  978.689756] usb 2-2: TI USB 3410 1 port adapter converter now
attached to ttyUSB0

The device is regonized and attached to ttyUSB0

Checking if ttyUSB0 exists
$ ls /dev/ttyU*
/dev/ttyUSB0

It does

Comments on Ubuntu 9.04 (jaunty Jackalope)
1.WVDIAL and WVDIALCONF are not installed by default – other wise this
would have been quite easy to setup

2.Even Though the device is regonized there seems to be no method of
setting it up to use.

So needed to setup wvdial manually as there was no internet connection
possible on Ubuntu.

Searched in Google and found that am not the only one missing wvdial
and some people have already addressed the problem.

[http://ubuntuforums.org/showthread.php?t=846522](http://ubuntuforums.org/showthread.php?t=846522)

check out George Vita's helpful help note at

[http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html)

before installing the files from this i reloaded the repositories to
access only the cd since there were some conflicts between the
downloaded files and what apt was seeing as later versions,

Installed the files in the following order. Gdebi picked up the files
and installed them without much hassle , rather no hassle.

1. libxplc0.3.13_0.3.13-1_i386.deb
2. libwvstreams4.4-base_4.4.1-1.1_i386.deb
3. libwvstreams4.4-extras_4.4.1-1.1_i386.deb
4. libuniconf4.4_4.4.1-1.1_i386.deb
5. wvdial_1.60.1+nmu2_i386.deb

Ran wvdialconf
:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   USB0

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

Till date had never needed to run wvdialconf to setup this device on
Ubuntu 7.04, 7.10 and pclinux0s version

so decided to short cut to wvdial itself

copied the following parameters into wvdial.conf
~$ sudo gedit /etc/wvdial.conf
[sudo] password for ram:

[Modem0]
Modem = /dev/ttyUSB0
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
# Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
Idle Seconds = 90
Auto Reconnect = off

[Dialer XX]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = xxxxxxx
Password = xxxxxxx
# Inherits = Modem0

**

Then tried wvdial

$ sudo wvdial 93
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Input/output error

So no idea why this error

**
Tried the following:

Did a
$ sudo mknod /dev/ttyUSB1 c 188 1

also unplugged and replugged the device
$ sudo wvdial 93
[sudo] password for ram:
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Input/output error

same error

so now going for reboot
 Post reboot
dmesg

 USB Serial support registered for TI USB 3410 1 port adapter
 USB Serial support registered for TI USB 5052 2 port adapter
 ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter converter detected
 ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
 usbcore: registered new interface driver ti_usb_3410_5052
 ti_usb_3410_5052: v0.9:TI USB 3410/5052 Serial Driver
 ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter converter detected
 usb 2-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0

$ sudo wvdial 93
[sudo] password for ram:
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error

 it started but then something crashes again.

**
Till this gets resolved am back to Ubuntu 7.10

Any ideas / tips etc

thanks
ram

---

### Post by ramnarayan on 2009-06-14
ANother similar thread is at

Another thread is at [http://ubuntuforums.org/showthread.php?t=993888&highlight=Huawei+ets+2280](http://ubuntuforums.org/showthread.php?t=993888&highlight=Huawei+ets+2280)

 but this thread does not narrow to the problem (i think)

ram

---

### Post by ramnarayan on 2009-07-01
Hi

Initially the problem seemed with a bug in the kernel, but since thats been recitified am still facing the problem

latest outputs and what i have tried are below

$ dmesg
[ 2463.820056] usb 2-2: new full speed USB device using uhci_hcd and address 6
[ 2464.011217] usb 2-2: configuration #1 chosen from 1 choice
[ 2464.017144] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter converter detected
[ 2464.017151] usb 2-2: firmware: requesting ti_usb-v0451-p3410.fw
[ 2464.028810] usb 2-2: firmware: requesting ti_3410.fw
[ 2464.612056] usb 2-2: reset full speed USB device using uhci_hcd and address 6
[ 2464.755125] usb 2-2: device firmware changed
[ 2464.755151] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[ 2464.756857] usb 2-2: USB disconnect, address 6
[ 2464.924057] usb 2-2: new full speed USB device using uhci_hcd and address 7
[ 2465.143219] usb 2-2: configuration #1 chosen from 2 choices
[ 2465.145169] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter converter detected
[ 2465.145180] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[ 2465.147201] ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter converter detected
[ 2465.147273] usb 2-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0

$ wvdial 93
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Wed Jul  1 22:03:21 2009
ram@ram-laptop:~$ sudo wvdial 93
[sudo] password for ram: 
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error

Details from wvdial.conf
[Modem0]
Modem = /dev/ttyUSB0
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
# Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
Idle Seconds = 90
Auto Reconnect = off

[Dialer 93]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = 5961211393
Password = 5961211393
# below line error in spelling crtcts which should be crtscts
# PPPD Options = crtcts multilink usepeerdns lock defaultroute
# PPPD Options = crtscts multilink usepeerdns lock defaultroute
Inherits = Modem0

Also tried the followin GUI front ends for wvdial and ppp and pppoe

**
gnome ppp
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error

kppp
unable to open modem
****
gpppon
no response 

***
So what to do

is there a bug in wvdial now or what do i need to do to get this device working.

I am using it (right now on Ubuntu 7.10) so why in the name of XXXX cannot it work on 9.04 . 

frustrated and much irritated

ram

---

### Post by ramnarayan on 2009-07-05
Hi

BUMP
Re: Huawei ETS 2288 CDMA phone on Ubuntu 9.04 *(STILL not working)*

which i think is the way to say hey anyone with anything new to say on this ??

---

