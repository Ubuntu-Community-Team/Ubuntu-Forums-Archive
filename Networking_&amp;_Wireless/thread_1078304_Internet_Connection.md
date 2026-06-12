---
title: "Internet Connection"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by herbjr on 2009-02-23
Hello Ubuntu Community! I am a new Ubuntu user. I dual boot my laptop with Windows XP and Ubuntu. I wanted to get use to using a linux based system so i choose to use Ubuntu for many of reasons. 

Anyway, I am here because i need support. My only source to the internet is my wireless card that connects to my ISP called XOHM. I have tried many things to get it to work but at the moment, no success. I wanted to know if anyone knew of a way I could make this work.

I attempted to install ndiswrapper to allow me to use the drivers and wine to allow me to run the connection manager but I could not successfully install neither of them (Wine or ndiswrapper). One of them said something about flex or something. It is also hard for me to get programs from the software manager because I can not refresh the list due to not having access to the internet. Therefor, i have to result to booting Windows XP, finding/downloading the files, then re-booting Ubuntu and installing them.

If anyone has any information that could help me, please let me know asap. I love Ubuntu already, but i can not use it if i can not connect to the internet :).

---

### Post by Iowan on 2009-02-23
Welcome aboard! [s]and thank you for choosing Ubuntu[/s] (sounds a bit too much like the help desk). What kind of wireless card?  (I don't yet use wireless, but *someone* here should be able to help.) Some other information that might be helpful can be optained from a terminal by typing **sudo iwconfig** and **lshw -C network**.

---

### Post by herbjr on 2009-02-23
Thank You. I am using a Mobile Broadband connection provided by the ISP called XOHM. The maker of the card is ZTE or so. I can get more information about the card if you want. Just let me know what you need.

---

### Post by Iowan on 2009-02-23
I don't see ZTE in the list of [supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer"), but I found a website for ZTE [Windows drivers]("http://www.driversupdated.com/exact/zte-corporation.php").

---

### Post by herbjr on 2009-02-24
Great!! Do you know how I can use those drivers on Ubuntu and then run the connection manager?

---

### Post by GeorgeVita on 2009-02-24
Hi **herbjr**,

I am using a ZTE MF636 modem with Ubuntu 8.04 on a Toshiba Satellite L30.

Open a terminal window and try the command: **lsusb**
Post here the results.

Try to find the exact model of your modem (like ZTE MF636). Ask your provider or send us a link with a photo of the device.

Also take a look at [http://ubuntuforums.org/showthread.php?t=1005910](http://ubuntuforums.org/showthread.php?t=1005910)

Regards,
George

---

### Post by herbjr on 2009-02-24
Here is the info from lsusb:
> 
Bus 005 Device 003: ID 04fc:0c15 Sunplus Technology Co., Ltd
Bus 005 Device 002: ID 19d2:0007  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


USB Card - "ZTE Tu25":
(Photo)
[[IMG]http://www.4ginfo.com/images/stories/4Ginfo_Xohm_USB.jpg[/IMG]]("http://www.4ginfo.com/index.php/Page-7.html")

(Information)
> 
**General**
[INDENT]    * Size: 3.15 in x 1.25 in x 0.43 in
    * Weight: 0.88 oz
    * Standards Compliance: Complies with Universal Serial Bus Revision 2.0 specifications, carries USB-IF logo
    * USB 2.0 standard provides maximum data transfer rates and works with most current and future laptops and desktops
    * Faster and more stable connectivity with two antennas and omni-directional capability
    * Indicator light shows status of connection[/INDENT]
**Environmental Specifications**
[INDENT]    * Operating Temperature: -10°C - +55°C (+14°F - +131°F)
    * Storage Temperature: -40°C - +70°C (-40°F - +158°F)
    * Humidity: 5% to 95% over operating temperature[/INDENT]
**Mechanical Specifications**
[INDENT]    * Dimensions (W x D x H): 80.3 mm × 35.2 mm × 11 mm
    * Weight: 2.0 oz
    * LED: Yes/li>
    * Antenna: Yes[/INDENT]
**Software Specifications**
[INDENT]    * WiMAX Standard: IEEE 802.16e-2005
    * WHQL: Yes[/INDENT]
**Hardware Specifications**
[INDENT]    * Interface Type: USB
    * Frequency Range: 2.496 GHz – 2.690 GHz
    * Current Consumption: Max. (Peak) 2.5W[/INDENT]


I tried posting all information needed. Source of information can be found [here]("http://www.4ginfo.com/index.php/Page-7.html") and by clicking the image.

---

### Post by GeorgeVita on 2009-02-26
Well, we know that you have a ZTE Tu25 4G (!) modem, which responds to **lsusb** as **19d2:0007**

Don't wait for the system to recognize it as a modem (as in most ZTE 3G modems).

Try the terminal command: **sudo modprobe usbserial vendor=0x19d2 product=0x0007**
(give your password when asked). This command will try to assign a communication port for your modem. Plug in the modem, wait 30 seconds and give the terminal command: **ls /dev/ttyU* /dev/ttyA* **
Post here the results.

---

### Post by herbjr on 2009-03-02
> **GeorgeVita said:**
> Well, we know that you have a ZTE Tu25 4G (!) modem, which responds to **lsusb** as **19d2:0007**

Don't wait for the system to recognize it as a modem (as in most ZTE 3G modems).

Try the terminal command: **sudo modprobe usbserial vendor=0x19d2 product=0x0007**
(give your password when asked). This command will try to assign a communication port for your modem. Plug in the modem, wait 30 seconds and give the terminal command: **ls /dev/ttyU* /dev/ttyA* **
Post here the results.
**/dev/ttyU* came out to be /dev/ttyUSB0**. /dev/ttyA* did not provide anything. Says no such file or dir.

---

### Post by GeorgeVita on 2009-03-02
Ok, now test the following:

-boot without the modem

-from terminal: **sudo modprobe usbserial vendor=0x19d2 product=0x0007**

-plug in the modem and look if the Network Manager 0.7 icon (2 PC screens UP-RIGHT on the top panel) shows any message like "a modem detected ...". If you see this message try to setup "mobile broadband" from this icon.

- if nothing happens try in terminal: **sudo wvdialconf**
(this command will try to find any modem scanning ports and we hope that /dev/ttyUSB0 is a real "modem" port! You can read more running: **man wvdialconf** from terminal)

- post here all output from terminal (left click and select with the mouse, right click and copy, paste here all text).

---

### Post by herbjr on 2009-03-03
Here you go:

```
Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem
Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?
Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
If you still have problems, send mail to <wvdial-list@lists.nit.ca>
```

---

### Post by GeorgeVita on 2009-03-04
... unfortunately as the /dev/ttyUSB0 cannot be used as a modem port, I cannot help any more.

If you see that nobody else gives a new idea here, try with a new thread with a more informative title like:
"Cannot use ZTE Tu25 4G broadband modem with Ubuntu 8.10"
on the same category "Networking & Wireless", stating the data you now have: **lsusb** reports it as **19d2:0007**
trying to **usbserial** it we found **/dev/ttyUSB0** but **wvdialconf** cannot use it as a modem port. Also Network Manager 0.7 cannot see it at all.

Good Luck!

---

