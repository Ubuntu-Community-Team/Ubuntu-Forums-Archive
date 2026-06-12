---
title: "AnyData adu-560d USB Modem w/ Ubuntu 10.10"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by CR4ZYC on 2011-02-09
I can not get my internet to work on ubuntu 10.10 using my AnyData adu-560d Modem. The only way I'm connected to the internet is with this modem and windows!

What I did:
I connected my USB Modem.
I used the network setup program.
From there I selected Mobile Modem. Found AnyData, found my location, Found my ISP in the listing. 
I completed that. When I go to click on the wireless symbol at the top. My newly created wireless mobile setting is listed. It appears that it tries to connect, but then Immediately a message pops up stating that I am offline.

I found out that my Modem only shows up as a CD-drive. (/dev/sr2)

I don't know what to do.

---

### Post by CR4ZYC on 2011-02-10
):P I would also like to post more stuff to see what is actually going on but, I don't know where to find any logs or error messages related to this problem. Any Help is appreciated!

---

### Post by thomazp on 2011-02-11
I saw someone with this problem.
He ejected it and began to work.
Try it.
Good Luck.
Best.

---

### Post by CR4ZYC on 2011-02-11
p { margin-bottom: 0.08in; }  I tried to ejecting ttyUSB0 in terminal. 
It says it's busy!  In disk utility only CD-drive shows up for my modem iafter ejecting nothing happens.


 Syslog:
 

 ubuntu modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted  
 Feb 11 14:11:45 ubuntu modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted  
 Feb 11 14:11:45 ubuntu modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted  
 Feb 11 14:11:45 ubuntu modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Successfully called chroot.  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Successfully dropped privileges.  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Successfully limited resources.  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Running.  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Canary thread running.  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Watchdog thread running.  
 Feb 11 14:11:47 ubuntu rtkit-daemon[1426]: Supervising 1 threads of 1 processes of 1 users.  
 Feb 11 14:11:48 ubuntu rtkit-daemon[1426]: Supervising 2 threads of 1 processes of 1 users.  
 Feb 11 14:11:48 ubuntu rtkit-daemon[1426]: Supervising 3 threads of 1 processes of 1 users.  
 Feb 11 14:13:19 ubuntu rtkit-daemon[1426]: Supervising 4 threads of 2 processes of 2 users.  
 Feb 11 14:13:19 ubuntu rtkit-daemon[1426]: Supervising 5 threads of 2 processes of 2 users.  
 Feb 11 14:13:19 ubuntu rtkit-daemon[1426]: Supervising 6 threads of 2 processes of 2 users.  
 Feb 11 14:13:20 ubuntu rtkit-daemon[1426]: Supervising 7 threads of 3 processes of 2 users.  
 Feb 11 14:13:36 ubuntu kernel: [ 126.202363] sr 7:0:0:0: Attached scsi CD-ROM sr1  
 Feb 11 14:14:07 ubuntu modem-manager: (ttyUSB0): probe requested by plugin 'AnyData'  
 Feb 11 14:14:07 ubuntu modem-manager: (ttyUSB2): probe requested by plugin 'AnyData'  
 Feb 11 14:14:07 ubuntu modem-manager: (ttyUSB1): probe requested by plugin 'AnyData'  
 Feb 11 14:14:08 ubuntu kernel: [ 158.003325] sr 8:0:0:0: Attached scsi CD-ROM sr1  
 Feb 11 14:14:10 ubuntu modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2  
 Feb 11 14:14:10 ubuntu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2  
 Feb 11 14:14:10 ubuntu modem-manager: (tty/ttyUSB1): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2  
 Feb 11 14:14:25 ubuntu modem-manager: last message repeated 2 times  
 Feb 11 14:14:25 ubuntu modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2 as /org/freedesktop/ModemManager/Modems/0  
 Feb 11 14:14:25 ubuntu modem-manager: (/org/freedesktop/ModemManager/Modems/0): data port is ttyUSB0  
 Feb 11 14:14:25 ubuntu modem-manager: Got failure code 100: Unknown error  
 Feb 11 14:15:15 ubuntu modem-manager: last message repeated 5 times  
 

 dpkg:
 install usb-modeswitch-data <none> 20100826-1  
 2010-10-07 16:11:56 status half-installed usb-modeswitch-data 20100826-1  
 2010-10-07 16:11:56 status unpacked usb-modeswitch-data 20100826-1  
 2010-10-07 16:11:56 status unpacked usb-modeswitch-data 20100826-1  
 2010-10-07 16:11:56 install usb-modeswitch <none> 1.1.4-1  
 2010-10-07 16:11:56 status half-installed usb-modeswitch 1.1.4-1  
 2010-10-07 16:11:57 status unpacked usb-modeswitch 1.1.4-1  
 2010-10-07 16:11:57 status unpacked usb-modeswitch 1.1.4-1
 I know that usb-modeswitch is installed and it seemed to have worked on my modem then
 

 lsusb :
 has : Bus 006 Device 003: ID 16d5:6502 AnyDATA Corporation CDMA/UMTS/GPRS modem  
 

 I set up a new mobil broadband connection and put everything in (Number, User, Password, ISP Name,)
 and then nothing happens.
 

 When I clickon the network connection button and select the connection I created, I can see that it attempts to connect for less than a second.   And then I get a message saying Working offline!


I've tried gnome-ppp  also unsuccessful.

---

### Post by CR4ZYC on 2011-02-12
Does Any one now of a windows emulator that I could use to run my modem in a windows like environment, but still within Linux? I could then possibly route the Internet from their.....

---

### Post by CR4ZYC on 2011-02-12
This is when it changed to a modem ( I believe it was the first time I plugged it in) notice the ERROR message: 

