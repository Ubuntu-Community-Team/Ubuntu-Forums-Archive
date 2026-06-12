---
title: "Mobile Broadband problem"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by andrei90 on 2010-08-29
Hello.
I`m experiencing problems with my Vodafone Mobile Broadband&#8482; connection. The connection wont be established,altough I passed the connection wizard in Broadband,it still doesnt work. What could be the problem,the stick shows me that it has connection. Note that I have an HSPA Usb stick , Model : K3765 , if this could help you on resolving my problem.
What should I do ? Help me please.
Thank you.

---

### Post by alexfish on 2010-08-29
hi

can you have a look through here

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 
Post # 1 ref Network Manager failing to connect


also look at alternate dial up method  / suggest Sakis3g

alexfish

---

### Post by AlexDudko on 2010-08-29
Are there any errors while connecting?

---

### Post by andrei90 on 2010-08-29
> **AlexDudko said:**
> Are there any errors while connecting?

No errors,because it's not even connecting.

---

### Post by AlexDudko on 2010-08-29
Look for errors in log files. You can find some information in **/var/log/messages** or you can use a GUI **Log File Viewer**.
See what errors appear there while you are trying to establish the connection.

---

### Post by andrei90 on 2010-08-30
> **alexfish said:**
> hi

can you have a look through here

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 
Post # 1 ref Network Manager failing to connect


also look at alternate dial up method  / suggest Sakis3g

alexfish

I did what u told me with the nm-connection-editor and look what's it saying :
```

** (nm-connection-editor:8143): WARNING **: Tried to get deprecated property gsm/puk
** (nm-connection-editor:8143): WARNING **: Invalid setting Mobile Broadband: network-id
```but the connection screen opens tho...but it doesnt work.

---

### Post by alexfish on 2010-08-30
hi

do you have a pin code

if so enter the pin code

also need more info if the connection fails , read back through the How to

it shows you how to retrieve the information

IE: the bit .[FONT=Verdana][SIZE=2][B]you may be able to find your  service providers APN from the terminals ,connect the modem

[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]this may give a list of the  providers on the device:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]example response from the first  terminal[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
+CGDCONT:  1,"IP","","0.0.0.0",0,0
+CGDCONT:  2,"IP","payandgo.o2.co.uk","0.0.0.0",0,0
+CGDCONT:  3,"IP","m-bb.o2.co.uk","0.0.0.0",0,0[/SIZE][/FONT][FONT=Verdana][SIZE=2]

if it produces a list can you post them back here[/SIZE][/FONT] 

also post details of the APN in the network manager

also did you try sakis3g 

alexfish

---

### Post by andrei90 on 2010-08-31
I put the pin code before and its the same thing , now look what it says :

```
** (nm-connection-editor:2013): WARNING **: Invalid connection (empty)

