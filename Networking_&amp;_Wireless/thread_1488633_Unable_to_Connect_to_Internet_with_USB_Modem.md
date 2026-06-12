---
title: "Unable to Connect to Internet with USB Modem"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by vinaykumaruppalapati on 2010-05-20
Hi
 
I am using BSNL EVDO USB modem for internet connection from pasy 1 year. I have no problem using it in Windows, how ever when it comes to UBUNTU it will never conncets.
 
This device worked weell in Ubuntu 9.04, not worked in 9.10.
when it comes to 10.04, system is recognising the device and it will get connected at the begining and gets disconnected after few minutes and it will never connect.
Some times it connects when I remove the device and pluginn again.
 
Alternately I have installed WVDial as recommended by many users in online forms. The problem now is the connection is getting disconnected freaquently and some times I will get responce as modem not responding, and some time I will get responce unable to initiate the modem.
 
Please guys this is the main problem which I am facing.
 
Another problem which I am facing is that I am getting wavy picture when i play videos in You tube. Normal movies when I play in media players are fine I think its only problem with the Youtube videos.

---

### Post by alexfish on 2010-05-20
hi

there may be more than one problem to sort with the device 

so need some info ; 

1 . boot up the computer with out the device
2 . plug the device in and allow the device to settle
3. does any icon or file etc appear on the desk top ; **need answer**
4. from the terminal enter this code

Code :

lsusb

5. if a device has appeared on the desk top , right click and safely remove the device
5.1 use the lsusb command again , **post the results**
5.2 if no device has appeared on the desk top open up the Disk utility from the system menu . take a screen shot of the window . **post the results**
5.3 from the terminal 

Code:

dmesg | grep -e "modem" -e "tty"  **post the results**


6. try to make the connection with the modem, if successful go to 7 , if not Stop and post all the results requested

7. wait until the connection is dropped , go back to 5.1 , then post the results requested

---

### Post by vinaykumaruppalapati on 2010-05-20
Hi alexfish;9332915]

Thank You for your immediate help, the below are the results for your questions.

I have rebouted the system with out usb modem, but no icon or file appeared on the desktop

For the terminal code I got the following results

"vkums@vkums:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 19d2:fffe ONDA Communication S.p.A. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vkums@vkums:~$ "

The Terminal results after removing the USB modem for the code "lsusb" is as follows (With out any icon on the desktop)

"vkums@vkums:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vkums@vkums:~$ "

The screen shot of the Disk utility is as follows, if unable to view, pls see the attachment.

[IMG]http://ubuntuforums.org/home/vkums/Desktop/Screenshot-3.png[/IMG]



The results for the terminal code "dmesg | grep -e "modem" -e "tty" " is as follows

"vkums@vkums:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.252160] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.252576] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   96.416369] USB Serial support registered for GSM modem (1-port)
[   96.417277] option 3-2:1.0: GSM modem (1-port) converter detected
[   96.418653] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[   96.418736] option 3-2:1.1: GSM modem (1-port) converter detected
[   96.420810] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[   96.420889] option 3-2:1.2: GSM modem (1-port) converter detected
[   96.421334] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
[   96.421385] option 3-2:1.3: GSM modem (1-port) converter detected
[   96.421700] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB3
[   96.421754] option: v0.7.2:USB Driver for GSM modems
[  407.140657] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  407.155937] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  407.156681] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  407.156980] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  693.047825] option 3-2:1.0: GSM modem (1-port) converter detected
[  693.048109] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[  693.051571] option 3-2:1.1: GSM modem (1-port) converter detected
[  693.051930] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[  693.053679] option 3-2:1.2: GSM modem (1-port) converter detected
[  693.054053] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
[  693.057350] option 3-2:1.3: GSM modem (1-port) converter detected
[  693.057719] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB3
vkums@vkums:~$"

