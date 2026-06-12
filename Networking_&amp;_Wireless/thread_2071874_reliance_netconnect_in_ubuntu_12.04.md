---
title: "reliance netconnect in ubuntu 12.04"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by autobot3688 on 2012-10-16
Hi, I am finally able to connect my usb reliance net connect modem in ubuntu. I had to follow several procedures to  make it work throug wvdial. Iam sharing my experience hoping this might help some one.

The following are the steps

we need to install wvdial.
the following debian packages should be installed.
(i)libwvstreamsbase,libssl,extras,uniconf,wvstreams

(ii)edit /etc/usbmode_switch as following

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# Evaluated by the wrapper script /usr/sbin/usb_modeswitch_dispatcher
#
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=1


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" and probably others

EnableLogging=1

#reliance modem
DefaultVendor= 0x15eb
DefaultProduct=0x1231
TargetVendor= 0x15eb
TargetProduct=1231
CheckSuccess=5

(iii)edit /etc/wvdial.conf as following



[Dialer Defaults]
Newppd = Yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

ISDN = 0
Modem Type = Analog Modem
SetVolume = 0
Phone = #777
Modem = /dev/ttyACM0
Username = 9391829563
Dial Command = ATDT
Password = 9391829563
Baud = 460800
Stupid Mode = 1
Auto DNS = 1
Check Default Route = 1

now u can connect to internet using wvdial now add gnomeppp and its dependent packages later do the following.
(i)groupadd dialout
   gpasswd -a <username> dialout
now logout and login
(ii)chgrp dialout /usr/bin/wvdial
    chmod u+s,o= /usr/bin/wvdial
(iii)ls -l /usr/bin/wvdial
u will see permissions as
-rwsr-x--- 1 root dialout 114368 2005-12-07 19:21 /usr/bin/wvdial
 now u can use gnomeppp to connect to internet

---

### Post by ejoftiduttu on 2012-12-23
When i tried to connect my reliance netconnect on ubuntu 12.04 i'm getting a msg likethis

ejofti@ejofti-ThinkPad-E420:~$ sudo wvdial netconnect
--> WvDial: Internet dialer version 1.61
--> Warning: section [Dialer netconnect] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Anyone plz help me solve this..

---