** (nm-connection-editor:2013): WARNING **: <WARN>  nma_gconf_connection_new(): No connection read from GConf at /system/networking/connections/1.
```

---

### Post by andrei90 on 2010-08-31
I just called the Vodafone Operator and it told me that Vodafone Mobile Broadband doesnt support Linux and it told me to download the drivers to make it work and change the connection to Dial Up ...

---

### Post by alexfish on 2010-08-31
hi

If you don't provide the Info I have requested then I can't help

why are you still trying Network Manager ,what details have you entered in the network manager , 

THE CORRECT APN IS IMPORTANT 

if the device is recognised on the system then if the correct info is entered then it should work 

from what your operator is saying Just does not make sense , which drivers do you need to down load

---

### Post by andrei90 on 2010-08-31
Here's the info you requested :

My broadband **PIN Code** is the default one **1234**

```
andrei@ubuntu:~$ tr -s "\n" < /dev/ttyUSB2
bash: /dev/ttyUSB2: No such file or directory
``` this is what's it saying when I type that...

My **APN **:[COLOR=Blue]_ i**nternet.vodafone.ro**_[/COLOR]

What is sakis3g ?

---

### Post by alexfish on 2010-08-31
hi

we will go through this stage by stage

boot up the computer first, then connect the dongle

from the terminal enter this command

[FONT=Verdana][SIZE=2]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue]dmesg | grep -e "modem" -e "tty"

[COLOR=Black]post the result , then may be see what is going wrong


[/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by andrei90 on 2010-08-31
> **alexfish said:**
> 
[FONT=Verdana][SIZE=2]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue]dmesg | grep -e "modem" -e "tty"
[/COLOR][/SIZE][/FONT]

The result :

[        0.000000]console [[COLOR=Magenta]tty[/COLOR]0]enabled

Also when I do 
[FONT=Verdana][SIZE=2]tr -s "\n" < [/SIZE][/FONT][FONT=Verdana][SIZE=2]/dev/tty[COLOR=Blue]**USB2**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]it says:
-bash: [/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]/dev/tty[COLOR=Blue]**USB2 **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]No such file or directory
[/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by alexfish on 2010-09-01
hi Andrei

in the **how to** it says if the output does not look like then use this command: since no port have registered
it will not respond ; probably needs to be modeswitched


[LIST]
[*][FONT=Verdana][SIZE=2]For USB Devices ;If nothing  shows enter this command from the terminal[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Code :**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

lsusb

this  will give the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ID's**[/SIZE][/FONT][FONT=Verdana][SIZE=2] of the device


can you post the results of the lsusb command


alexfish

[/SIZE][/FONT]

---

### Post by PaulReaver on 2010-09-01
guys? you trying to confuse the man?



_if your on ubuntu lucid_


make sure your connected to the internet by cable, wifi, etc
then
copy and paste this into a terminal

sh -c 'wget [http://www.betavine.net/repository/bcm_lucid_install.sh](http://www.betavine.net/repository/bcm_lucid_install.sh) -O /tmp/bcm.sh && /usr/bin/xterm -e sudo sh /tmp/bcm.sh'


this'll install vodafone's betavine connection manager, 

you can check your balance and data usage,top-up, and send text messages. :)

it even works with some non vodafone huawei dongles,
its open source, I think the community should pinch (i mean help) the project ;) 


[http://www.betavine.net/bvportal/resources/datacards]("http://www.betavine.net/bvportal/resources/datacards")

---

### Post by andrei90 on 2010-09-01
> **alexfish said:**
> 
[FONT=Verdana][SIZE=2]**Code :**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

lsusb

this  will give the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ID's**[/SIZE][/FONT][FONT=Verdana][SIZE=2] of the device


can you post the results of the lsusb command


alexfish

[/SIZE][/FONT]

[B]Results :

[/B]andrei@ubuntu:~$ lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 002: ID 04d9:a01d Holtek Semiconductor, Inc. 

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 003: ID 064e:a103 Suyin Corp. 

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



So I have to modeswitch ? :(

[quote=PaulReaver]

guys? you trying to confuse the man?



_if your on ubuntu lucid_


make sure your connected to the internet by cable, wifi, etc
then
copy and paste this into a terminal

sh -c 'wget [http://www.betavine.net/repository/bcm_lucid_install.sh](http://www.betavine.net/repository/bcm_lucid_install.sh) -O /tmp/bcm.sh && /usr/bin/xterm -e sudo sh /tmp/bcm.sh'


this'll install vodafone's betavine connection manager, 

you can check your balance and data usage,top-up, and send text messages. :smile:

it even works with some non vodafone huawei dongles,
its open source, I think the community should pinch (i mean help) the project :wink: 
[/quote]

I will try this as soon as my cable internet is working,its currently down...I`m running on windows 7 with mobile broadband now.

---

### Post by alexfish on 2010-09-01
hi Andre 

I would advise not to install any software at present

OK

from the outputs there does not appear to be a device showing on the system 
or at least nothing which relates to a HSPA Usb stick , Model : K3765

so I need some help . below shows two devices connected  

[COLOR=Blue]Bus 002 Device 003: ID 064e:a103 Suyin Corp.
Bus 005 Device 002: ID 04d9:a01d Holtek Semiconductor, Inc.[/COLOR]

if you unplug the device does the above change , also could you tell me what the two devices are

need to know if you are connecting via a [COLOR=Blue]usb hub[/COLOR] , or a [COLOR=Blue]usb switcher[/COLOR]

