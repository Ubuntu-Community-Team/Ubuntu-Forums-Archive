---
title: "How to setup ZTE AC8700 EVDO on Ubuntu"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by ramnarayan on 2009-11-06
Hi

Just laid my hands on a 3G ! ZTE AC8700 EVDO data card from BSNL (service provider in India)

I thought it would be simple to setup and run but ran into snags.

Checked the net but there are bug reports but no real nice how to's

The resources available are from BSNL (surprise surprise) but not good enough
[http://www.bsnlevdo.in/evdo/setup-bsnl-evdo-usb-modem-in-linux/](http://www.bsnlevdo.in/evdo/setup-bsnl-evdo-usb-modem-in-linux/)
 and from
[http://satish.playdrupal.com/?q=node/41](http://satish.playdrupal.com/?q=node/41)

there are some solutions at [http://ubuntuforums.org/showthread.php?t=942873](http://ubuntuforums.org/showthread.php?t=942873)

but am not sure my problem in entirely the same.
***
I tried the following
1. Inserted the device and this is the dmesg (snipped to relevant sections only)

[   76.817632] usbserial: USB Serial Driver core
[   76.834853] usbserial: USB Serial support registered for GSM modem (1-port)
[   76.835493] option 1-2:1.0: GSM modem (1-port) converter detected
[   76.836178] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[   76.836748] option 1-2:1.1: GSM modem (1-port) converter detected
[   76.837360] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[   76.837916] option 1-2:1.2: GSM modem (1-port) converter detected
[   76.838480] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[   76.839034] option 1-2:1.3: GSM modem (1-port) converter detected
[   76.839593] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[   76.840143] usbcore: registered new interface driver option
[   76.840147] option: USB Driver for GSM modems: v0.7.2

Here the question is why is it showing up as a GSm modem ??

lsusb
Bus 001 Device 010: ID 19d2:fffe

lsusb -v (snipped)

Bus 001 Device 010: ID 19d2:fffe
Device Descriptor:
 bLength                18
 bDescriptorType         1
 bcdUSB               1.10
 bDeviceClass            0 (Defined at Interface level)
 bDeviceSubClass         0
 bDeviceProtocol         0
 bMaxPacketSize0        64
 idVendor           0x19d2
 idProduct          0xfffe
 bcdDevice            0.00
 iManufacturer           1 ZTE, Incorporated
 iProduct                2 ZTE CDMA Tech
 iSerial                 0

this is my wvdial.conf
[Dialer m0]
# New 3g GSM CDMA device
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = xxxxx (phone number)
Password = xxxxx (phone number as above)
Phone = #777
Stupid Mode = 1
# Inherits = Modem0
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap
nobsdcomp nodeflate

results of wvdial
$ sudo wvdial m0
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.

***
my OS is Ubuntu 8.10 with kernel as below
 uname -a
Linux ram-laptop 2.6.27-15-generic #1 SMP Tue Oct 20 06:52:09 UTC 2009
i686 GNU/Linux

***
any idea what i need to do set up this device, *will be very grateful*

ram

---

### Post by ramnarayan on 2009-11-11
Hi

Seems like Ubuntu was all ok and the problem was at the service providers end. THis has now been rectified and the device simply "Just works"

though am using it through wvdial rather than network manager since there is a bug in the network manager.

regards
ram

---

### Post by Satbirsoni on 2010-05-02
Hi 

I have same modem ZTE AC8700 in Bangalore , i am struggling to setup it with ubuntu 
9.04 and thn 10.04.

i am getting Below on lusb

```
#lsusb

Bus 005 Device 003: ID 19d2:fffe ONDA Communication S.p.A
```
on wvdialConf

i am getting message "Sorry No Modem was Detected"


wanted to give last try to 8.04 , Could you please provide me steps/snapshot to configure it.

Also does EVDO gives better performance with Linux thn windows..?

Thanks in Advance 

Satbir Singh

---

### Post by pdc on 2010-05-02
if you plug the modem in 

and type (or copy and paste) this into a terminal

> dmesg | grep tty

and tell us what you get: *we are hoping to see ttyUSB0 and ttyUSB1 etc *

---

### Post by dalfish on 2010-05-02
first you have ascertain where the device is. Then try with the network manager applet. Also hal is removed from ubuntu karmickola. Lucid also is devoid of hal. They use devicekit instead. it is not as effective as hal. Hal detects your device. Device kit. i tried  to connect my ISP is BSNL and modem huawei modem in karmic and lucid. there was an auto cdma option in network applet prior to karmic koala. From karmic this is absent Hence cannot connect to the internet. You can try auto cdma option if you are using jaunty or ubuntu 8.10. If you want to change the OS I would recommend PCLOS. Such devices works flawlessly in PCLOS KDE version using the KPPP It is up to you to decide.but frist Try with Ubuntu ALL THE BEST

---

### Post by alexfish on 2010-05-02
[http://en.wikipedia.org/wiki/DeviceKit](http://en.wikipedia.org/wiki/DeviceKit)

Also of note the device has been recognised : the device is on 

Ports
ttyUSB0
ttyUSB1
ttyUSB2
ttyUSB3


the problem here is to hope the Modem Manager will pick the **correct control Port**. if it is failing I suggest using Gnomeppp or wvdial , Then **force the connection to use one of the ports listed**
one of the problems is the enumeration of the device ESP; if the modem is capable of 3g and cdma   The enumeration from the modem manager 

The enumeration from the modem manager 
                                 **MM_MODEM_TYPE**

 MM_MODEM_TYPE_GSM = 1     A GSM device.    
MM_MODEM_TYPE_CDMA = 2     A CDMA device.       

regards

alexfish

---

