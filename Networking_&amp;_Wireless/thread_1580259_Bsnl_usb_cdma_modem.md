---
title: "Bsnl usb cdma modem"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by bharuchas on 2010-09-23
Hi, 
I am a newbie at Ubuntu and have UNR 10.04 on my benq joybook. I have recently purchased a USB MODEM from BSNL which is a CDMA 1x modem. It works fine on my desktop which has windows XP, but on my laptop it shows connecting and immediately shows "Network Disconnected". I have tried a lot of permutations and combinations but it just does not connect. I have both wvdial and network manager, bot detect it, but when i try to connect it shows connecting and then disconnects. I browsed through a lot of forums for this, and some seemed close and i tried practically all, but nope, it just does not happen.
Any help would be highly appreciated. 
Sohrab Bharucha

---

### Post by dineshs on 2010-09-23
please post the results of the following commands so that someone can help you
```
lsusb
```
```
dmesg | grep -e "modem" -e "tty"
```
(Ref [this]("http://ubuntuforums.org/showthread.php?t=1466490") guide by alexfish)

---

### Post by ubun2warrior on 2010-09-23
hi

simply right click on the network manager icon on ur panel> select edit connections> go to mobile broadband and select bsnl and then click on edit> now there in the advanced option set the APN as bsnlnet and click on Apply.

i think this will work

regards
ubun2warrior

---

### Post by bharuchas on 2010-09-24
For Dineshs
lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05c6:3197 Qualcomm, Inc. CDMA Wireless Modem/Phone
Bus 003 Device 002: ID 18e8:6252 Qcom 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0408:13e0 Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
-------------------------
sohrab@sohrab-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[  835.567041] USB Serial support registered for moto-modem
[  835.567150] moto-modem 3-1:1.0: moto-modem converter detected
[  835.567595] usb 3-1: moto-modem converter now attached to ttyUSB0
[  835.567659] moto-modem 3-1:1.1: moto-modem converter detected
[  835.568543] usb 3-1: moto-modem converter now attached to ttyUSB1
[  835.568673] usbcore: registered new interface driver moto-modem

---

### Post by bharuchas on 2010-09-24
For Ubun2warrior

In my network connections, i have the bsnl connection, and in that when i edit i do not get advanced settings. I have 3 tabs,
1. PPP Settings which has authentication, Comression and echo
2. Mobile broad band, which has #777, user ID and password
3. IPv4 settings.
NO where could i find the word APN
Can you advice?

---

### Post by dineshs on 2010-09-24
Can you run```
sudo wvdialconf
```
Then see what is in */etc/wvdial.conf using the following command*```
sudo gedit /etc/wvdial.conf
```
It should show something like```
[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Modem Type = Analog Modem 
ISDN = 0 
Phone = #777 
Modem = /dev/ttyUSB0 
Username = YOUR_USERNAME 
Password = YOUR_PASSWORD 
Baud = 460800 
Stupid Mode = 1 
Auto DNS 
Check Def Route 

```
Now try to connect using```
sudo wvdial 
```

---

### Post by bharuchas on 2010-09-24
ohrab@sohrab-laptop:~$ sudo wvdialconf
[sudo] password for sohrab: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: QUALCOMM INCORPORATED
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
----------------

--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
sohrab@sohrab-laptop:~$ sudo gedit /etc/wvdial.conf
sohrab@sohrab-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

---

### Post by dineshs on 2010-09-24
Please run```
sudo gedit /etc/wvdial.conf
```and post the result

---

### Post by bharuchas on 2010-09-24
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone = #777
; Password = 9684026606
; Username = [email]9684026606@aaavd.in[/email]

---

### Post by dineshs on 2010-09-24
make it ```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = #777
Password = 9684026606
Username = 9684026606@aaavd.in
```ie Remove the ; sign before phone,password and username and try```
sudo wvdial
```

---

### Post by bharuchas on 2010-09-24
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.

---

