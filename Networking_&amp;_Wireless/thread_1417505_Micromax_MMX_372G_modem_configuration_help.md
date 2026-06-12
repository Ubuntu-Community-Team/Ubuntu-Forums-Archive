---
title: "Micromax MMX 372G modem configuration help"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by pratik_narain on 2010-02-27
I've purchased a Micromax MMX 372G 3g usb modem with a BSNL 3G sim card in India. It is automatically mounted as a storage device. I referred to google and learned about usb_modeswitch. I used usb_modeswitch and I'm able to actually recognize the modem at /dev/ttyUSB1. I tried Network Manager as well as wvdial to connect. With network manager I've no success. And with wvdial also Its not connecting. I'm posting the script which I use to switch modem mode as well as my wvdial.conf file and lsusb output before and after the modem modeswitch.

**~/init_3g_modem**
# /bin/bash

usb_modeswitch -v 0x05c6 -p 0xf000 -M "5553424312345678000000000000061b000000020000000000000000000000"
sleep 2
modprobe -v option 
sleep 2
echo "05c6 9000" >/sys/bus/usb-serial/drivers/option1/new_id

**wvdial.conf**
Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","gprsnorth3g.cellone.in"
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB1
Username = 9532996898
Password = pratik
Baud = 9600

**lsusb before modeswitch**
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 016: ID 05c6:f000 Qualcomm, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 0421:04c4 Nokia Mobile Phones 
Bus 006 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

-- the Qualcomm device is the storage device.

**lsusb after modeswitch**
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 017: ID 05c6:9000 Qualcomm, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 0421:04c4 Nokia Mobile Phones 
Bus 006 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

-- I'm not confirm that whether it is the qualcomm or the primax device that is the modem mode device.

Any help regarding this is requested ASAP. Thank you.

---

### Post by metatecque on 2010-02-27
GeekSquid: said this ...

modprobe usbserial ...... see this post 

[http://trick-mobile.blogspot.com/2009/07/settings-for-airtel-gprs-on-ubuntu-via.html](http://trick-mobile.blogspot.com/2009/07/settings-for-airtel-gprs-on-ubuntu-via.html)

---

### Post by pratik_narain on 2010-02-27
I already tried the above method

---

### Post by pdc on 2010-02-28
have you tried the wvdial script with ttyUSB2 ? (instead of ttyUSB1 )

---

### Post by pratik_narain on 2010-02-28
@pdc Is there any specific reason to suggest this as wvdialconf detects the modem at ttyUSB1 only.

---

### Post by alexfish on 2010-02-28
> **pratik_narain said:**
> @pdc Is there any specific reason to suggest this as wvdialconf detects the modem at ttyUSB1 only.


hi

you can  check which lines are been by the modem with this code from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

also a useful command to see what may be happening, use a separate terminal

Code:

tail -f /var/log/syslog

also remove any usb devices not require when setting up the modem ,IE the Nokia Phone, 

regards

alexfish

---

### Post by grtraders on 2010-03-27
Hi prateek

Its sad that you abandoned ubuntu. [http://bbs.archlinux.org/viewtopic.php?pid=729246](http://bbs.archlinux.org/viewtopic.php?pid=729246)

I really salute your efforts trying to install this thing onto your Ubuntu Os but unfortunately what you are trying to do is pretty simple and established easily.

I have successfully connected the same modem to my Ubuntu 9.10 Laptop & it works like a charm.

Coming to your Point --

Download usbswitch from [www.draisberghof.de/usb_modeswitch](www.draisberghof.de/usb_modeswitch)

If you are using Firefox and you choose to save the file you will find it in the Home/User/Downloads folder Where User is your  login username.

At the Top Bar click Places >> Computer >> File System >> Home >> User >> Downloads >> Select the File named usb-modeswitch-1.1.1.tar.bz2 & Right Click n choose Extract here. You will find a Folder named usb-modeswitch-1.1.1 created there itself. Close the Window.

Open up a terminal window by clicking Applications at the Top Bar >> Accessories >> terminal

Enter the following hitting Enter after each line of Code--

```
cd /home/user/Downloads/usb-modeswitch-1.1.1
```
```
sudo make install
```
Enter your password when prompted
```
exit
```

Plug in your Modem. The Red Flashing Light should change to Green Flashing (if it is GPRS connection) or Blue Flashing if it is 3G connection.

1. At the top Bar, to the side of the Speaker Icon, right click Network icon & select "Edit Connections" >> Mobile Broadband tab >> Add button.

2. In the New mobile broadband connection window, you should find **Micromax 9000** listed under _Create a connection for this mobile broadband device_ >> click Forward

3. Select India under _Choose your Provider's Country_  >> click Forward

4. Select _I can't find my provider and I wish to enter it manually:_ and Enter "Bsnl" in the name field  >> click Forward

5. Enter **bsnlnet** under the Selected plan APN (Access Point Name)  >> click Forward

6. Hit Apply which will automatically open the _Editing Bsnl Connection 1_ window

7. Under _basic_ select the number to be dialled as *99***1# & Check mark _Available to all users_ in the same Window. Leave all else Blank & hit Apply.

8. Enter your password again in the Authentication window to complete the Creation of your Connection.

9. click "Close" to close the "Network Connections Window"

10. Click the Network Icon next to Speaker in the Top Bar and select Bsnl Connection 1 created above & it should connect if all was done as advised,

Regards,
Ravi.

---

### Post by pankaj143gupta on 2010-04-03
.

---

### Post by abhi3pathi on 2010-04-16
i downloaded usbswitch and after that it shows blue light but it is not showing any network in at the top adjacent to speaker sign nor it shows in edit conection ->mobile broadband menu.can any one tell me what to do to connect through my micromax mmx372g device.
plz help

---

### Post by dineshs on 2010-04-17
[http://ubuntuforums.org/showthread.php?t=1439356](http://ubuntuforums.org/showthread.php?t=1439356)

---

### Post by rushikesh988 on 2010-08-01
> 
# D-Link DWM-162-U5, Micromax MMX 300c
#
# Contributor: Zhang Le

;DefaultVendor= 0x05c6
;DefaultProduct= 0x2001

;TargetVendor= 0x1e0e
;TargetProductList="ce16,cefe"

;MessageContent="5553424312345678000000000000061b0 00000020000000000000000000000"

;NeedResponse=1 


where can I generate the code like this for my 200G modem ???

USB MODE SWITCH IS NOT WORKING WITH MY MMX 200G MODEM

---

### Post by pdc on 2010-08-02
OK

join the usb_modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

seek help directly there

---