Hi I did not pasted the "lsusb" terminal code results after net got disconnected because when I am posting this results the net is working and I will paste the results once the net gets disconnected.
Hi just want to inform you that all the results above are of "NetworkManager Applet 0.8" and not of wvdial.

Please note that the net is not connecting automatically when I start up the system.

---

### Post by vinaykumaruppalapati on 2010-05-20
Hi the below is the result for the terminal comand "lsusb" after net got disconnected.

"vkums@vkums:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 011: ID 19d2:fffe ONDA Communication S.p.A. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vkums@vkums:~$ ^C
vkums@vkums:~$" 

I have tried connecting the net using network manager, but unable to connect.
I tried connecting with "wvdial" unable to connect 
the following are the terminal output when tried wvdial

"vkums@vkums:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
vkums@vkums:~$ sudo wvdial
[sudo] password for vkums: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
vkums@vkums:~$ "

After removing and inserting the usb modem again I have tried connection with network manager but unable to connect
Then tried connecting with "wvdial" but the out put is as below.

"vkums@vkums:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
vkums@vkums:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
--> Sending: ATQ0
--> Re-Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
--> Modem not responding.
vkums@vkums:~$"

I have deleted the mobile broadband from the network manager and removed the usb modem and reinsurted and tried wvdial the net got connected and got disconnected immediately, the below are the results....

"vkums@vkums:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }-}#}%B#}%}'}"}(}"{B~
--> PPP negotiation detected.
--> Starting pppd at Fri May 21 08:07:19 2010
--> Pid of pppd: 2604
--> Using interface ppp0
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> local  IP address 117.254.125.87
--> pppd: (&#65533;9 @&#65533;9 
--> remote IP address 192.168.52.12
--> pppd: (&#65533;9 @&#65533;9 
--> primary   DNS address 218.248.240.181
--> pppd: (&#65533;9 @&#65533;9 
--> secondary DNS address 208.67.220.220
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> Connect time 0.3 minutes.
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> Disconnecting at Fri May 21 08:07:42 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port."

Then again after some time I got connected to net with wvdial automatically the below are the continued results of the above results

--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }-}#}%B#}%}'}"}(}"{B~
--> PPP negotiation detected.
--> Starting pppd at Fri May 21 08:08:09 2010
--> Pid of pppd: 2644
--> Using interface ppp0
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 
--> local  IP address 117.254.117.128
--> pppd: (&#65533;9 @&#65533;9 
--> remote IP address 192.168.52.12
--> pppd: (&#65533;9 @&#65533;9 
--> primary   DNS address 218.248.240.181
--> pppd: (&#65533;9 @&#65533;9 
--> secondary DNS address 208.67.220.220
--> pppd: (&#65533;9 @&#65533;9 
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: (&#65533;9 @&#65533;9 
--> Connect time 13.7 minutes.
--> pppd: (&#65533;9 @&#65533;9 
--> pppd: (&#65533;9 @&#65533;9 

Well if you want any further details I will post them, pls help me resolving this issue.

---

### Post by alexfish on 2010-05-21
hi

when you get the above error message resources busy , this is the modem manager hanging on to the modem and its ports, if this happens the unplug the device and then reconnect it

since you have achieved success with wvdial {last message } I recommend using this for the connection,if the modem is problematic for the Network Manager { can be notable with some CDMA connections} then monitor further while using wvdial

also give your system and the modem time to settle before making the connection

if you don't like using the terminal then use Gnomeppp ,it  is a front end tool for wvdial 

regards

alexfish

---

### Post by vinaykumaruppalapati on 2010-05-22
Hi


Thank you for your help, I have now installed Gnome PPP and the net is working perfectly well.

You have really solved my problem.

You know what I have another problem which is related to the videos in the you tube, I am getting wavy videos in you tube, when I am playing movies in normal players I am getting good picture, but the problem is only with the you tube movies.( I do understand that I have to either open a new thread in videos section or need to post in the one which is already running I will do that this sunday.)

---

