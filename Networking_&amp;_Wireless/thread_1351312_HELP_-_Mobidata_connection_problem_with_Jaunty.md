---
title: "HELP - Mobidata connection problem with Jaunty"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by holy_rainman on 2009-12-10
Hello experts of Ubuntu,

i have a problem where i have a mobidata modem and cannot connect with my jaunty. i have tried several ways and these are the steps that i have done...

1) installed (in order) wvdial in offline mode by downloading the files:
         1_libxplc0.3.13_0.3.13-1_i386.deb
         2_libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb
         3_libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb
         4_libuniconf4.4_4.4.1-0.2ubuntu2_i386.deb
         5_wvdial_1.60.1+nmu2_i386.deb
    all files was successfully installed.

2) Get the latest usb_modeswitch file from the page [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) from the section "Downloads"

3) click with the right button of the mouse in the file and select extract here. (/desktop)

4) Get the latest usb_modeswitch.conf from the page [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) from the section "Downloads"

5) typed sudo -i (asked for password)

6) typed sudo cp '/home/rainman/Desktop/usb_modeswitch.conf' '/etc' 
    (the reason i did not use make install because i observed when make install, the copied data seemed been cutoff since my mobidata is at the end of the file. that is why i copied it manually and checked it was ok and no cutoff data)

7) typed cd /home/rainman/Desktop/usb_modeswitch-1.0.5

8) typed sudo gedit /etc/usb_modeswitch.conf 

9) looked for the modem mobidata 100hu and erased the comments # and ;. it looked like this:

##########################################
MobiData MBD-100HU 
 
Unconfirmed. Please report! 
 
Contributor: Chris ?  
DefaultVendor=  0x1c9e  
DefaultProduct= 0xf000  

TargetVendor=   0x1c9e 
TargetProduct=  0x9603 

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"  

saved and quit.

10) pluged the modem. typed lsusb and the result was:
    Bus 001 Device 003: ID 064e:d101 Suyin Corp.
    Bus 001 Device 002: ID 1c9e:f000  
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

11) typed sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
      and then typed lsusb. the result was this:
    Bus 001 Device 007: ID 1c9e:9603  
    Bus 001 Device 003: ID 064e:d101 Suyin Corp. 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 002: ID 15d9:0a33  
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

    ID has changed from f000 to 9603

12) typed sudo gedit /etc/wvdial.conf
     edited the wvdial.conf according to this setting:

[Dialer digi]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Idle Seconds = 0
Auto Reconnect = 1
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW
Username = user
Password = pass

13) all was done without any error. however when the final step to connect the modem where i typed sudo wvdial digi, the result was:

root@aim:/home/rainman/Desktop/usb_modeswitch-1.0.5# sudo wvdial digi
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or dir

===> i am new to this ubuntu and the question is... is there anything wrong that i have done or is there any missing step? (i have done quite a research and some discussion) Please give any comment regarding my steps if there is any wrong doing. Hope some experts will help solve my problem..   :)

---

### Post by GeorgeVita on 2009-12-13
Hi **holy_rainman**,
after step **#11** you have a new productID which possibly is the real modem. After this you must check/create some communication ports as /dev/ttyUSB0 and try to use them! So try the following:

11a) **sudo modprobe usbserial vendor=0x1c9e product=0x9603**

11b) **ls /dev/ttyUSB***
... you must see some ports created. If not, check last lines of **dmesg** to determine what happened

Regards,
George

---

