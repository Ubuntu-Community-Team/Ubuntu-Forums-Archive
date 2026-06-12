---
title: "How to configure Broadband internet (Nokia CS-1x)"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by dmendizabal on 2010-01-16
This is a simple explanation for the ones who are trying to connect to the internet using a broadband modem. Even though my experience is with the Nokia CS-10 in Kubuntu/Ubuntu, it might be useful for other brands and/or models.

1.The Nokia CS-10 is recognized as a CD-ROM by the system. In order to change this status, you need to simply eject the CD-ROM. Once it is done, the modem will be recognized and a red light will turn on in the device during the initialization and finally you will have a flashing green light. 
At this point the modem is recognized, but there is no data transfer as yet. You will also notice that the KNetworkManager icon has changed into a phone confirming the existence of this device.

2.In case that you need for the system to detect the modem without this tricky help. There is a driver from Nokia support page to install the required configuration and rules to make the modem being detected as a modem when you just plug it in.
Unfortunately, the DEB version of this package has a problem with the postinst and postrm scripts:
The script comes with the following instruction:

**udevadm control reload_rules**

Which should be as follows:

**udevadm control --reload-rules**

I have made the change already for both misspellings and I'm attaching the corrected DEB file for your convenience.

3.I've tried to use the KNetworkManager/NetworkManager by creating a connection with all the information of the provider, but everytime I click on this connection, it doesn't seems to do anything. No attempt to dial and register with the server. Therefore I have opted to make the connection with a more basic tool: wvdial.

4.Install wvdial in your computer in case it is not installed as yet.

5.Execute **sudo wvdialconf** to read the basic information from the modem including the speed and it will be writen in the /etc/wvdial.conf file.

6.You need to add the rest of the parameters to this file including the APN, username and password. 
In my case the file looks like this:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
[color=red]Init3 = AT+CGDCONT=1,"IP","internet.ideasclaro.com.jm"[/color]
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
[color=red]Phone = *99***1#
Password = claro
Username = claro[/color]

Where the lines in red are the ones I had to add after the generation of the file by wvdialconf

7. The modems created by pluging in the Nokia CS-10 are /dev/ttyACM0 and /dev/ttyACM1. In order to iniciate the connection execute **sudo wvdial** in the terminal. It will read all the configuration parameters from the file above. Do not close this window to be able to finalize the connection when you are done.

8. Once you are done with the internet, press Ctrl-C inside the terminal to finish the wvdial sesion. Finally,  the ttyACM0 and ttyACM1 files will be removed from /dev once the modem is unpluged.
In case they are not removed (after the modem was unpluged) for any reason, you need to remove these files manually. Because in other case, the next time that you plug in the modem, it will create ttyACM2 and ttyACM3 instead and the wvdial won't work since as you remember it has been configured (in wvdial.conf) to connect through ttyACM0.

I hope this is useful for any of you and let's hope that the developers for KNetworkManager/NetworkManager improve this applet for a next Kubuntu/Ubuntu edition.

---

### Post by pdc on 2010-01-17
great work; thanks for this; this will be very useful to folks

looks like it is this device

[http://europe.nokia.com/find-products/accessories/all-accessories/home-and-office/imaging/nokia-internet-stick-cs-10](http://europe.nokia.com/find-products/accessories/all-accessories/home-and-office/imaging/nokia-internet-stick-cs-10)

a mobile broadband stick

out of interest what do you get with 

> lsusb

before and after the "eject" command is issued?

George Vitas advised me recently on creating udev rules to automate this "eject" command for ZTE modems, in post #104

[http://fostergrant.ubuntuforums.org/showthread.php?t=1147685&page=11](http://fostergrant.ubuntuforums.org/showthread.php?t=1147685&page=11)

---

### Post by pdc on 2010-01-17
instead of the eject command, some folks use usb_modeswitch;

I see in the usb_modeswitch.conf file there is one entry for a Nokia CS-15

> # Nokia CS-15
#
# Contributor: Antti Turunen

;DefaultVendor=  0x0421
;DefaultProduct= 0x0610

;TargetVendor=   0x0421
;TargetProduct=  0x0612

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="5553424312345678000000000000061b000000020000000000000000000000"


so your lsusb may well be 0421:0610

---

### Post by dmendizabal on 2010-01-17
lsusb gives me: 0421:060e

I don't use eject because the device doesn't seem to support this command.

---

### Post by pdc on 2010-01-17
thanks for this;

---

### Post by coc_21 on 2010-05-01
the deb file doesnt work on 10.04. The installation process starts then its starts another process then gives me the error which state I have to close the previous installer window.

Any ideas ???

---