### Post by dineshs on 2010-09-24
Can you add ```
Carrier Check = no
Stupid mode = on
```to  /etc/wvdial.conf using ```
sudo gedit /etc/wvdial.conf
```
ref [this]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9")

---

### Post by bharuchas on 2010-09-24
this is the final config
----------
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = #777
Password = 9684026606
Username = [email]9684026606@aaavd.in[/email]
Carrier Check = no
Stupid mode = on
-------------
this is the result

sohrab@sohrab-laptop:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Fri Sep 24 15:42:18 2010

---

### Post by dineshs on 2010-09-24
You may try to send a private message to alexfish.Maybe he can suggest something

---

### Post by ubun2warrior on 2010-09-24
> **bharuchas said:**
> For Ubun2warrior

In my network connections, i have the bsnl connection, and in that when i edit i do not get advanced settings. I have 3 tabs,
1. PPP Settings which has authentication, Comression and echo
2. Mobile broad band, which has #777, user ID and password
3. IPv4 settings.
NO where could i find the word APN
Can you advice?

hi 

In the IPv4 tab, just check if the Method: Automatic (PPP) is set or not...

regards

ubun2warrior

---

### Post by bharuchas on 2010-09-25
> **ubun2warrior said:**
> hi 

In the IPv4 tab, just check if the Method: Automatic (PPP) is set or not...

regards

ubun2warrior
yes it is, anything else i can do, it just disconnects.

---

### Post by Hiren Modi on 2010-09-25
You can Directly contact with Bsnl usb customer care , they will give you a better solution for your problem.....

---

### Post by bharuchas on 2010-09-25
> **Hiren Modi said:**
> You can Directly contact with Bsnl usb customer care , they will give you a better solution for your problem.....
I tried that as well, their customer care could not help me due to the linux i am using, they seem familiar only with windows, not even mac.

---

### Post by ubun2warrior on 2010-09-25
hi

try installing usbmodeswitch from synaptics and restart ur comp, and create a fresh connection, delete any previous bsnl connection..

may be this will work

i have myself used bsnl, airtel, reliance, tata photon, they all work out of the box in ubuntu..

regards

ubun2warrior

---

### Post by bharuchas on 2010-09-27
> **ubun2warrior said:**
> hi

try installing usbmodeswitch from synaptics and restart ur comp, and create a fresh connection, delete any previous bsnl connection..

may be this will work

i have myself used bsnl, airtel, reliance, tata photon, they all work out of the box in ubuntu..

regards

ubun2warrior
Nope boss just not happening, it just disconnects.

---

### Post by alexfish on 2010-09-27
hi

the dial command 777# does not appear to be working

can you try ATDT*99# , post details of wvdial output to see if it responds

---

### Post by bharuchas on 2010-09-28
> **alexfish said:**
> hi

the dial command 777# does not appear to be working

can you try ATDT*99# , post details of wvdial output to see if it responds

This is the output
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
--> Sending: ATQ0
--> Re-Sending: ATX3
--> Modem not responding.
I feel there is something basic that i am not doing, why should it not happen?

REgards,
Sohrab.

---

### Post by dineshs on 2010-09-28
Please wait for alexfishs response.Meanwhile can you try to install gnome-ppp and give it  a try?

---

### Post by alexfish on 2010-09-28
> **bharuchas said:**
> This is the output
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
--> Sending: ATQ0
--> Re-Sending: ATX3
--> Modem not responding.
I feel there is something basic that i am not doing, why should it not happen?

REgards,
Sohrab.

hi

can you post details of the wvdial.conf

can be done from the terminal

Code:

cat /etc/wvdial.conf

---

### Post by vtired on 2010-11-02
Is there any place where one get get a good tutorial on how to use wvdial on Ubuntu? On Fedora 13 I just install usb-modeswitch, wvdial, run as root on the terminal wvdialconf and the network manager recognises the modem. The rest is just selecting the provider from the list on the network manager. I have compared /etc/wvdial.conf on both my Ubuntu 10.04 and Fedora 13. They are exactly the same. But on Ubuntu the usb modem, telsey everyweb, won't work.

---