regards

alexfish

Important :Reminder please do not install any software , esp the one mentioned by Paul Reaver (I will explain later)

---

### Post by alexfish on 2010-09-01
A message for Paul Reaver

When posting on threads , read the threads in detail and follow and read the links,
prior advising  , installing 3rd party software , ESP ones not in the repo's or safe sources

---

### Post by andrei90 on 2010-09-01
Hi alex.
So I looked up the command and here's what I got :

   [FONT=&quot]andrei@ubuntu:~$ lsusb[/FONT]
  
  [FONT=&quot]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  
  [FONT=&quot]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  
  [FONT=&quot]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  
  [FONT=&quot][COLOR=Magenta]Bus 005 Device 002: ID 04d9:a01d Holtek Semiconductor, Inc. [/COLOR][/FONT]<--- USB Wireless Mouse
    [FONT=&quot]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  
  [FONT=&quot]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  
  [FONT=&quot]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  
  [FONT=&quot][COLOR=DarkGreen]Bus 002 Device 002: ID 064e:a103 Suyin Corp.         <<<<<------------- I dont know what this is exactly because I have nothing plugged in the USB[/COLOR][/FONT]
    [FONT=&quot]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
  
  [FONT=&quot]***[COLOR=Red]Bus 001 Device 002: ID 12d1:1520 Huawei Technologies Co., Ltd.[/COLOR]***[/FONT] <-- Vodafone :D
  [FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]

  I forgot I didnt plugged it when I typed lsusb :d my mistake here,sorry.

And thank you for the advice my friend :) , I already read this :

*[SIZE=5][[COLOR=Red]**Please do not blindly run commands.**[/COLOR]]("http://ubuntuforums.org/announcement.php?a=54")[/SIZE]*

---

### Post by alexfish on 2010-09-01
Hi

OK found your device ID's ,the listing is  as follows

##################################################################################
# Huawei K3765

DefaultVendor= 0x12d1
[COLOR=Blue]DefaultProduct=0x1520 <=================== Device ID unswitched[/COLOR]

TargetVendor=  0x12d1
[COLOR=Blue]TargetProduct= 0x1465 <=================== this will be the device ID whe[/COLOR]n Switched

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"
####################################################################################

The usb_modeswitch should work

so before downloading post the results of 

Code:

[COLOR=Blue]uname -a[/COLOR]

I will then post the correct links for your system .also on how to download via another computer . and then install on Ubuntu

---

### Post by andrei90 on 2010-09-01
Hi alex. 

Here it is :

   [FONT=&quot]andrei@ubuntu:~$ uname -a[/FONT]
  [FONT=&quot]Linux ubuntu 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux[/FONT]

---

### Post by alexfish on 2010-09-01
Hi Andrei


 This is what you will have to do . Get a usb stick , plug it into a computer with internet access


 Click on the two links provided and download the two packages . store the two packages on the usb stick .take note of the names


 Once in ubuntu connect the usb stick / open it ,find the two packages .double click on the the first package it will self install, same for the second, unplug the usb stick


 Reboot the computer and connect the device. wait for the device to settle. click on the Network Manager, also check the device ID's with the "lsusb command" if problem please inform


 You may see something like "make new connection , if so click and follow the wizard


 Enter the correct pay plan for your provider ,(important) .


 at the end , leave the info as it is , click OK . then hopefully you will now see the connection . click on the connection


The first link is the data package / the on that will contain the necessary data for your device


    [modeswitchdata]("http://packages.debian.org/sid/usb-modeswitch-data")(comm): mode switching data for     usb-modeswitch
20100826-1: all    

this is the modeswitch package for 64 bit systems
     [modeswitch     amd64]("http://packages.debian.org/sid/amd64/usb-modeswitch/download")(>= 1.1.4)    mode switching tool for controlling "flip flop"     USB devices

---

### Post by andrei90 on 2010-09-02
Hi.
I installed everything,and still no response,I even passed trough the Create Broadband Connection Wizard..and still no response

