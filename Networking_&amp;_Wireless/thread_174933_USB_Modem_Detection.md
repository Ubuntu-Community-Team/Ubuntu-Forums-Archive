---
title: "USB Modem Detection"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by Arishy on 2006-05-12
I am using The Live version on P4 
Attached a USB 56K Softmoden. The system sees it. I went and "enabled" it
by clicking the check box. Tried auto detect it I get no detection.

I am new to Linux and I need handholding step by step to provide any info you need to let the system recognize it.

I have an Ethernet and ADSL through a router That goes very well I can get to the Inet. I need to enable the usb modem so I can send/recieve faxes.

Can you please help.

I know I did not provide you with enough DATA, but I hope we can do it together.
:confused:

---

### Post by Matchless on 2006-05-13
Hi,
  Go to "Official Wiki" at the top of the forum page and search for dialupmodemhowto That should put you on the road. USB modems are seen as winmodems and need drivers to be installed in Ubuntu and not all types and models can be made to work on linux. External modems on the other hand, that plug into a serial port, do not require any drivers and should work out of the box.
Good luck

---

### Post by Arishy on 2006-05-15
Well...I will definetly do that Thank you for the link...
But as I said earlier Linux sees the modem, the auto detect did not work. is there a "guru" way to test it on a command line before I do my research.

---

### Post by mesh2005 on 2006-05-15
My advice is don't waste your time with USB modems, I have Zoom 5510 USB, I posted many times , I spent more than a week trying to communicate with it but I failed although it is listed in the devices list detected at startup.
Really USB modems are annoying with Linux.

---

### Post by Arishy on 2006-05-15
You saved me a lot of Hassle....I thank you for that.
I will get com1 serial modem, Hayes will sure work,  and just dump this modem.

Purely academic question:

Can I attach text files in the forum, like for example ModemData.txt that came out of scanmodem tool.

The other one is to sort my confusion coming from windows. In windows if the modem is not recognized it means you need a driver (by the way windows xp saw the usb modem with NO DRIVER). Now in Linux the os SEES the modem which means no driver needed Why it is not detected That is my confusion

---

### Post by digitalaboriginal on 2006-05-17
[QUOTE=Arishy]
The other one is to sort my confusion coming from windows. In windows if the modem is not recognized it means you need a driver (by the way windows xp saw the usb modem with NO DRIVER). Now in Linux the os SEES the modem which means no driver needed Why it is not detected That is my confusion[/QUOTE]

Why would you think that Windows needs no driver? The way it works is that new hardware always comes with a driver disk. On the next release the hardware vendor gladly gives the driver to MS, so it is available for automatic install. 

Linux SEES the modem? how do you know? If you are using lsusb or /proc/.. it just means that the lowest levels of the usb stack have seen the new hardware. Linux still needs a driver (or class driver) to handle new devices.

Regards

---

### Post by Arishy on 2006-05-22
[QUOTE=digitalaboriginal]Why would you think that Windows needs no driver? The way it works is that new hardware always comes with a driver disk. On the next release the hardware vendor gladly gives the driver to MS, so it is available for automatic install. [/QUOTE]

My point here was the -ve part. Let me explain If I cannot see you I need a driver. If I see you I "have" your driver.

So, I thought; wrongly of course; If Linux sees me I do not need to provide a driver. 


[QUOTE=Linux SEES the modem? how do you know? If you are using lsusb or /proc/.. it just means that the lowest levels of the usb stack have seen the new hardware. Linux still needs a driver (or class driver) to handle new devices.

Regards[/QUOTE]

I can provide you with ALL the details and you can help me with installing the driver that I got for it from the Internet. BUT it means you stay with me until we do it ....I am new to Linux and I will not be able to do it alone. This one is not an easy assignment as you are surely aware.

If I do not hear from you I will follow the advice given to me earlier, and miss on a chance to get deeper with Linux.

---

