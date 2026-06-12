---
title: "Relaince NC on Hardy 8.04"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by mak_20789 on 2010-05-02
Hi,
     anyone from India pls answer my query:

I surf net only thru Ubuntu and I read 2 articles abt connecting Reliance NC on ubuntu so thinking that it would work on my Hardy 8.04 I bought it, but it wouldnt work. Also one command:

modprobe usbserial vendor=0x12d1 product=0×1412  
(I replaced 1412 with the number on my machine)

gave me a Fatal error, but I gave the same command with sudo and no error was shown. Did I mess up with something?

I am giving the 2 articles I followed here that didnt work.
Post will get a lengthy, pls bear with me.
Thank you in advance.

1st article:

Configuring wvdial

Now , we need to configure wvdial to connect to Reliance Netconnect; to do so open gedit or any other editor you like and modify the wvdial.conf file.

    sudo gedit /etc/wvdial.conf

it should have default settings and section, don't modify them and instead add the following section:

    [Dialer Defaults]
    Init1 = ATZ
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    Modem Type = Analog Modem
    Baud = 9600
    New PPPD = yes
    Modem = /dev/ttyUSB0
    ISDN = 0

    [Dialer netconnect]
    Username = ( Add your Phone Number here)
    Password = ( Add your phone number here)
    Phone = #777
    Stupid Mode = 1
    Inherits = Modem0

Replace your Phone number with your actual phone number , like 93102xxxx for me and save the configuration file.

Now, once you are done configuring wvdial, connect by issuing the following command:
sudo wvdial netconnect and wait for pppd to start, once connection has been successful you should see local ip address , remote IP address and 
address of DNS servers on the screen. To disconnect , press Ctrl+C in the terminal window where you had connected.




2nd article:

Pre-Configuration Procedures 

2)      Boot up Linux

3)      Open up a terminal  and key in su (Stands for Super user and it gives you administrative privileges )

4)      Plugin your USB modem and unplug any other devices you have installed (including any wired/wireless internet connections you may have).

5)      Next key in lsusb (This command lists all the usb devices currently connected to your system )

Your output should be similar to this

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 12d1:1412 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubIt may vary slightly depending on your modem make (Huawei or quallcom).

6)    Make sure to note down the number that you get . Here for example it would be 12d1:1412

7) Next key in  modprobe usbserial vendor=0x12d1 product=0×1412  ,

make sure that the number you enter for your vendor and product are the number you got for your lsusb command.

Configuring software client wvdial

Now we are going to use wvdial in Linux to connect to the internet .wvdial is just a generic internet client which can be used to connect to any internet connection that requires dialing . For example : your landline Dialup connection or in our case a mobile broadband internet  Its kind of like an all purpose internet client software.

8 ) open up wvdial’s configuration file using this command

gedit /etc/wvdial.conf
9) Paste the below code into the window that pops up ( make sure to enter your relevant details ).

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Stupid Mode = 1

Modem Type = USB Modem

ISDN = 0

Phone = #777

New PPPD = yes

Modem = /dev/ttyUSB0 (This may also be dev/ttyUSB2 depending on where you plugged in your device)

Username = 9xxxxxxxxxx (your username, should be a number )

Password = 9xxxxxxxxxx (Your password , should be the same number)

CBaud = 460800

Delete all the comments in the brackets . The fields you should edit are Modem , Username and password the only ones with comment .

Save and exist .

10) That’s it ! your done , that was simple was nt it ?

Fire up a new Terminal and key in sudo wvdial , enter your root password in the password prompt . it should generate a long list of codes finally ending with Primary DNS Secondary DNS . If it does you have got your connection working successfully  ! enjoy.

Closing your connection :

You can disconnect your client by selecting your terminal and pressing  Ctrl+C

---

### Post by GeorgeVita on 2010-05-02
Hi **mak_20789**,
under the 'product name' Reliance NC will probably be a different modem device resulting to another set up procedure.
Please reboot without the modem, open a terminal and use ```
sudo dmesg -c
``` to clear all system log. Then attach your modem, wait 30 seconds, from terminal: ```
lsusb
``` find your modem, use: ```
sudo modprobe usbeserial vendor=0xABCD product=0xEFGH
``` replacing ABCD and EFGH with that shown on lsusb. Check ```
dmesg
``` and post here the output from **lsusb** and the last **dmesg** (NOT the output from the 1st one).

Regards,
George

---

### Post by mak_20789 on 2010-05-02
Hi George,
          thank you for your reply.
I followed all your instructions.
Here is the output of the 2 commands you asked for:

lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:624f Microdia 
Bus 001 Device 001: ID 0000:0000 



dmesg:

[  187.251806] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  187.419957] usb 4-1: configuration #1 chosen from 1 choice
[  187.564929] usbcore: registered new interface driver libusual
[  187.591001] Initializing USB Mass Storage driver...
[  187.592414] scsi2 : SCSI emulation for USB Mass Storage devices
[  187.593933] usbcore: registered new interface driver usb-storage
[  187.593944] USB Mass Storage support registered.
[  187.594075] usb-storage: device found at 2
[  187.594079] usb-storage: waiting for device to settle before scanning
[  192.591649] usb-storage: device scan complete
[  192.594645] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[  192.639565] sr1: scsi-1 drive
[  192.639640] sr 2:0:0:0: Attached scsi CD-ROM sr1
[  192.639691] sr 2:0:0:0: Attached scsi generic sg2 type 5
[  196.021134] ISO 9660 Extensions: Microsoft Joliet Level 1
[  196.027132] ISOFS: changing to secondary root
[  377.139149] usbcore: registered new interface driver usbserial
[  377.139453] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  377.139764] usbcore: registered new interface driver usbserial_generic
[  377.139770] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core

Please tell me what to do next.
Regards
Mak

---

### Post by GeorgeVita on 2010-05-03
> **mak_20789 said:**
> ...
Bus 004 Device 002: ID **12d1:1446** Huawei Technologies Co., Ltd. 
[  192.639565] **sr1**: scsi-1 drive
[  192.639640] sr 2:0:0:0: Attached scsi CD-ROM **sr1**

Hi **mak_20789**, try the following:
- reboot without modem, wait for the system to load, do NOT use 'sudo modprobe ...'
- attach modem, wait 30 seconds, check dmesg and note **srX** drive
- from terminal eject it (use appropriate srX, below shown sr1): ```
sudo eject sr1
```
- wait some seconds and check again lsusb
- we need a new product id (ex. 0x140c or 0x1003 etc), in that case try: ```
sudo modprobe usbeserial vendor=0x12d1 product=0xEFGH
```
- check again last lines of dmesg for the creation of ports (/dev/ttyUSB0)

Regards,
George

(also consider trying a newer LiveCD of ubuntu, now running the 10.04 LTS)

---

