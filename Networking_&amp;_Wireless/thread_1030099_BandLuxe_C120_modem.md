---
title: "BandLuxe C120 modem"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by ravindasenarath on 2009-01-04
i use ubuntu 8.10 . i have a bandLuxe C120 usb modem. i couldnt amke it work with ubuntu. when i try this command

**sudo wvdialconf /etc/wvdial.conf**

it says no modem wad detected but for **dmesg** command it display 
GSM Modem now attached to ttyusb0

can some one help me to make this modem get work with ubuntu.

---

### Post by ieee488 on 2009-01-04
searching on Google 
[http://marvinrebooted.wordpress.com/index/bandluxe-gsm-modem-with-ubuntu/](http://marvinrebooted.wordpress.com/index/bandluxe-gsm-modem-with-ubuntu/)
see if that works

---

### Post by sreeyeshns on 2009-01-04
Try installing gnome-ppp, which will provide you an easy GUI interface to configure your usb modem.

It's really working. I have successfully established a dialup connection using this tool.

Use the following command to install gnome-ppp if you have another Internet connection or download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)(I think there will be no dependency problem)

command:
sudo apt-get install gnome-ppp

If necessary I will mail you the package. OK?

---

### Post by ravindasenarath on 2009-01-06
i tried gnome-ppp it doesnt work. problem is the modem doesnt configured by ubuntu as i see.when i try followng command
[B]
sudo wvdialconf /etc/wvdial.conf[/B]

it says no modem was detected:confused::confused:

---

### Post by ravindasenarath on 2009-01-29
i solve this problem. just a firmware update needed .
thankx for every one try to help me

---

### Post by &#1601;&#1575;&#1610;&#1585;&#1608;&#1587; on 2009-03-08
> **ravindasenarath said:**
> i solve this problem. just a firmware update needed .
thankx for every one try to help me

how we  can update the firmware ??????????

---

### Post by acho on 2009-03-13
help me...!!! ](*,) :(

my console
-----------------------------------------------------------
hanif@achosoft:~$ **sudo wvdialconf /etc/wvdial.conf** 
[sudo] password for hanif: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
------------------------------------------------------------
and then I try this

------------------------------------------------------------
sudo gedit /etc/wvdial.conf
------------------------------------------------------------

try to put this :

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = at+cgdcont=1,"ip","YOUR.ISP.NAME"
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = (usually blank, or ISP name again)
Username =

then I try this 
--------------------------------------------------------
hanif@achosoft:~/bandluxe-eeepc$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--------------------------------------------------------

why can not detect device modem????


thank's for your help bro....

---

### Post by babarhaq on 2009-04-14
In my case I have to eject it before wvdial can detect the modem at /dev/ttyUSB0

---

### Post by ddreamer on 2010-08-19
Hi, all:
    I have worked it out on Ubuntu 10.04 using NetworkManager without firmware upgrade. There is no need of "eject" either. According to others, this method worked as well in 9.04, 9.10. Please refer to [http://swiss.ubuntuforums.org/showthread.php?p=9739114&highlight=bandluxe+c120#post9739114](http://swiss.ubuntuforums.org/showthread.php?p=9739114&highlight=bandluxe+c120#post9739114)

---

