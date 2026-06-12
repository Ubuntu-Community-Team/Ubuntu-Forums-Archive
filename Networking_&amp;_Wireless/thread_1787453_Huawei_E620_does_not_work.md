---
title: "Huawei E620 does not work"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by kinu on 2011-06-21
Hi,

Network manager is unable to "see" this modem.

In the first form of the assistant to define a mobile connection, I can't select any device to use. If I complete the wizard, I got a connection listed, but I cannot access it.

With lsubs I got

```
Bus 004 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```

I'm using Ubuntu 11.04.

Thank you in advance.

---

### Post by nomko on 2011-06-21
A search on this must give you enough information:
 
[http://ubuntuforums.org/showthread.php?t=1653728&highlight=Huawei+E620](http://ubuntuforums.org/showthread.php?t=1653728&highlight=Huawei+E620)
 
[http://ubuntuforums.org/showthread.php?t=1454283&highlight=Huawei+E620](http://ubuntuforums.org/showthread.php?t=1454283&highlight=Huawei+E620)
 
[http://ubuntuforums.org/showthread.php?t=1358615&highlight=Huawei+E620](http://ubuntuforums.org/showthread.php?t=1358615&highlight=Huawei+E620)
 
[http://ubuntuforums.org/showthread.php?t=1268141&highlight=Huawei+E620](http://ubuntuforums.org/showthread.php?t=1268141&highlight=Huawei+E620)
 
All topics related to Huawei:
[http://ubuntuforums.org/search.php?searchid=81634485&pp=25](http://ubuntuforums.org/search.php?searchid=81634485&pp=25)
 
 
For the next time, please perform a search on this forum to find related topics about the Huawei modem, just a hint.

---

### Post by kinu on 2011-06-21
Hi nomko,

I read all the old posts before posting, but the only solution is for ubuntu 9.04, and involved old (then beta) packages.

I have no found any reference or solution to this problem in Natty.

That is why I post.

Or maybe I have to downgrade usb-modeswitch and usb-modeswitch-data, or networkmanager ? 

Thank you in advance.

---

### Post by nomko on 2011-06-21
> **kinu said:**
> Hi nomko,
 
I read all the old posts before posting, but the only solution is for ubuntu 9.04, and involved old (then beta) packages.
 
Whats the name of those packages? You could search for it to find new files. Normally, most beta files will eventually become final.

---

### Post by kinu on 2011-06-21
Hi nomko,

I've been searching in bugs database and have found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/772577]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/772577")

I think I have same issue because I can see the modem using lusb but network manager is unable to recognize the modem.

They sat that it works in 10.10, but not it 11.04.

Thank you for trying to help.

kinu.

---

### Post by alexfish on 2011-06-21
hi Kinu

can post the results of usb-devices from the terminal
```
usb-devices
```locate the line which indicate the device and post only those lines.
also results of
```
ls -al /dev/serial/by-id
```
and
```
uname -a
```
need to know if system is lap top or dektop , if laptop please state which model and if dual booting with windows or from wubi install.

can also suggest downloading sakis3g from
**[*Sakis3G* - All-in-one script]("http://www.sakis3g.org/")**

regards

alexfish

---

### Post by kinu on 2011-06-22
Hi alexfish,

```
$ usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0002 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-8-generic ehci_hcd 
S:  Product=EHCI Host Controller 
S:  SerialNumber=0000:00:1d.7 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.0 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.1 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.2 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.3 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
```

```
$ ls -al /dev/serial/by-id 
ls: no se puede acceder a /dev/serial/by-id: No existe el fichero o el directorio (cannot access /dev/serial/by-id: Inexistent file or directory)
```

```

$ uname -a 
Linux my-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux 
```

It's a laptop, Fujitsu fujitsu Amilo pi1505.

I will try the script tonight.

Thank you.

---

### Post by kinu on 2011-06-22
Hi again,

I've tried sakis3g. The only two options that work are "Compiling embeded usb-modeswitch" (done) and "switch modem only", that tell me "modem switched to 121d:1001". All the other said "Failed to connect...". and it always fails when "locating tty..."

Any idea?

---

### Post by alexfish on 2011-06-22
from the usb-devices the device is not registering on the system , normally would have expected this, from earlier versions of Ubuntu,I presume the device was connected, if the laptop has two usb ports try swaping the connection , also check the bios settings for usb1 and usb2(the connection port has to be usb2 for linux), if you had previous windows7 or dual booting , does any notification show up in windows as  which may indicate a bios setting error, or bus config error.

think the device ID should be 1001 , but not sure , if that been the case this device should have been recognised by the kernel, and should not require usb_modeswitch , also it usb_modeswitch should be installed at default, and the only requirement would be to update the usb_modeswitch.d files(the data set), do not recompile a new version of usb_modeswitch, it may produce errors.

can try running sakis3g from the terminal in debug mode, I am curious to to see what it shows
```
sakis3g -debug
```post any relevant info
also can post the results of the lsusb command 
```
lsusb
```can confirm as requested if dual booting Ubuntu and windows or have installed with wubi , or is Ubuntu the only OS, or possibley running from VMware like virtual box

added:: also re do the usb-devices command after running sakis3g

alexfish

---

### Post by kinu on 2011-06-23
Hi,

Changing usb port, as you suggested, changed the results of the commands

usb-devices:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

ls -al /dev/serial/by-id: file or directory inexistent

lsusb:

```
Bus 002 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```

sakis3g -debug: Connect 3G command, (it fails at "Locating tty")

```
-------------------------------------------
Will now proceed with Sakis3G execution.
-------------------------------------------
[02372] [10:15:50] Located "echo" within PATH (/bin/echo).
[02372] [10:15:50] Level 1 dependencies met.
[02372] [10:15:50] Dir "/bin" exists in PATH.
[02372] [10:15:50] Dir "/usr/bin" exists in PATH.
[02372] [10:15:50] Dir "/sbin" exists in PATH.
[02372] [10:15:50] Dir "/usr/sbin" exists in PATH.
[02372] [10:15:50] Done setting up PATH.
[02372] [10:15:50] Located "readlink" within PATH (/bin/readlink).
[02372] [10:15:50] My location is "/home/cesar/Escritorio/sakis3g".
[02372] [10:15:50] Located "wc" within PATH (/usr/bin/wc).
[02372] [10:15:50] Located "cat" within PATH (/bin/cat).
[02372] [10:15:50] Located "tail" within PATH (/usr/bin/tail).
[02372] [10:15:50] Located "head" within PATH (/usr/bin/head).
[02372] [10:15:50] Located "sort" within PATH (/usr/bin/sort).
[02372] [10:15:50] Located "uniq" within PATH (/usr/bin/uniq).
[02372] [10:15:50] Located "ls" within PATH (/bin/ls).
[02372] [10:15:50] Located "sed" within PATH (/bin/sed).
[02372] [10:15:50] Located "setsid" within PATH (/usr/bin/setsid).
[02372] [10:15:50] Located "getent" within PATH (/usr/bin/getent).
[02372] [10:15:50] Located "ps" within PATH (/bin/ps).
[02372] [10:15:50] Located "chmod" within PATH (/bin/chmod).
[02372] [10:15:50] Located "chown" within PATH (/bin/chown).
[02372] [10:15:50] Located "touch" within PATH (/usr/bin/touch).
[02372] [10:15:50] Located "expr" within PATH (/usr/bin/expr).
[02372] [10:15:50] Located "seq" within PATH (/usr/bin/seq).
[02372] [10:15:50] Located "cp" within PATH (/bin/cp).
[02372] [10:15:50] Located "rm" within PATH (/bin/rm).
[02372] [10:15:50] Located "who" within PATH (/usr/bin/who).
[02372] [10:15:50] Located "mv" within PATH (/bin/mv).
[02372] [10:15:50] Located "basename" within PATH (/usr/bin/basename).
[02372] [10:15:50] Located "dirname" within PATH (/usr/bin/dirname).
[02372] [10:15:50] Level 2 dependencies met.
[02372] [10:15:50] Basic binaries are resolved.
[02372] [10:15:50] Parent process is: bash
[02372] [10:15:50] Running by user request.
[02372] [10:15:50] Person behind screen is cesar.
[02372] [10:15:51] Configuration file /etc/default/sakis3g does not exist or is not readable.
[02372] [10:15:51] Configuration file /etc/sysconfig/sakis3g does not exist or is not readable.
[02372] [10:15:51] Configuration file /etc/sakis3g.conf does not exist or is not readable.
[02372] [10:15:51] Configuration file(s) loaded.
[02372] [10:15:51] Will attempt to get access to display :0.
[02372] [10:15:51] Located "xauth" within PATH (/usr/bin/xauth).
[02372] [10:15:51] Already granted access to display :0.
[02372] [10:15:51] Will be using display :0.
[02372] [10:15:51] Selecting GUI.
[02372] [10:15:51] Unable to locate "kdialog" within PATH.
[02372] [10:15:51] Located "zenity" within PATH (/usr/bin/zenity).
[02372] [10:15:51] zenity selected as GUI.
[02372] [10:15:51] Locale es_ES.UTF-8 found in environment.
[02372] [10:15:51] Will attempt to get translation file from package: messages/es_ES.UTF-8.
[02372] [10:15:51] Loaded default value for foldwrapping: 60
[02372] [10:15:51] No translations retrieved from file. Will not be using translations.
[02372] [10:15:51] Loaded default value for foldwrapping: 60
[02372] [10:15:51] Not currently running with root privileges.
[02372] [10:15:51] Located "gksu" within PATH (/usr/bin/gksu).
[02372] [10:15:51] Running on a GNOME system.
[02372] [10:15:51] Root level dependencies met.
[02372] [10:15:51] Loading Usb-ModeSwitch device database.
[02372] [10:15:51] Embedded device database loaded.
[02372] [10:15:51] Switchable devices within embedded device database:
0421:0610 0471:1210 0471:1237 0482:024d 04e8:f000 057c:84ff 05c6:1000 05c6:2001 05c6:f000 072f:100d 0930:0d46 0ace:2011 0ace:20ff 0af0:6711 0af0:6731 0af0:6751 0af0:6771 0af0:6791 0af0:6811 0af0:6911 0af0:6951 0af0:6971 0af0:7011 0af0:7031 0af0:7051 0af0:7071 0af0:7111 0af0:7211 0af0:7251 0af0:7271 0af0:7301 0af0:7311 0af0:7361 0af0:7381 0af0:7401 0af0:7501 0af0:7601 0af0:7701 0af0:7801 0af0:7901 0af0:8200 0af0:8201 0af0:8300 0af0:8302 0af0:8304 0af0:8400 0af0:c031 0af0:c100 0af0:d013 0af0:d031 0af0:d033 0af0:d035 0af0:d055 0af0:d057 0af0:d058 0af0:d155 0af0:d157 0af0:d255 0af0:d257 0af0:d357 0b3c:c700 0fce:d0cf 0fce:d0e1 0fce:d103 1004:1000 1004:607f 1004:613a 1004:613f 1033:0035 106c:3b03 106c:3b06 1076:7f40 1199:0fff 1266:1000 12d1:1001 12d1:1003 12d1:101e 12d1:1414 12d1:1446 12d1:1520 12d1:1521 12d1:1557 1410:5010 1410:5020 1410:5030 1410:5031 1410:5041 148f:2578 16d8:6803 16d8:700a 16d8:f000 198f:bccd 19d2:0003 19d2:0026 19d2:0040 19d2:0053 19d2:0083 19d2:0101 19d2:0103 19d2:0115 19d2:1001 19d2:1007 19d2:1009 19d2:2000 19d2:fff5 19d2:fff6 1a8d:1000 1ab7:5700 1b7d:0700 1bbb:f000 1c9e:1001 1c9e:9200 1c9e:f000 1dd6:1000 1e0e:f000 1f28:0021 1fac:0130
[02372] [10:15:51] Switched devices within embedded device database:
0421:0612 0471:1206 0471:1234 04e8:6601 057c:8401 05c6:9000 072f:90cc 0930:0d45 0af0:6600 0af0:6701 0af0:6901 0b3c:c000 0b3c:c001 0b3c:c002 1004:6114 1004:6124 1004:6141 106c:3715 106c:3717 1076:7f00 1199:0017 1199:0018 1199:0019 1199:0020 1199:0021 1199:0022 1199:0024 1199:0026 1199:0027 1199:0028 1199:0029 1199:0112 1199:0120 1199:0218 1199:0220 1199:0224 1199:6802 1199:6803 1199:6804 1199:6805 1199:6808 1199:6809 1199:6812 1199:6813 1199:6815 1199:6816 1199:6820 1199:6821 1199:6822 1199:6832 1199:6833 1199:6834 1199:6835 1199:6838 1199:6839 1199:683a 1199:683b 1199:683c 1199:683d 1199:683e 1199:6850 1199:6851 1199:6852 1199:6853 1199:6855 1199:6856 1199:6859 1199:685a 1266:1002 1266:1003 1266:1004 1266:1005 1266:1006 1266:1007 1266:1008 1266:1009 1266:100a 1266:100b 1266:100c 1266:100d 1266:100e 1266:100f 1266:1011 1266:1012 12d1:1001 12d1:1003 12d1:1406 12d1:140c 12d1:141b 12d1:1464 12d1:1465 12d1:14a5 12d1:14ac 1410:4100 1410:4400 1410:6000 1410:6002 1410:7001 1410:7003 148f:9021 16d5:6502 16d8:6006 16d8:680a 198f:0220 19d2:0001 19d2:0002 19d2:0015 19d2:0016 19d2:0017 19d2:0022 19d2:0031 19d2:0037 19d2:0052 19d2:0055 19d2:0063 19d2:0064 19d2:0094 19d2:0104 19d2:0116 19d2:0124 19d2:0128 19d2:1003 19d2:1008 19d2:1010 19d2:fff1 19d2:ffff 1a8d:1002 1a8d:1009 1ab7:5731 1b7d:0001 1bbb:0000 1c9e:6061 1c9e:9000 1c9e:9063 1c9e:9202 1c9e:9603 1dbc:0005 1dd6:1002 1e0e:9000 1e0e:9200 1e0e:ce16 1e0e:cefe 1f28:0020 1fac:0131 1fe7:0100
[02372] [10:15:51] Embedded Usb-ModeSwitch device database contains 260 entries.
[02372] [10:15:51] Folder "/etc/usb_modeswitch.d" exists. Will check if it contains configuration files.
[02372] [10:15:51] Loading system supplied device database.
[02372] [10:15:51] Switchable devices within system device database:

[02372] [10:15:51] Switched devices within system device database:

[02372] [10:15:51] Finished starting up.
[02372] [10:15:51] No actors defined.
[02372] [10:15:51] Executing default actor for "zenity".
[02372] [10:15:51] Loaded default value for pppint: ppp0
[02372] [10:15:51] Located "ifconfig" within PATH (/sbin/ifconfig).
[02372] [10:15:51] Asking user to select: MENU Please select an action Choose action for Sakis3G script to follow. OK Cancel CONNECT Connect with 3G MOREMENU More options... ABOUT About Sakis3G EXIT Exit
[02372] [10:15:52] Asking user to select: MENU Please select an action Choose action for Sakis3G script to follow. OK Cancel CONNECT Connect with 3G MOREMENU More options... ABOUT About Sakis3G EXIT Exit
[02372] [10:15:52] Variable MENU is not set already.
[02372] [10:15:52] Prompting user to select variable MENU.
[02372] [10:15:52] Located "fold" within PATH (/usr/bin/fold).
[02372] [10:15:58] User selected: "1."
[02372] [10:15:58] Considering selection: 1
[02372] [10:15:58] User selection was 1.
[02372] [10:15:58] Verbosing: 7% Locating device
[02372] [10:15:58] Located "kill" within PATH (/bin/kill).
[02372] [10:15:59] Establishing zenity verbose helper.
/-------------------------------------------------------------------------------
[02372] [10:15:59] Will now run command: \'/usr/bin/touch /tmp/sakis3g.zenity.pipe\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[02372] [10:15:59] Command returned 0.
\-------------------------------------------------------------------------------
/-------------------------------------------------------------------------------
[02372] [10:15:59] Will now run command: \'/bin/chmod 666 /tmp/sakis3g.zenity.pipe\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[02372] [10:15:59] Command returned 0.
\-------------------------------------------------------------------------------
[02372] [10:15:59] PID 3404 is still running.
[02372] [10:15:59] Fetching connected USB devices by using "/sys/bus/usb/devices".
[02372] [10:15:59] Connected USB devices are:
12d1:1001:HUAWEI Mobile
[02372] [10:15:59] Connected USB modems are:
12d1:1001:HUAWEI Mobile
[02372] [10:15:59] Autoselecting unique USB modem plugged: 12d1:1001
[02372] [10:15:59] Setting up modem.
[02372] [10:15:59] Not currently running with root privileges.
[02372] [10:15:59] State variables are: --interactive --debug SGUI="zenity" MODEM="12d1:1001" MENU="CONNECT" DISPLAY=":0" LOCALAUTHORITY="/var/run/gdm/auth-for-cesar-QAXnq9/database"
[02372] [10:15:59] Verbosing: 14% Acquiring root privileges
[02372] [10:15:59] PID 3404 is still running.
[02372] [10:15:59] PID 3404 is still running.
/-------------------------------------------------------------------------------
[02372] [10:15:59] Will now run command: \'/bin/rm -f /tmp/sakis3g.zenity.pipe\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[02372] [10:15:59] Command returned 0.
\-------------------------------------------------------------------------------
[02372] [10:15:59] PID 3404 is still running.
[02372] [10:15:59] PID 3404 is not running any more.
[02372] [10:15:59] This instance will call gksu and abort.
/-------------------------------------------------------------------------------
[02372] [10:15:59] Will now display contents of: \'/tmp/sakis3g.gksu.wrapper.2372\'
/-------------------------------------------------------------------------------
#!/bin/sh
export PROVIDER="./sakis3g"
/home/cesar/Escritorio/sakis3g "-debug" --interactive --debug SGUI="zenity" MODEM="12d1:1001" MENU="CONNECT" DISPLAY=":0" LOCALAUTHORITY="/var/run/gdm/auth-for-cesar-QAXnq9/database"
exit $?

\-------------------------------------------------------------------------------
-rwxr-xr-x 1 cesar cesar 230 2011-06-23 10:15 /tmp/sakis3g.gksu.wrapper.2372
\-------------------------------------------------------------------------------
```

Thank you for your interest.

kinu

---

### Post by alexfish on 2011-06-23
Not sure why the HID driver is loading for this device,the device is showing up as a different class on what should be the  modem port,

can try removing the hid driver from the terminal
```
sudo modprobe -r usbhid
```then load the option driver
```
sudo modprobe option
```see what happens
alexfish

---

### Post by kinu on 2011-06-28
Hi, I'm back here again. This is what I got when issuing these commands:

```
$ sudo modprobe -r usbhid
$ sudo modprobe option
$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
cesar@cesar-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-06-24 10:14 .
drwxr-xr-x 4 root root 80 2011-06-24 10:14 ..
lrwxrwxrwx 1 root root 13 2011-06-24 10:14 usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0 -> ../../ttyUSB0
```

So it's detected! (I think)

But seems that network manager is not able to "see" it.

So one step beyond. What's next?

One again, thank you.

---

### Post by Matbro on 2011-06-29
Hi

Think the result should be more like this:


ls -al /dev/serial/by-id
[I]total 0
drwxr-xr-x 2 root root 160 2011-06-29 10:17 .
drwxr-xr-x 4 root root  80 2011-06-29 10:17 ..
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if04-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if05-port0 -> ../../ttyUSB4
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if06-port0 -> ../../ttyUSB5
[/I]

Have you tried this ?

sudo modprobe usbserial vendor=0x12d1 product=0x1001
ls -al /dev/serial/by-id

what result do you get ?
/Mats

---

### Post by alexfish on 2011-06-29
> **Matbro said:**
> Hi

Think the result should be more like this:


ls -al /dev/serial/by-id
[I]total 0
drwxr-xr-x 2 root root 160 2011-06-29 10:17 .
drwxr-xr-x 4 root root  80 2011-06-29 10:17 ..
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if04-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if05-port0 -> ../../ttyUSB4
lrwxrwxrwx 1 root root  13 2011-06-29 10:17 usb-Huawei_Technologies_HUAWEI_Mobile-if06-port0 -> ../../ttyUSB5
[/I]

Have you tried this ?

sudo modprobe usbserial vendor=0x12d1 product=0x1001
ls -al /dev/serial/by-id

what result do you get ?
/Mats
Hi Matbro

There is a HID driver binding to the modem part of the device, this will have to be removed
```
sudo modprobe -r usbhid
```then do the
```
sudo modprobe usbserial vendor=0x12d1 product=0x1001
```

also note that Attributes for this device does not show as a wlan device
> C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
at present not sure where the info is eminating from, the line should look like
> C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
therefore the option driver  not bind to the device, yet binds to the other parts of the device
so will need to find where this is emanating from , possible usb.id descriptors,but
 not sure.
if have alternate method of connection can try updating the usb-ids
```
sudo /usr/sbin/update-usbids
```

alexfish

---

### Post by kinu on 2011-06-29
Hi alexfish and Matbro,

sudo modprobe usbserial vendor=0x12d1 product=0x1001
ls -al /dev/serial/by-id

```
total 0
drwxr-xr-x 2 root root 80 2011-06-29 13:06 .
drwxr-xr-x 4 root root 80 2011-06-29 13:06 ..
lrwxrwxrwx 1 root root 13 2011-06-29 13:06 usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-06-29 13:06 usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0 -> ../../ttyUSB1 
```

I'm switching from linux to windows to connect the internet, so I cannot execute the update-usbid. I will seek tomorrow for a wifi zone and will try to execute it.

---

### Post by alexfish on 2011-06-29
Hi kino

from  info of usb-devices

I:  [COLOR=Blue]If#= 0 [/COLOR]Alt= 0 #EPs= 3 Cls=03(HID  ) Sub=01 Prot=02 Driver ([COLOR=Navy]EP=3 usually indicates the modem part of the device)[/COLOR]..(Cls=03(HID ) this should be Cls=ff(vend.);;Sub=01 Prot=02 should be Sub=ff Prot=ff).
I:  [COLOR=Green]If#= 1[/COLOR] Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver
I:  [COLOR=Red]If#= 2[/COLOR] Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver

the modem port is on If#= 0.

from the "ls -al /dev/serial/by-id"
lrwxrwxrwx 1 root root 13 2011-06-29 13:06 usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-[COLOR=DarkGreen]if01[/COLOR]-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-06-29 13:06 usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-[COLOR=Red]if02[/COLOR]-port0 -> ../../ttyUSB1

there is no tty* allocate for the modem part of the device
so doubt if any of these drivers will work at present (altough may be detected by modem manager)only the control port may work , see what happens.

the main problem is the att codes and class codes/

so will wait to see what happens if get connected in wifi zone

also try to update the system

if problem still exists the also suggest reporting bugs to
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

alexfish

---

### Post by alexfish on 2011-06-29
here is a script which will give more info than the standard usb-devices,may help with debugging.
save in home directory as "usb-modem"
then call from the terminal
```
tclsh `pwd`/usb-modem
```

```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"
# for device 12d1:1001
    ################################
    # NO PROCS
    #   Set ids and paths
    global exist
    set exist            0
    set Vendor "12d1"
    set Product "1001"
    set Device "$Vendor:$Product"     
    set dir "/sys/bus/usb/devices/"
    puts "Searching Dir $dir"
    set devices [ glob -nocomplain -directory $dir *]
    ###############################
    # check vendor exist infile + check ids
    #-*
    foreach device $devices {
        #puts $device
        set count 0
        set more [ glob -nocomplain -directory $device *]
        #--*
        foreach mdevice $more {
            incr count
            set checkvendor [string first {idVendor} $mdevice]
            #---*
            if {$checkvendor > -1 } {
                set vend [open $mdevice r]
                set idVendor [read $vend]
                set idVendor [string trim $idVendor]
                close $vend
                #----*                                
                if {$idVendor == $Vendor } {
                    set prodpath "$device/idProduct"
                    set prod [open $prodpath r]
                    set idProduct [read $prod]
                    set idProduct [string trim $idProduct]
                    set deviceVend "$idVendor:$idProduct"
                    close $prod
                    #-----*
                    if {$Device == $deviceVend} {
                        set exist             1
                        set wild [string trim $device $dir]
                        set dirs_inf [ glob -nocomplain -directory $dir $wild*]
                        puts "Start Stats"
                        foreach inf $dirs_inf {
                            set dirs_inf [ glob -nocomplain -directory $inf *]
                            foreach infos $dirs_inf {
###################################################################
# File Quirks just incase
                            set avoid 1
                            set subsystem [string first subsystem $infos]
                            set remove [string first remove $infos]
                            set power [string first power $infos]
                            set driver [string first driver $infos]
                            set descriptors [string first descriptors $infos]
                             if {$descriptors > -1} {set avoid 0}
                             if {$driver > -1} {set avoid 0}
                             if {$power > -1 } {set avoid 0}
                             if {$subsystem > -1 } {set avoid 0}
                             if {$remove > -1 } {set avoid 0}
####################################################################
# get the bits
                            
                             if {$avoid} {
                                set isfile [file isdirectory $infos]
                             if {! $isfile } {
                                set devinfo [open $infos r]
                                set a [read $devinfo]
                                set b [split $a "\n"]
                                puts "------- $infos --------"
                            foreach bit $b {puts "  $bit"}
                            close $devinfo}
                            }
                            
##############################################################
                            }
                        }                        
                    }
                }
            }
        }
    }
#-----*
############################################
# if exist then get the bits
############################################
# just get out
if {$exist} {
    puts "DONE"
    } else {
    puts "Device $Device does not exist"
    }
#############################################
```alexfish

---