I also did this 
```
sudo gedit /etc/udev/rules.d/Huawie1003.rules

enter line similar to below edit the ID's according to the device

ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

```

With my ID in it of course... And it came with nothing . Now _it doesnt even recognize my Vodafone Huawei_ ...

---

### Post by alexfish on 2010-09-02
Hi Adrei

in the post above requested to use the lsusb command if there is a problem after installing the usb_modeswitch 

Boot up the computer without the device connected

connect the device, wait for the device to settle and post the results of

Code:

[COLOR=Blue]lsusb[/COLOR]

also the ID's in the rules you have done are incorrect

if a rule is to be written then the ID's have to correspond to the device , more on that later ,

also can you post the results of these commands from the terminal

to find the version of modeswitch 

code:
[COLOR=Blue]usb_modeswitch -e[/COLOR]

to see if the device is listed in the database

Code:
[COLOR=Blue]cat /etc/usb_modeswitch.d/12d1:1520[/COLOR]

alexfish

---

### Post by ingol on 2010-09-02
Most likely it is a signal strength issue. Move the computer around until you can get a better cell connection.Look for a place in your house/unit whatever for where the signal is the strongest.


---------------------------------------------------------------
  [custom   logo design]("http://logodesignswork.com/")

---

### Post by andrei90 on 2010-09-02
> **ingol said:**
> Most likely it is a signal strength issue. Move the computer around until you can get a better cell connection.Look for a place in your house/unit whatever for where the signal is the strongest.


---------------------------------------------------------------
  [custom   logo design]("http://logodesignswork.com/")

I have full signal. All around the apartment.

---

### Post by andrei90 on 2010-09-02
> **alexfish said:**
> Hi Adrei

in the post above requested to use the lsusb command if there is a problem after installing the usb_modeswitch 

Boot up the computer without the device connected

connect the device, wait for the device to settle and post the results of

Code:

[COLOR=Blue]lsusb[/COLOR]

also the ID's in the rules you have done are incorrect

if a rule is to be written then the ID's have to correspond to the device , more on that later ,

also can you post the results of these commands from the terminal

to find the version of modeswitch 

code:
[COLOR=Blue]usb_modeswitch -e[/COLOR]

to see if the device is listed in the database

Code:
[COLOR=Blue]cat /etc/usb_modeswitch.d/12d1:1520[/COLOR]

alexfish

Hi alex .
I found out how to fix that sudo gedit etc/udev/rules.d/Huawie1003.rules , I did rm -rf /etc/udev/rules.d/Huawie1003.rules. Now the Huawei usb is recognized...

Here's what u asked for:

   andrei@ubuntu:~$ usb_modeswitch -e
  
  
   * usb_modeswitch: handle USB devices with multiple modes
  
  
   * Version 1.1.4 (C) Josua Dietze 2010
  
  
   * Based on libusb0 (0.1.12 and above)
  
  
   
   
   
   ! PLEASE REPORT NEW CONFIGURATIONS !
  
  
   
   
   
  andrei@ubuntu:~$ cat /etc/usb_modeswitch.d/12d1:1520
  
  
  ########################################################
  
  
  # Huawei K3765
  
  
   
   
   
  DefaultVendor= 0x12d1
  
  
  DefaultProduct=0x1520
  
  
   
   
   
  TargetVendor=  0x12d1
  
  
  TargetProduct= 0x1465
  
  
   
   
   
  CheckSuccess=20
  
  
   
   
   
  # Standard profile
  
  
  MessageContent="55534243123456780000000000000011060000000000000000000000000000"
  
  
   
   
   
  # CDC ether profile
  
  
  ;MessageContent="55534243450100000002000080000611062000000100000000000000000000"
  
  
  ;NoDriverLoading=1

   [COLOR=Blue]**andrei@ubuntu:~$ lsusb**[/COLOR]
  
   
   
  Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
   
  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
   
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
   
  Bus 005 Device 002: ID 04d9:a01d Holtek Semiconductor, Inc. 
  
  

  
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
   
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
   
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
   
  
  

  
  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
   
   
  Bus 001 Device 002: ID 12d1:1520 Huawei Technologies Co., Ltd. 

  
  [FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]

---

