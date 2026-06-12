---
title: "UMW190 has no Verizon Entry in Network Mgr Broadband config"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by ktraub on 2010-05-14
Hello All,

I am having trouble getting a Verizon UMW190 configured in Network Manager under 10.04 Lucid as a 'New Mobile Broadband Connection'. As the UMW190 is a 'World' capable mobile Broadband adapter is has both CDMA and GSM capability. I only need CDMA for now.
However, when network manager detects the VZ UMW190, it does not offer Verizon as a choice in the Provider list.
I searched and found references in this forum for using the UMW190 under 9.10 with gnome-ppp via this link:
[http://ubuntuforums.org/showthread.php?t=1405966&highlight=UMW190](http://ubuntuforums.org/showthread.php?t=1405966&highlight=UMW190)
and tried it without any luck.
I have previously used a VZ UM175 on this machine under 10.04 without any issues as Verizon appeared in the Provider list and the configuration worked without a problem.
Any help is greatly appreciated.
-Kev

---

### Post by alexfish on 2010-05-14
hi

you need to detect if the modem has been configured and the ports 

from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

this will give the modem and the ports , from this try each on until you get a connection

if you are met with failer:

can you post the results of the above

and also the results of

Code:

lsusb

regards

alexfish

---

### Post by ktraub on 2010-05-14
Sorry but no luck.

Here's what I get from dmesg & lsusb:

ktraub@opclaptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[ 7891.390964] cdc_acm 1-6:1.0: ttyACM0: USB ACM device
[ 7891.393468] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems a                                                                            nd ISDN adapters
[22067.185383] cdc_acm 1-6:1.0: ttyACM0: USB ACM device
ktraub@opclaptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[ 7891.390964] cdc_acm 1-6:1.0: ttyACM0: USB ACM device
[ 7891.393468] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[22067.185383] cdc_acm 1-6:1.0: ttyACM0: USB ACM device
ktraub@opclaptop:~$ lsusb
Bus 008 Device 005: ID 0a5c:4503 Broadcom Corp.
Bus 008 Device 004: ID 0a5c:4502 Broadcom Corp.
Bus 008 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 008 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 106c:3716 Curitel Communications, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Help please.
Thanks,
-Kev

---

### Post by alexfish on 2010-05-14
hi

no sure what is up with the modem

looking at your outputs

[ 7891.390964] [COLOR=Blue]cdc_acm 1-6:1.0: ttyACM0: USB ACM device[/COLOR]
[  7891.393468] cdc_acm: v0.26:USB Abstract Control Model driver for USB  modems and ISDN adapters
[22067.185383][COLOR=Blue] cdc_acm 1-6:1.0: ttyACM0: USB  ACM device[/COLOR]


as from the device in the thread link shows

[13992.007142] [COLOR=Blue]cdc_acm 2-2:1.0: ttyACM0: USB ACM device[/COLOR]
[13992.009585]  cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and  ISDN adapters
[16192.714060][COLOR=Blue] cdc_acm 2-2:1.0: ttyACM1: USB ACM device[/COLOR]

you only have one port registered , this could possibly mean the control port or the communication port is down , or maybe looking at a bug

there are a coupe of options , possibility the device may have to be configured in windows , also worth checking it works with windows , if it fails there then I could presume there is a fault with the device , in that case there is only one option

 lets us know the outcome

regards

alexfish

---

### Post by ktraub on 2010-05-14
I have already configured the UMW190 in Windows and it works fine. I also used the Verizon Access manager in Windows to disable the on-board storage.

---

### Post by alexfish on 2010-05-14
hi

I am digging in the dark now

what happens if you re enable the on board storage
then try following what they did in the thread you mentioned

regards

alexfish

---

### Post by ktraub on 2010-06-10
OK, I finally got this working by making a change to the PPP Settings for this Mobile Broadband connection with the UMW190 on Verizon.
Under the Mobile Broadband tab, just fill in:
Number: #777
Username: (yournumber)@vzw3g.com
Password: vzw

and then If you edit the connection and go into PPP Settings
---> Authentication
  ----> Configure Methods
    ----> and click ONLY PAP, CHAP, MSCHAPv2

and under PPP Setting Compression
only check 'Allow BSD data compression' and
           'Allow Deflate data compression'
and un-check all the other Compression methods.
as in the attached to screenshots, it works!):P
-Kev

---

### Post by 1ightbu1b on 2010-06-23
ktraub,
   I tried your recommendation to no avail. I still cannot get connected. Will continue to search for solution and would appreciate any help. Thanks in advance.

---

### Post by ktraub on 2010-06-23
1ightbulb,

Sorry, but my previous solution turned out to be unreliable.

I have since gotten this solution to work consistently: 
[http://www.linux.com/archive/feature/52729](http://www.linux.com/archive/feature/52729)

It is a little clunky, but it does work.
-Kev

---

### Post by ktraub on 2010-06-23
Also, this GUI solution works:
[http://ubuntuforums.org/showpost.php?p=8996651&postcount=2](http://ubuntuforums.org/showpost.php?p=8996651&postcount=2)

but the trick is you MUST run gnome-ppp with gksu as:
gksu gnome-ppp
otherwise it will fail as it doesn't have sufficient rights to run gnome-ppp.

One other thing, it takes a loooonnnngggg time to connect, as much as 30 seconds before it actually comes back with an IP address so BE PATIENT!

Hope that helps.
-Kev

---

### Post by alexfish on 2010-06-23
Hi 
for permissions , check to see if you are a member of the dialout and dip

Code:

[SIZE=2][COLOR=#000000][FONT=Times New Roman][LEFT]id[/LEFT]
[/FONT][/COLOR][/SIZE]
if you are not a member of both groups

goto system/administration

manage groups and check the boxes for

dialout and dip

or from the terminal

sudo adduser YOURUSERNAME dip
sudo adduser YOURUSERNAME dialout

regards
alexfish

---

### Post by 1ightbu1b on 2010-06-23
Thanks  so much. That  was the solution.

---

