---
title: "samsung mobile modem not detecting when connecting new mobile broadband connection"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by saman6015 on 2010-10-17
Hello every one i am using samsung S3310 with aircel when i am connecting new mobile broadband connection my device is not identifying ,so that i cant connect Internet.but everything okay i mean settings in mobile and pc.

for same connection i used Nokia mobile its identified and Internet was connected

but samsung mobile is not identifying 
in terminal i typed LSUSB
my device is shown in that,
i don't know what is the problem 
could anyone help me please

---

### Post by Jahid65 on 2010-10-17
can you paste the result of lsusb command? Is usb-mideswitch is installed? if no, install that & try again. Even doesn't successful then you may have to use wvdial.

---

### Post by saman6015 on 2010-10-18
administrator@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: [SIZE=4]ID 04e8:6795 Samsung Electronics Co., Ltd [/SIZE]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


what is that wvdial  please help me

---

### Post by saman6015 on 2010-10-18
p { margin-bottom: 0.08in; }  administrator@ubuntu:~$ wvdialconf  
 Editing `/etc/wvdial.conf'.  
 

 Scanning your serial ports for a modem. 
 

 ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud  
 ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud  
 ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.  
 Modem Port Scan<*1>: S1   S2   S3   ACM0  
 

 

 Sorry, no modem was detected!  Is it in use by another program?  
 Did you configure it properly with setserial?  
 

 Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)  
 

 If you still have problems, send mail to <wvdial-list@lists.nit.ca>.  
 administrator@ubuntu:~$ lsusb  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 007: ID 04e8:6795 Samsung Electronics Co., Ltd  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 administrator@ubuntu:~$ 







my device is not identifying

---

### Post by Vtwin on 2010-10-20
Hi I'm very new to Ubuntu so what I did may not apply to your position. I'm using a Mobile Broadband dongle ZTE MF112 so nothing to do with Sumsung but it might be the same issue which is that the device is recognized as a CD rather than a modem. Installing mode-switch alone didn't work for me. I ended up going to  /lib/udev/rules.d/61-mobile-action.rules and at the bottom changed the ENV{ID_VENDOR_ID}== "19d2" and
ENV MODEL etc "2000" to the ones that show after running lsusb. In your case 04e8 and 6795. I kept the original entry by commenting out using #. Then copied and pasted and changed to my own modem IDs. I'm not sure if I've explained it very well or if it's completely safe to do but it worked for me when I restarted my computer.

---

### Post by saman6015 on 2010-10-21
i couldn't  understand  please explain................

---

### Post by halj32 on 2010-10-21
> **Vtwin said:**
> Hi I'm very new to Ubuntu so what I did may not apply to your position. I'm using a Mobile Broadband dongle ZTE MF112 so nothing to do with Sumsung but it might be the same issue which is that the device is recognized as a CD rather than a modem. Installing mode-switch alone didn't work for me. I ended up going to  /lib/udev/rules.d/61-mobile-action.rules and at the bottom changed the ENV{ID_VENDOR_ID}== "19d2" and
ENV MODEL etc "2000" to the ones that show after running lsusb. In your case 04e8 and 6795. I kept the original entry by commenting out using #. Then copied and pasted and changed to my own modem IDs. I'm not sure if I've explained it very well or if it's completely safe to do but it worked for me when I restarted my computer.

he/she is saying you may need to install usb-mode-switch
try installing it with Synaptic Package Manager

goodluck

---

### Post by saman6015 on 2010-10-22
i did every thing but not identifying modem by network manger

---

### Post by Vtwin on 2010-10-22
Hi I'll try and explain more clearly what worked for me although your Samsung might be completely different and I'm too inexperienced to offer any other advice. 

Start the terminal and enter  sudo gedit
I used Open to navigate to /lib/udev/rules.d/61-mobile-action.rules
At the bottom there's an entry for ZTE MFxxx. 
I copied and pasted this entry below the original
In your case you would then change "19d2" to "04e8" and "2000" to "6795" and then click on save.
Reboot and see if your modem shows up in Network Manager.
If it doesn't work it would probably be a good idea to remove the changes made in the 61-mobile file.
Hope this helps

---

### Post by saman6015 on 2010-10-23
i did below mentioned

Start the terminal and enter sudo gedit
I used Open to navigate to /lib/udev/rules.d/61-mobile-action.rules
At the bottom there's an entry for ZTE MFxxx. 
I copied and pasted this entry below the original
In your case you would then change "19d2" to "04e8" and "2000" to "6795" and then click on save.
Reboot and see if your modem shows up in Network Manager.
If it doesn't work it would probably be a good idea to remove the changes made in the 61-mobile file.
Hope this helps

and one more thing i did 
sudo gedit
i used to open to navigate to /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi 
i edited samsung vendor not identifying

---

### Post by dineshs on 2010-10-23
what does ```
dmesg | grep -e "modem" -e "tty" 
```say

---

### Post by saman6015 on 2010-10-24
**mobile modem** 			
 			 			 		   		 		 		Hello every one i am posting this as fifth time 

[SIZE=3]i don't know how to connect Internet using samsung mobile  S3310 i connected with nokia it's worked,but in samsung mobile it is  not connecting [/SIZE].

i searched full of this Ubuntu forum related to this problem, i got some of threats in that too there is no solution 

main thing is device is identified by USB but not by network manager.

i did 

administrator@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
administrator@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
administrator@ubuntu:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   ACM1 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

administrator@ubuntu:~$ sudo apt-get install usb-modeswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
usb-modeswitch is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
administrator@ubuntu:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.334037] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.334489] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.467939] tty tty55: hash matches
[  221.698623] cdc_acm 3-3:1.8: ttyACM0: USB ACM device
[  221.703210] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  237.831165] cdc_acm 3-3:1.8: ttyACM0: USB ACM device
[  413.099290] cdc_acm 2-3:1.8: ttyACM0: USB ACM device
[  512.280554] cdc_acm 3-3:1.8: ttyACM0: USB ACM device
administrator@ubuntu:~$ 




i dont know ,what i have do ,
last few days i was tried i didn't get the solution,i got so much  disappointment if i get simple idea related to this problem i will be  very happy

please,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,  ,,,,,,,,,,,

thanks in advance
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10011388") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10011388")

---

### Post by dineshs on 2010-10-25
> [ 512.280554] cdc_acm 3-3:1.8: ttyACM0: USB ACM device
[This ]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1483169")thread looks similar.

---

