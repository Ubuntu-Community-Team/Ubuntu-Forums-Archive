---
title: "ubuntu Jaunty, wireless broadband ZTE MF633BP+ usb modem - can't set it up"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by seriousproblems on 2009-09-03
Can anyone please tell me in a simple way to set up this modem? I have just purchased a Telstra wireless broadband modem but it only works on Windows and Mac. I searched for days for ubuntu stuff, and it doesn't work. 
I've tried everything suggested by [http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-b](http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-b)
to no avail. And also tried usb mode switch but cant get that working too. Jaunty recognises the modem but as soon as I click on it, the icon goes away and does not detect anymore. Anyone have similar problms? Or anyone who has got this modem working please help! Thankyou!

---

### Post by steve888 on 2009-10-31
> **seriousproblems said:**
> Can anyone please tell me in a simple way to set up this modem? I have just purchased a Telstra wireless broadband modem but it only works on Windows and Mac. I searched for days for ubuntu stuff, and it doesn't work. 
I've tried everything suggested by [http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-b](http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-b)
to no avail. And also tried usb mode switch but cant get that working too. Jaunty recognises the modem but as soon as I click on it, the icon goes away and does not detect anymore. Anyone have similar problms? Or anyone who has got this modem working please help! Thankyou!

hi, same here.

Unable to get Telstra's MF633BP+ working with Ubuntu (9.10), or previous versions.

---

### Post by pdc on 2009-10-31
hi steve888 and (two months ago, seriousproblems):

seems this must act like many usb modems: it has windows software loaded; 

and when you plug it into linux, it sees it as a CD-rom;

and if you ask the modem to identify itself; (by typing in a terminal)

> lsusb you will get one vendor ID: product ID number

and if you successfully "flip" the device to be a USB modem and you again type 

> lsusb

you will now see the same vendor ID but a different product ID

and if you type 

> dmesg after a successful flip, 

you should see refereences to tty0 and tty1 etc

so if you firstly tell us what 

> lsusb says   and what 

> dmesgsays with the modem plugged in;

_________

THere seemed initially one piece of software to "flip" such a device from being seen as CD-ROM to being recognised as a USB modem;

that was usb_modeswitch from draigberghof

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

on this posting from their forum 

[http://draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=215&sid=5347d076faa5f8cc48f6d907016bbfde](http://draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=215&sid=5347d076faa5f8cc48f6d907016bbfde)

you can see someone using the usb_modeswitch to flip the device;

(so it sounds like the flip works ...........)

______________

the other piece of software that has become available is called ozerocdoff

[http://www.pharscape.org/](http://www.pharscape.org/)

but it seems more for specified devices that they name;

________________________

let us know what your lsusb and dmesg say:

seems likely you will need to download usb_modeswitch; 

and install it but tell us lsusb and dmesg first ...

---

### Post by steve888 on 2009-11-01
Hi pdc,

I went off and got it working! (and just came back to post how I did it, and saw your suggestions - thank you).

What I did was to change to OpenSUSE as the Ubuntu 9.10 NetworkManager kept crashing, and it was declared a bug ("insufficient privileges"), so rather than wait for a fix loaded OpenSuse 11.2 RC2 with the new KDE - very nice.

installed usb_modeswitch, etc.

Set up wvdial.conf as follows - being a novice, I'm not sure about some of the following, but it works (for me)!

[Dialer Defaults]
Modem = /dev/ttyUSB2
Baud = 460800
New PPPD = yes
Stupid Mode = yes
Dial Command = ATD
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+cgdcont=1,"IP","telstra.bigpond"
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = (myname)@bigpond.com
Password = mypassword
CarrierCheck = no
Auto DNS = yes
Check DNS = yes

Setup a file in etc/udev/rules.d/999-zte.rules with this line in it:
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"

Set up usb_modeswitch.conf as follows: (removed comments from the mf626 section and added the ZTE MF633BP+ line):

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF626
#
# Contributor: Joakim Wennergren

ZTE MF633BP+ 
DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"


Hope this helps.

Works fine, although it can be slow to connect. Also, sometimes the NetworkManager popup lists nameservers, other times is blank, but still works.

Will play around with it to see if can speed up connection.

UPdate:

I had to also include a rules file after zte.rules with the command to run modprobe command (with relevant settings).

More details if needed. Generally now connects in 7 to 8 seconds.

---

