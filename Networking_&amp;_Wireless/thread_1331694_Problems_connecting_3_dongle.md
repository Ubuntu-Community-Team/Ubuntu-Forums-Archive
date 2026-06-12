---
title: "Problems connecting 3 dongle"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by judith_sw on 2009-11-19
Hi,

Despite early problems, I now have the latest version of Ubuntu up and running on my HP 2133, including wireless access. However, I am still unable to get the 3 dongle recognised and connected. The details are as follows:


[LIST]
[*]Huawei E156G dongle for 3 network in the UK.
[*]Previously used with Windows laptop.
[*]When I connect in Windows, I get a connection console that shows the strength of the signal and whether I connect or not - on the netbook, the dongle shows up as a device, but when I click on it, it opens as a folder, showing its contents. The installation process doesn't happen.
[*]Although I could previously enter the "edit mobile broadband connections", it has now started to tell me I have insufficient privileges to start the editor!
[/LIST]

It seems that I have a couple of problems here ...as well as my limited knowledge of Ubuntu. I would really like to get the dongle working, as I am at a conference tomorrow and will need to access the internet during the day.

I'm going to need some very basic instruction, but if anyone knows how to get me up and running and doesn't mind taking me through it step by step, I would be very grateful

Thank you :)

---

### Post by judith_sw on 2009-11-19
A little update ... I've managed to get the dongle recognised by adding it as an additional device (edit allowed me to do this). The netbook recognises it as a mobile broadband connection, listing it as "available", but it will not connect.

When I double-click on the desktop icon, the dongle shows up as cdrom0 with no files in it. When I connect another icon appears with all the files in it. This is listed as 3Connect.

Any ideas?

---

### Post by mali2297 on 2009-11-19
There is a guide here:
[http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/](http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/)

The person uses Huawei E220 but I would think the instructions also applies for your modem.

---

### Post by judith_sw on 2009-11-19
Hi,

I just ran the wvdialconf instruction and got the following output:

judith@judith-laptop:~$ wvdialconf
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
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp2774': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

The page you linked to suggests then doing some fixes ... this is where I am unsure what to do. I can see that there are some problems here. Could you suggest what to do?

---

### Post by BlissBryan on 2009-11-19
What about running this command as root (or using sudo)?

---

### Post by judith_sw on 2009-11-19
Would this just be:

sudo wvdialconf - I tried this and got what looks like the same output.

How do I run the command as root ... I've not done this before.

Thanks!

---

### Post by mali2297 on 2009-11-19
Yes, run it as root:
```

sudo wvdialconf

```
Then open the configuration file in an editor:
```

gksudo gedit /etc/wvdial.conf

```
Do the fixes in the instructions. Save the file. Finally, run
```

sudo -b wvdial

```
to try connecting.

---

### Post by mali2297 on 2009-11-19
> **judith_sw said:**
> Would this just be:

sudo wvdialconf - I tried this and got what looks like the same output.

How do I run the command as root ... I've not done this before.

Thanks!

If wvdialconf doesn't work, try creating /etc/wvdial.conf from scratch. Copy these lines to the file:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Username = three
Password = three
Modem = /dev/ttyUSB1
Dial Command = ATDT
Baud = 9600

```

---

### Post by judith_sw on 2009-11-19
Hi,
I typed in the commands exactly as per the webpage fix. It tried to connect, but failed. The output is:

judith@judith-laptop:~$ sudo -b wvdial
judith@judith-laptop:~$ --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Thu Nov 19 22:49:23 2009

I'm wondering if I should have also put the [Dialer three] fix? The serialport seems to be a problem. This is what is now in the wvdialconf file:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Username = three
Password = three
Modem = /dev/ttyUSB1
Dial Command = ATDT
Baud = 9600

[Dialer three]
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
Init5 = AT+CGDCONT=1,"IP","3internet"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800

---

### Post by mali2297 on 2009-11-19
After adding the *[Dialer three]...* part to /etc/wvdial.conf, try starting wvdial with the command
```

sudo -b wvdial three

```

You could also try changing the dial command from *ATDT* to *ATDP* or *ATX3DT*.

---

### Post by judith_sw on 2009-11-19
Still no joy, unfortunately. Output as follows:

judith@judith-laptop:~$ sudo -b wvdial three
[sudo] password for judith: 
judith@judith-laptop:~$ --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ERROR
--> Bad init string.

---

### Post by judith_sw on 2009-11-19
I'm trying the alternative commands now ...

---

### Post by mali2297 on 2009-11-19
Remove the lines
```

Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2

