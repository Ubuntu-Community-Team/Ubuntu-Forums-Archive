---
title: "ubuntu10.4/android2.2/Huawei Ideos usb"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by Marcellodusini on 2011-01-12
**Target**: installing/debugging an android application on a real device

This is my configuration:
**ubuntu10.4/android2.2/Huawei Ideos**
I wanto to get the adb tool to see my cell.
-----------------------------------------------------------------------------
If I type** lsusb** I see the Huawei recognized at the usb: OK
I followed the instructions of the android.com: OK

I do not succeed in having the phone listed by command
**adb devices**

Thank you everybody for comments.

More info:
In*** .bashrc*** I put
[I][FONT=Courier New]export PATH=${PATH}:~/WORK/android-sdk-linux_x86/platform-tools
export PATH=${PATH}:/home/mars/WORK/android-sdk-linux_x86/tools[/FONT]
[/I]
in *** /etc/udev/rules.d/***
I have  ***70-android.rules***
whose contents is
[FONT=Courier New][I]SUBSYSTEM="usb", SYSFS{idVendor}=="12d1", MODE="0666"
[/I]
[FONT=Arial]This is what I see in my terminal window:[/FONT]
mars@mars-desktop:~$ adb devices
List of devices attached 
????????????    no permissions[/FONT]

---

### Post by Marcellodusini on 2011-01-12
Hello,
 I reply to myself since I found the solution and I like to share it with all of you:
The guidelines of the android.com did not taylor my case, in fact;

**[SIZE=6]Starting point:[/SIZE]**
**ubuntu10.4/android2.2/Huawei Ideos**
with all the android tools well installed and working.
+
In*** .bashrc*** I put
[I][FONT=Courier New]export PATH=${PATH}:~/WORK/android-sdk-linux_x86/platform-tools
export PATH=${PATH}:[/FONT][/I]*[FONT=Courier New]~[/FONT]**[FONT=Courier New]/WORK/android-sdk-linux_x86/tools[/FONT]*
+
if I type
[FONT=Courier New]lsusb [/FONT]
I get
[FONT=Courier New]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 12d1:1038 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
+
if I type
[FONT=Courier New]adb devices[/FONT]
I get
[FONT=Courier New]List of devices attached 
????????????    no permissions[/FONT]

**[SIZE=5]Solution[/SIZE]**

[LIST=1]
[*]Open a terminal
[*][FONT=Courier New]cd /etc/udev/rules.d[/FONT]
[*][FONT=Courier New]sudo touch 50-android.rules[/FONT]
[*][FONT=Courier New]sudo gedit 50-andorid.rules[/FONT]
now write into the file the following line:
SUBSYSTEMS=="usb", ATTRS{idVendor}=="12d1", MODE:="0666
[*]Save & close
[*]reboot or type the following:
sudo udevadm control --reload-rules
[*][FONT=Courier New]adb devices[/FONT]
[*]responds in this way now
[FONT=Courier New]List of devices attached 
5C4CA98649CE    device
[SIZE=1]*[FONT=Arial][WHISPERING: GREAT!!][/FONT]*[/SIZE]
[/FONT]
[*]If I type
[FONT=Courier New]usb-devices[/FONT]
I get 6 USB ports, and one of them reports:
[FONT=Courier New]T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1038 Rev=02.26
S:  Manufacturer=Huawei Incorporated
S:  Product=Ideos
S:  SerialNumber=5C4CA98649CE
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=42 Prot=01 Driver=usbfs[/FONT]
[/LIST]
I hope this helps.
Mars

[FONT=Arial Black][SIZE=5]References:[/SIZE][/FONT]
Italian web-page:
[http://www.androidworld.it/forum/app-inventor-91/%5Bguida%5D-vodafone-ideos-ubuntu-10-04-a-8394/](http://www.androidworld.it/forum/app-inventor-91/%5Bguida%5D-vodafone-ideos-ubuntu-10-04-a-8394/)
which refers to this:
[http://androidboss.com/using-android-debug-bridge-adb-in-linux/](http://androidboss.com/using-android-debug-bridge-adb-in-linux/)
which refer to these:
[http://www.2linessoftware.com/2009/01/31/getting-android-sdk-to-work-with-fedora-10/](http://www.2linessoftware.com/2009/01/31/getting-android-sdk-to-work-with-fedora-10/)
[http://forum.xda-developers.com/showthread.php?t=561270](http://forum.xda-developers.com/showthread.php?t=561270)
[http://www.manvstech.com/2009/12/06/android-sdk-i386-on-64-bit-system-cannot-open-shared-object-file-issue/](http://www.manvstech.com/2009/12/06/android-sdk-i386-on-64-bit-system-cannot-open-shared-object-file-issue/)
[http://androidforums.com/support/3534-problems-mounting-communicating-g1-ubuntu.html](http://androidforums.com/support/3534-problems-mounting-communicating-g1-ubuntu.html)
[http://www.mail-archive.com/android-discuss@googlegroups.com/msg14523.html](http://www.mail-archive.com/android-discuss@googlegroups.com/msg14523.html)

---

### Post by balta on 2011-01-18
really glad it worked for you :D

---

### Post by raffaele181188 on 2011-02-20
Thanks, it works now :D
Maybe someone should suggest Android's doc maintainers to update their udev rules

---

### Post by mzijlstra on 2011-03-21
Thanks :D  

I saw: [http://developer.android.com/guide/developing/device.html#setting-up](http://developer.android.com/guide/developing/device.html#setting-up) 

But i didn't realize that the Huawei vendorId (12d1) value should have replaced the 0bb4 that was shown as part of SYSFS{idVendor}=="0bb4"  (although it looks extremely obvious now that I know).

---

