---
title: "virginmobile datamax not working"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by preetamk on 2010-12-05
Dear friends, Help me out.
I am using a virginmobile datamax connection. I had absolutely no problem using it in ubuntu 9.10. I am unable to use that in ubuntu 10.10

Instructions that I had followed for 9.10 are the following.
1. The datamax usb will appear as a drive. The first step is to right click over it and press eject.------- In 10.10, the drive appears but its name appears as 'SIT Mass Storage' instead of the usual 'vFlash'
2. There is no option in 10.10 to eject the drive. It says safely remove drive. When I do that it says

Unable to Stop Dribe
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

3. Only after ejecting 9.10 would recognise the drive as a modem and from then on it was easy to install it ------ In 10.10, the ubuntu recognises it as a modem straight away. And even after all configurations I do it still does not connect

4. I tried connecting through wvdial. This was the response

user: wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
ttyACM0<Info>: Device or resource busy
Modem Port Scan<*1>: ACM0 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)



If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by preetamk on 2010-12-05
Bus 005 Device 003: ID 1b7d:0001

This is the value terminal returns for lsusb

---

### Post by alexfish on 2010-12-05
hi

ttyACM0<Info>: Device or resource busy

possible indicates a daemon or other connection manager is holding on to the device

if you have Network Manager installed try


Code:

sudo killall modem-manager

---

### Post by preetamk on 2010-12-05
thank you, thats not working. My guess is that between the releases there is a new software usb-modeswitch that is probably creating the problem

The usb modem have 2 ports - one storage and the other modem. in windows typically only one can be active at a moment. And in the prev ubuntu 9.10 I was asked o eject the storage part of it so that i can access the modem.

In 10.10, both the storage and the modem part of is recognised but both of them don't open. I can try uninstalling a few softwares and see how it works.

unfortunately after deleting usb modes-switch both the storage and the modem part did not show up

---

### Post by preetamk on 2010-12-05
I have tried uninstalling various usb* files.. Nothing seems to work..

---

### Post by alexfish on 2010-12-05
hi

the main difference between 10.10 and earlier disto's 

usb_modeswitch is part of the distro 

so question was usb_modeswitch required in the other version of ubuntu


if not try

Code:

sudo gedit /etc/usb_modeswitch.conf

then set the line "DisableSwitching=1"
this will disable the modeswitching
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=1


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

if this does not work

can post detail of

Code:

[COLOR=Blue]usb-devices[/COLOR]


locate the lines which indicate the device and post only those lines

---

### Post by preetamk on 2010-12-06
Sorry, alexfish.. I made a mistake the previous time.. This was the response after killall modem manager

Still conf file not opening


preetam@preetam-acer:~$ wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- Manufacturer: QUALCOMM INCORPORATED
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp2140': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

### Post by preetamk on 2010-12-06
And disabling the modem switch disables both the modem and storage part

---

### Post by preetamk on 2010-12-06
> **alexfish said:**
> 
Code:

[COLOR=Blue]usb-devices[/COLOR]


locate the lines which indicate the device and post only those lines
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1b7d ProdID=0001 Rev=00.00
S:  Manufacturer=EpiValley Incorporated
S:  Product=EpiValley CDMA USB Modem
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by alexfish on 2010-12-06
Hi

looks ok

just double checked your call to configure wvdial

should try

Code:

sudo wvdialconf

also look at post #9

[How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

---

### Post by preetamk on 2010-12-06
preetam@preetam-acer:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CRM=1
AT+CRM=1
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
preetam@preetam-acer:~$ sudo gedit /etc/wvdial.conf
preetam@preetam-acer:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CRM=1
AT+CRM=1
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 3600000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Dec  6 20:21:18 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 4475
--> Using interface ppp0
--> pppd: (E[06] @C[06] `K[06] 
--> pppd: (E[06] @C[06] `K[06] 
--> pppd: (E[06] @C[06] `K[06] 
--> pppd: (E[06] @C[06] `K[06] 
--> Disconnecting at Mon Dec  6 20:21:22 2010
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

---

### Post by preetamk on 2010-12-06
wvdial.conf details

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CRM=1
Stupid Mode = 1
Modem Type = USB Modem
Phone = #777
ISDN = 0
Password = hsia
New PPPD = yes
Username = [email]hsia@ttsl.vmi.com[/email]
Modem = /dev/ttyACM0
Baud = 460800

---

### Post by preetamk on 2010-12-06
attaching a page from the manual...

Thank you Alexfish for patiently helping me.. I still don't know what is the problem

---

### Post by preetamk on 2010-12-06
Init1 = AT
Init2 = ATE0V1&D2&C1S0=0
Init3 = ATS7=60
Init4 = ATS0=0

I tried this from your post.. Not helping

I changed the Init1, Init2 values as given in the manual and kept the Init3, 4 as in your post.. Not helping

Removed the New pppd= yes line.. Not helping

Tried googling ppd error exit code = 19... Couldn't understand a word

In man pppd exit code 19 reads "We failed to authenticate ourselves to the peer"

pppd says it uses 3 protocols EAP, CHAP, and PAP.. Of the log that was produced by wvdial -  the pppd has tried CHAP and PAP.. It seems not to have tried EAP - will that make a difference?

---

### Post by preetamk on 2010-12-06
Dear oh dear

tried running wvdial as root

sudo wvdial
preetam@preetam-acer:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: AT+CRM=1
AT+CRM=1
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 3600000
~[7f][03] !E  0h_@ m[06][04]E(\%[1e][0e]cDE
[08][01]=a}]Gu    p[02][7f][7f],D  [02][04][05]4[01][01][04][02]Ei~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Dec  6 22:15:17 2010
--> Pid of pppd: 5077
--> Using interface ppp0
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> local  IP address 14.99.68.69
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> remote IP address 172.29.244.49
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> primary   DNS address 121.242.190.210
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
--> secondary DNS address 121.242.190.180
--> pppd: &#65533;&#65533;{[08]&#65533;&#65533;{[08]&#65533;&#65533;{[08]
 

still did not work.. browser did not connect

as mentioned in the manual I tried

sudo cp /etc/ppp/resolv.conf /etc/

oh god it worked.!!!!!!!!!!!!!!!!!!!!

Thank you.. Thanks a lot alexfish

---

### Post by alexfish on 2010-12-06
hi

good news

now check your permissions for "dialout" and "dip"

Code:

[COLOR=Blue]id[/COLOR]

if can't see (dialout) and (dip)

try

Code:

[COLOR=Blue]sudo adduser <YOURUSERNAME> dip[/COLOR]
[COLOR=Blue]sudo adduser <YOURUSERNAME> dialout[/COLOR]


alexfish

---

### Post by alexfish on 2010-12-06
dam thing double posted

---

### Post by preetamk on 2010-12-07
Gnome PPP is working great.
And id shows up both dialout and dip

But can you clarify whether Gnome PPP is working because of the earlier priming with the wvdial or is an independent application in itself
(I am a noob at this... really sorry for pestering)
Thank you

---

### Post by alexfish on 2010-12-08
Hi

Gnomeppp only passes on the info to wvdial to use

but has one limitation , only one dialup connection at a time

where as wvdial can have multiple connections in the config file

called by name

EG:

wvdial myname1

wvdial myconnection2  and so on

---