```
and try again.

---

### Post by mali2297 on 2009-11-19
It's past bedtime for me, so I have to go. I hope it works out for you.

---

### Post by judith_sw on 2009-11-19
No luck with the alternative commands. Removing the 2 lines produce:

judith@judith-laptop:~$ sudo -b wvdial
judith@judith-laptop:~$ --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Thu Nov 19 23:34:09 2009

---

### Post by pdc on 2009-11-19
9.10 seems to have had problems with mobile broadband; some of these seem to be settling as new bug fixes are implemented;

all I can suggest is plugging the modem in; 

type > lsusb

see what your Huawei Vendor ID: product ID are;

now: back to the desktop; if modem has an icon,


**right click** on its icon; select eject

again type > lsusb         has the second number changed for the modem? (this is just out of curiosity .........)

If so, try and connect, if you have network manager configured already for 3

---

### Post by judith_sw on 2009-11-19
Time for me to get some sleep too. Thanks you for all your help! Hopefully I can get this solved soon - I have enjoyed learning about it tonight, even if it is annoying too :-)

---

### Post by judith_sw on 2009-11-20
Hello again,

Still no luck in connecting. My wvdial file is:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = ***99#**
Username = **three**
Password = **three**
Modem = /dev/ttyUSB1
Dial Command = ATDT
Baud = 9600

[Dialer three]
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
Init5 = AT+CGDCONT=1,"IP","3internet"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800

The output for sudo wvdial three is:

judith@judith-laptop:~$ sudo wvdial three
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ERROR
--> Bad init string.
--> Cannot get information for serial port.

[B]Problems seem to be:
"Cannot get information for serial port" and
"Bad init string"
[/B]
Any help very gratefully received. I need some sleep now, but will be online again in the morning.

Incidentally, are there any dongles that work straight out of the box with HP 2133 and Ubuntu 9.10? Easy, straightforward, no issues in UK??? Could be tempted!!!

---

### Post by judith_sw on 2009-11-22
I've given up for now. Please see my more recent post regarding a Huawei K3565 Vodaphone dongle - works a treat thanks to you guys on the forum.

May try to sell the dongle, as it 's no good for me / I don't yet have the expertise / patience to persevere ...

---

### Post by CbrPad on 2009-11-22
This is probably the well known bug 446146.   See [https://bugs.launchpad.net/bugs/446146](https://bugs.launchpad.net/bugs/446146)

Try..

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003   

(the vendor and product id's here are for the huawei e220, you may have to change them to match your device).

---

### Post by judith_sw on 2009-11-22
Hi,

Thanks for all the advice, guys. 

I have actually managed to get the dongle working this afternoon. I'd totally given up on it, and had thought about selling it. I logged onto my home PC, which told me ... no signal / cannot connect. 

But I reinstalled the software and this time it kept telling me "no SIM card". I checked and the SIM card was in the wrong way round! I have no idea how this has happened, as I cannot recall ever having removed it. Mischevious colleagues, maybe, but I had had no problems using it on other computers in the past. But, Ihadn't checked.

Guess what ... it worked, first time, no tweaks, nothing ... I now have 2 working connections for mobile broadband, but I'm not too concerned as the 3 one expires in a month and I've found reception to be patchy (+ Vodaphone offers a 6 month life on download purchase). 

Nevertheless, I have been rather stupid and would like to apologise to all those who have tried to help. I did consider saying nothing, but I'm an honest person. Also, I have learnt so much through these difficulties, that the information I have learnt will be of immense use in the months to come!

Thank you ...  #-o

---

### Post by ^_Pepe_^ on 2009-11-22
Hi Judith,

Please can you confirm that you have a 9.10 Ubuntu version with a Huwaei E156G dongle just...working?

If so, please can you sumarize your steps to reach there?

Very interested here. I have one, and no luck yet.

Regards,

---

### Post by judith_sw on 2009-11-23
Hi Pepe,

Yes, Karmic Koala 9.10 and Huawei E156G dongle. The problem seems to have been entirely of my own making. If you read the rest of this thread, you will see that I abandoned my attempts to install this dongle and went and bought another one (Vodaphone K3565). In the meantime I did a clean install of KK 9.10, as I had played around with a lot of settings. The Vodaphone worked straight from the box - I had to disconnect and reconnect a couple of times and then it worked. I also switched off my home wireless broadband signal until the Vodaphone connection was working properly. The have been fine together since.

When I realised that there was an error with the SIM card in the E156G, I tried again and it worked immediately. I did not need to make any changes, I simply set it up as an additional connection.

If you still have no luck connection, have a look at messages 3, 7, 10, 17 and 22.

I hope this helps ... I think I've been lucky!

Judith

---

