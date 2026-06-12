---
title: "could not connect the internet using skytech USB CDMA modem in ubuntu 10.10 (SuperOS)"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by fxlovers on 2010-11-01
please help :sad:....
i can't connect the internet using **[COLOR=#ff0000]Skytech[/COLOR]** CDMA USB modem in my ubunntu 10.10 (Super OS) i follow the instruction in this thread [[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1609880[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1609880")

1. Boot w/ out device,
2. connect the device,
3. open the terminal and type..

GC224PA-UUF:~$ usb-devices
...............
T: Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 2 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=2015 ProdID=0001 Rev=00.00
S: Manufacturer=Qualcomm, Incorporated
S: Product=USB MMC Storage
S: SerialNumber=000000000002
C: #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
-------------------------------------------
GC224PA-UUF:~$ ls -al /dev/serial/by-id/usb*
ls: cannot access /dev/serial/by-id/usb*: No such file or directory

GC224PA-UUF:~$ ls -al /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 2006-02-14 22:18 /dev/disk/by-id/usb-Qualcomm_MMC_Storage_000000000002-0:0 -> ../../sr1

-------------------------------------------
GC224PA-UUF:~$ grep Qualcomm /var/log/syslog
Feb 14 22:18:02 bagoesh-Presario-V3000-GC224PA-UUF kernel: [ 1030.832258] scsi 6:0:0:0: CD-ROM Qualcomm MMC Storage 2.31 PQ: 0 ANSI: 2
-------------------------------------------
GC224PA-UUF:~$ which modem-manager
/usr/sbin/modem-manager
-------------------------------------------
[B]sudo gedit /etc/udev/rules.d/zte_eject.rules
[/B]
[B]SYSFS{idVendor}=="2015", SYSFS{idProduct}=="0001", RUN+=/usr/sbin/eject %k, OPTIONS+="last_rule"
[/B]
reboot....
and the result is nothing :sad:(

i've check what happen and when I type 
GC224PA-UUF:~$ ls -al /dev/disk/by-id/usb 
ls: cannot access /dev/disk/by-id/usb: No such file or directory 
GC224PA-UUF:~$ ls -al /dev/serial/by-id/usb* 
ls: cannot access /dev/serial/by-id/usb*: No such file or directory 

I still can't connect the internet, kindly need help....
:confused:

---

### Post by fxlovers on 2010-11-02
please, help me.. :(

---

### Post by fxlovers on 2010-11-03
i've try many thing but it still unsolved, please help me guy. :confused:

---

### Post by sportscliche on 2010-11-04
There is a GUI program that makes connecting to a USB modem very easy.  I have used it successfully on several laptops running 10.04 and 10.10.  It is quite simple to setup and use:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

### Post by alexfish on 2010-11-07
> **fxlovers said:**
> please, help me.. :(

Hi 

you mentioned in a PM the device works in 9.10 but 10.10

the thing of note in 10.10 usb_modeswitch is installed at default

so need to know if usb_modeswitch is installed on 9.10

also could you do this:

from both operating systems :

boot up without the device.

open up a terminal and enter the following code.

Code:

lshal -m

this will monitor hald

connect the device.

follow the procedure to get the devices recognized (the os which works)

also post details of the commands you sending

also post details of 

Code:

  grep Qualcomm /var/log/syslog

ADDED can you have a look in this file on both systems see if any differences
usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
one way to influence the mode_switch is to edit the usb_modeswitch.conf

can be access and edited with this command.

sudo gedit /etc/usb_modeswitch.conf

the file should show
# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0

to disable set the line 

DisableSwitching=0

to 
DisableSwitching=true

if this has no effect then just reverse the changes

POST DETAILS OF all  outputs denoting which is relevant to each OS

alexfish

---

### Post by sarmad54 on 2011-03-04
> **sportscliche said:**
> There is a GUI program that makes connecting to a USB modem very easy.  I have used it successfully on several laptops running 10.04 and 10.10.  It is quite simple to setup and use:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

Hello , I have tried the program but I am getting the error message 
Unable to locate a configuration file for switching device 05c6:1000

I have a Qualcomm usb modem as detected by lsusb command and I ran the program through the Terminal interface

I would be so grateful if you would be able to help me

---

### Post by sportscliche on 2011-03-04
Can you confirm the program was installed correctly?  Did you follow the procedures for Ubuntu shown here?

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation)

---

### Post by sportscliche on 2011-03-04
This thread my also help:

[http://ubuntuforums.org/showthread.php?t=1531259](http://ubuntuforums.org/showthread.php?t=1531259)

---

### Post by Danxo on 2012-01-11
Its much better to use ppp dialer to connect, the broadband has so may issues and fails at times. if you are on debian, Try the following.
open the terminal 
type the following command
sudo apt-get install gnome-ppp
For more details contact \
Danson on:
[email]danmwaka@yahoo.com[/email] 
+254722952805
 Thank you

---