### Post by alexfish on 2010-09-02
Hi Andrei

from the info , the modem still has not switched

from the terminal try :

Code:
[COLOR=Blue]usb_modeswitch -v 0x12d -p 0x1520 -M "55534243450100000002000080000611062000000100000000000000000000"[/COLOR]


note on Ubuntu forums you may see the numbers after the -M contain a space this has to be removed before 
entering the command from the terminal / the space will occur at "5553424345010000000200008000061106200000010[COLOR=Blue][COLOR=Black]000000[/COLOR]Here[/COLOR] , remove the space
give time for the device to settle then post the results of

Code:
[COLOR=Blue] lsusb [/COLOR]

only post the line that contains your device

---

### Post by andrei90 on 2010-09-02
andrei@ubuntu:~$ usb_modeswitch -v 0x12d -p 0x1520 -M "55534243450100000002000080000611062000000100000000000000000000"
  
   
   
  Looking for default devices ...
  
   No devices in default mode or class found. Nothing to do. Bye.
   
  andrei@ubuntu:~$ lsusb
  Bus 001 Device 002: ID 12d1:1520 Huawei Technologies Co., Ltd.


_______________________


    andrei@ubuntu:~$ usb_modeswitch -v 0x12d -p 0x1520 -M "5553424345010000000200008000061106200000010000000 0000000000000"
  
  Error: MessageContent hex string has uneven length. Aborting.
   
  andrei@ubuntu:~$ lsusb
  Bus 001 Device 002: ID 12d1:1520 Huawei Technologies Co., Ltd.

---

### Post by alexfish on 2010-09-02
from the terminal try : try these two commands

Code:
usb_modeswitch -v 0x12d -p 0x1520 -M "[COLOR=Red]55534243450100000002000080000611062000000100000000000000000000[/COLOR]"

and then check again with lsusb command

if no change in the ID's try

Code

usb_modeswitch -v 0x12d -p 0x1520 -M "[COLOR=Red]55534243123456780000000000000011060000000000000000000000000000[/COLOR]"

[COLOR=Blue]please remember to check the [COLOR=Red]Numbers[/COLOR] entered in the terminal /remove any spaces in the number[/COLOR]

check again with [COLOR=Blue]lsusb[/COLOR] command

---

### Post by andrei90 on 2010-09-02
> **alexfish said:**
> from the terminal try : try these two commands

Code:
usb_modeswitch -v 0x12d -p 0x1520 -M "[COLOR=Red]55534243450100000002000080000611062000000100000000000000000000[/COLOR]"

and then check again with lsusb command

if no change in the ID's try

Code

usb_modeswitch -v 0x12d -p 0x1520 -M "[COLOR=Red]55534243123456780000000000000011060000000000000000000000000000[/COLOR]"

[COLOR=Blue]please remember to check the [COLOR=Red]Numbers[/COLOR] entered in the terminal /remove any spaces in the number[/COLOR]

check again with [COLOR=Blue]lsusb[/COLOR] command

   andrei@ubuntu:~$ usb_modeswitch -v 0x12d -p 0x1520 -M "55534243123456780000000000000011060000000000000000000000000000"
  
   
   
  Looking for default devices ...
  
   No devices in default mode or class found. Nothing to do. Bye.
  
   
   
  andrei@ubuntu:~$ usb_modeswitch -v 0x12d[COLOR=Blue]**[COLOR=maroon]1[/COLOR]**[/COLOR] -p 0x1520 -M "55534243123456780000000000000011060000000000000000000000000000"
  
   
   
  Looking for default devices ...
  
   Found devices in default mode or class (1)
  
  Accessing device 000 on bus 001 ...
  
  Using endpoints 0x01 (out) and 0x81 (in)
  
  Using endpoints 0x01 (out) and 0x81 (in)
  
  Inquiring device details; driver will be detached ...
  
  Looking for active driver ...
  
   No driver found. Either detached before or never attached
  
   Could not claim interface (error -1). Skipping device inquiry
  
  Error: could not get description string "manufacturer"
  
  Error: could not get description string "product"
  
   
   
  USB description data (for identification)
  
  -------------------------
  
  Manufacturer: 
  
       Product: 
  
    Serial No.: not provided
  
  -------------------------
  
  Looking for active driver ...
  
   No driver found. Either detached before or never attached
  
  Setting up communication with interface 0 ...
  
   Could not claim interface (error -1). Skipping message sending
  
  -> Run lsusb to note any changes. Bye.
  
   
   
  andrei@ubuntu:~$ lsusb
  
   
  [FONT=&quot]Bus 001 Device 002: ID 12d1:1520 Huawei Technologies Co., Ltd. [/FONT]

