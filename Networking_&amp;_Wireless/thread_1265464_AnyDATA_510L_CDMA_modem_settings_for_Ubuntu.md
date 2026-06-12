---
title: "AnyDATA 510L CDMA modem settings for Ubuntu"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by olalaaa on 2009-09-13
Very short, here are the lines to run in terminal :

Open a terminal ( you find it at Applications >> Accessories >> Terminal ) and run :

```
lsusb
```you will see a list, and there appears the usb storage device ( **ID 05c6:1000 Qualcomm, Inc.**)

```
cd /home/myusername/.apps/usb_modeswitch-1.0.5
``````
sudo ./usb_modeswitch -v 05c6 -p 1000 -M 5553424312345678000000000000061b000000020000000000000000000000 -m 0x08

```( this removes the usb-storage driver from your device ).

In my computer, I installed the usb_modeswitch in a new invisible folder called .apps created by me. You will just make "cd" in your folder where you have the usd_modeswitch installed.

```
sudo modprobe usbserial vendor=0x16d5 product=0x6502
```( this makes the device to be seen as serial instead of storage device )

```
lsusb
```this shows you again the list, where the Qualcomm device ID changed into something new, as we need it to happen : ( **ID 16d5:6502** )

```
dmesg
```this shows that we have usbserial there, and a modem is located at ttyUSB0, 1, and 2.

ONLY first time we must run also this line (which installs GSM "option" type modem instead of a mere "generic" modem (after first time, we are not required to run again that command, because the option drivers will already be there where we need them)

Next time when you plug and switch the modem, you don't need that line, only those above. It will start in "option" mode. ("Switching" is this procedure above, from storage to serial mode).

The one-time command is this :

```
sudo modprobe -v option
```followed by 

```
dmesg
```to see that indeed we can see that "option" mode is loaded.

That's it.

More details here : [http://clicknet-mobile-linux.blogspot.com]("http://clicknet-mobile-linux.blogspot.com/2009/09/anydata-510l-cdma-modem-settings-for.html")

---

