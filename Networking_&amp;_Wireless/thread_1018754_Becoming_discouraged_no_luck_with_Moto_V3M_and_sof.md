---
title: "Becoming discouraged no luck with Moto V3M and softmodem"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by lonewolf454 on 2008-12-22
I was very excited when I read about Ubuntu a few months back and downloaded entire install to a cd.  I have been trying for several months now (off and on, depending on discouragement level) to get connected.  This is on a Gateway MT3707 that came with Vista (probably the reason for me looking to linux-Vista sucks)  I can use the softmodem and an Alltel V3A (moto) with Vista no problem.  I cannot however figure out how to make either work with ubuntu. 

+++++++++++++++++  softmodem is seen by scanModem

NAME="Audio Device:ATI Technologies Inc IXP SB4x0 High Definition Audio Controller "
CLASS=0403
PCIDEV=1002:437b
SUBSYS=107b:0318
IRQ=17
HDA=1002:437b
SOFT=1002:437b.HDA
CHIP=0x11c11040
IDENT=11c11040
Driver=agrmodem+agrserial+patched_snd-hda-intel

I went to linmodems.technion.ac.il and downloaded 20080721.tar.bz2, and followed the brief generic instructions with no luck.  There was also a file of same name but with ALSA15 after name, not sure what is the difference.  It does not dial out.

+++++++++++++++++++  Motorola V3A:

I have set /etc/wvdial.conf as

[Dialer Moto]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 921600
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username =[mobilenumber]@alltel.net
Password = alltel
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier check = no
[Dialer shh]
Init3 = ATM0
[Dialer pulse]
Dial Command = ATDP

ScanModem finds it
Attachemd USB devices are:
ID 22b8:2ac4 Motorola PCS
ID 154b:0005

I also did a lsusb:
Bus 3 Dev 011 (note Dev# changes each time I connect/disconnect the phone)
ID 22b8:2ac4 Motorola PCS

When I do Wvdial from command prompt
-->Cannot open /dev/ttyUSB0 (tried different USB#'s 0-4)

When I ls /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory

I felt very computer savvy going into this, but now not so.  I have been living in a windows world for too long.  If anyone can help with either (or both) I would appreciate.  I am not sure where to look from here, as I have googled everything I could think of.

---

### Post by ieee488 on 2008-12-22
separate the printouts for the two devices and clearly identify which is for what; as it is I'm confused what is what.

---

### Post by lonewolf454 on 2008-12-22
Attached is my ModemData.txt

---

### Post by ieee488 on 2008-12-22
remove one or the other modem and re-run ScanModem

that makes life easier for everyone

---

### Post by lonewolf454 on 2008-12-22
I have tried both of these separately, to no avail,but here is just with the softmodem attached (internally)

I tried to list everything someone might need to help so I wouldn't fill up the forum thread asking me to list this and that and making it appear as though I had receieved information on how to resolve problem.

---

### Post by lonewolf454 on 2008-12-24
Wow what a difference working around the clock makes.  I have tried for some time o get the ISP dialup connection working, with no luck.  I have though made progress and actually am connected at present on the RAZR v3a modem.  It was disconnecting after 2.5 minutes at first, but fixed that now.  HOWEVER... Airtime costs money before 9 PM, so still needing to get the 11c agere softmodem working.  I have made some progress, but it disconnects after about a minute and I cant browse.

I will post later how I setup the Alltl V3A to work as USB modem once I get all the bugs worked out.(like not having to sudo wvdialconf (if possible) every time I turn on computer and get network connections dialer to work  It does seem faster on Ubuntu/Linux than Winblows.  

I am obviously a newbie to linux but now excited again!

---