---

### Post by alexfish on 2010-09-02
Hi

from the listing you have entered the same codes twice , please read previous post carefully , there are two different numbers in the codes:

start again

boot up the computer without the device , then connect the device ; if anydevice shows on the desktop leave it alone

check the device with the lsusb command

Code:

[COLOR=Blue]lsusb[/COLOR]

if the output of the device = [FONT=&quot]Bus 001 Device 002: ID [COLOR=Blue]12d1:1520[/COLOR] Huawei  Technologies Co., Ltd. 

then repeat the advice given in the previous post RE usb_modeswitch , remember there
are two different codes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
if the device ID's  = [/FONT][FONT=&quot]Bus 001 Device 002: ID [COLOR=Blue]12d1:[/COLOR][/FONT][FONT=&quot][COLOR=Blue]1465[/COLOR][/FONT][FONT=&quot] Huawei  Technologies Co., Ltd. 
[/FONT]
[FONT=&quot]check:
from the terminal

Code:

[/FONT][COLOR=Blue]dmesg | grep -e "modem" -e "tty" [/COLOR]

---

### Post by andrei90 on 2010-09-02
Hi

   andrei@ubuntu:~$ usb_modeswitch -v 0x12d -p 0x1520 -M "55534243450100000002000080000611062000000100000000000000000000"
   
  Looking for default devices ...
   No devices in default mode or class found. Nothing to do. Bye.
   
  andrei@ubuntu:~$ usb_modeswitch -v 0x12d -p 0x1520 -M "55534243123456780000000000000011060000000000000000000000000000"
   
  Looking for default devices ...
   No devices in default mode or class found. Nothing to do. Bye.
   
  andrei@ubuntu:~$ lsusb
   
  [FONT=&quot]Bus 001 Device 005: ID 12d1:1520 Huawei Technologies Co., Ltd.[/FONT]

---

### Post by alexfish on 2010-09-03
Hi Andrei

best I can do now is that you join the modeswitch forum

not sure what is happening 

the forum is quite helpfully , also mention you are using 64bit ubuntu

the  [ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")

I could also suggest , trying 32bit Ubuntu 

regards

alexfish

---

### Post by andrei90 on 2010-09-03
Ok alex,thank you for your help.

---

### Post by andrei90 on 2011-05-21
I finally solved it! After a year!

After I installed Xubuntu 11.04, installed the ubuntu-drivers-extra and now my Broadband is up and working 100% perfect! Well done Ubuntu for implementing the new Xubuntu 11.04! I bow to you guys :D

---

### Post by DarianMac on 2011-08-30
A friend asked me to help with a problem he has with mobile broadband connection. I did not know how to help him, why ask here (if allowed).
The problem is this: my friend connects to the Internet through a modem vodafone k3765. I understood that he set up the connection with pppconfig. It seems that the modem is recognized and works well, but the problem occurs when the boots. When an error occurs like "in /etc/ppp/peers/provider unrecognized option /dev/ttyUSB0" and can not connect.
My friend has to reboot to go into Windows, to connect the modem and then reboot again and come in Debian (it has dual boot Debian 6 Squeeze i386/Windows 7. The problem occurs only in Debian).
I understand that the PPP connection set to automatically activate on boot, but the problem persists. What could he do to be able to boot into Debian, and the connection to not have problems?
From the error message, the problem seems to be related to ttyUSB0. I could not help him my friend, I do not know the network connection, especially on such connections.

---

### Post by DarianMac on 2011-08-30
Eh, do not need help. My friend solved the problem yourself. Sorry for the post useless.

---