ubuntu kernel: [ 9740.787731] sr 6:0:0:0: Attached scsi CD-ROM sr1 
Feb 12 08:06:40 ubuntu modem-manager: (ttyUSB0): probe requested by plugin 'AnyData' 
Feb 12 08:06:40 ubuntu modem-manager: (ttyUSB2): probe requested by plugin 'AnyData' 
Feb 12 08:06:40 ubuntu modem-manager: (ttyUSB1): probe requested by plugin 'AnyData' 
Feb 12 08:06:41 ubuntu kernel: [ 9772.513796] sr 7:0:0:0: Attached scsi CD-ROM sr1 
Feb 12 08:06:42 ubuntu modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:06:42 ubuntu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:06:42 ubuntu modem-manager: (tty/ttyUSB1): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:06:57 ubuntu modem-manager: last message repeated 2 times 
Feb 12 08:06:57 ubuntu modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 as /org/freedesktop/ModemManager/Modems/0 
Feb 12 08:06:57 ubuntu modem-manager: (/org/freedesktop/ModemManager/Modems/0): data port is ttyUSB0 
Feb 12 08:06:57 ubuntu modem-manager: Got failure code 100: Unknown error 
Feb 12 08:07:40 ubuntu modem-manager: last message repeated 5 times 
Feb 12 08:14:27 ubuntu modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:19:43 ubuntu kernel: [10554.806771] sr 8:0:0:0: Attached scsi CD-ROM sr1 
Feb 12 08:20:14 ubuntu modem-manager: (ttyUSB1): probe requested by plugin 'AnyData' 
Feb 12 08:20:14 ubuntu modem-manager: (ttyUSB0): probe requested by plugin 'AnyData' 
Feb 12 08:20:14 ubuntu modem-manager: (ttyUSB2): probe requested by plugin 'AnyData' 
Feb 12 08:20:15 ubuntu kernel: [10586.524741] sr 9:0:0:0: Attached scsi CD-ROM sr1 
Feb 12 08:20:16 ubuntu modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:20:16 ubuntu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:20:16 ubuntu modem-manager: (tty/ttyUSB1): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:20:16 ubuntu modem-manager: (tty/ttyUSB1): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:20:29 ubuntu modem-manager: (tty/ttyUSB2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 
Feb 12 08:20:31 ubuntu modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1 as /org/freedesktop/ModemManager/Modems/1 
Feb 12 08:20:31 ubuntu modem-manager: (/org/freedesktop/ModemManager/Modems/1): data port is ttyUSB0 
Feb 12 08:36:36 ubuntu modem-manager: Got failure code 100: Unknown error 
Feb 12 08:37:42 ubuntu modem-manager: last message repeated 5 times


After applying all updates in Ubuntu. Modem seems to connect.... it goes thru a cylce then it disconnects. It is doing more than before! But still no internet!

Here is My SYSlog from one of these cycles:

 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) starting connection 'Kalimat Telecom connection 1'
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> (ttyUSB0): device state change: 3 -> 4 (reason 0)
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> (ttyUSB0): device state change: 4 -> 6 (reason 0)
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> (ttyUSB0): device state change: 6 -> 4 (reason 0)
Feb 12 09:16:38 ubuntu NetworkManager[964]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Feb 12 09:17:01 ubuntu CRON[30493]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 09:17:39 ubuntu NetworkManager[964]: <warn> CDMA connection failed: (32) No service
Feb 12 09:17:39 ubuntu NetworkManager[964]: <info> (ttyUSB0): device state change: 4 -> 9 (reason 0)
Feb 12 09:17:39 ubuntu NetworkManager[964]: <info> Marking connection 'Kalimat Telecom connection 1' invalid.
Feb 12 09:17:39 ubuntu NetworkManager[964]: <warn> Activation (ttyUSB0) failed.
Feb 12 09:17:39 ubuntu NetworkManager[964]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Feb 12 09:17:39 ubuntu NetworkManager[964]: <info> (ttyUSB0): deactivating device (reason: 0).
Feb 12 09:17:44 ubuntu AptDaemon: INFO: Quiting due to inactivity
Feb 12 09:17:44 ubuntu AptDaemon: INFO: Shutdown was requested
Feb 12 09:17:44 ubuntu AptDaemon: INFO: Initializing daemon

yellow light is on after the cycling.
In the manual for modem: YELLOW LIGHT = Success to network acquisition (Idle state)

I have tried to eject sdr1

sudo eject -v /dev/sdr1

tells me scsi eject sucessful but it is still listed in Disc Utility.



Still no Internet connection and I'm going crazy!
Any help is appreciated.

---

### Post by CR4ZYC on 2011-02-12
I stopped networkmanager, 
so I could try gnome-ppp.

looks like I get farther....
CHAP works but then can't get ARP....
then tries DHCP.... no response....

Every time I try connecting 5 packets get send and 4 are received.

So the initial handshake was completed..... don't know what to do.

I changed options, but I can't get further.

So frustrating.

---

### Post by CR4ZYC on 2011-02-13
I found a way around this issue.
  	 	 	 	p { margin-bottom: 0.08in; }   [COLOR=#000000][FONT=Courier New, serif][SIZE=2]It seems to be an issue with network-manager and how it is controlling the modem.
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New, serif][SIZE=2]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New, serif][SIZE=2]sudo service network-manager stop[/SIZE][/FONT][/COLOR]

This opens your modem up then use gnome-ppp

sudo gnome-ppp

And then put your username, password and #777 

And hit connect.   It will not show that your are connected! Open a browser and surf it up :D!

Hopefully they fix this in the next network-manager release!

You can remove network-manager from your start up programms so you don't have to stop it everytime!

---

