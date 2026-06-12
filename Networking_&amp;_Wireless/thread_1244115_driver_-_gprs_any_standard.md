---
title: "driver - gprs? any standard?"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by rolfi on 2009-08-19
Hallo,
I am from Germany, right now travalling in India and like to use a mobile internet-connection (probably Reliance with prepaid option) in India with Ubuntu 8.04 with a USB-Stick (receiver/transmitter).
I saw already some threads concerning this but each ist to special. It was hard to find a shop offering this and the man in the shop said bring the laptop. So I like to make shure that I have a working driver for the stick. Possible ? 
I am beginner with Ubuntu so I am thankful for an easy way :)

---

### Post by scorp123 on 2009-08-19
> **rolfi said:**
>  So I like to make shure that I have a working driver for the stick All "drivers" (which are called 'kernel modules' here; "drivers" is Windows-speak) are already in the Kernel.

What I'd suggest:
- start Ubuntu
- log in
- open a terminal (Applications > Accessories > Terminal)
- once the terminal is open, plug in the USB stick
- it should start blinking and/or show other reactions
- once this is happening type this into the terminal:  **dmesg**

That should spit out a truckload of information, but only really the last few lines matter. If it says something about "Modem detected." or something about "USB to serial adapter" then you have already won.

All that's left is go to the NetworkManager icon and define a "Wireless Broadband" connection. That's it. No driver installation needed ... at least for most adapters.

Some adapters have a dual function: When you first plug them in they will act as "virtual CD-ROM" drive that contains the Windows and/or Apple Mac drivers. Under Linux this makes no sense as we don't need those drivers. So to have the USB stick behave as a modem again it's enough if you simply click "Eject" on that virtual CD-ROM drive. That will send a signal to the modem and it will change its mode from "virtual CD-ROM" into the modem --- the part we're actually interested in.

My own stick -- a Novatel Wireless MC950D -- behaves like this. So to get the modem working I first have to "Eject" the virtual CD-ROM part, but after that it works tip top.

BTW, if you go and buy such a USB stick: I'd recommend you go for **Novatel** or **Huawei** ... These two brands are known to work tip top on Linux and no matter what model you end up with it should be easy if you have one of those modems.

---

### Post by rolfi on 2009-08-22
Thanks a lot for answering.
I encountered the problem of coverage in India with these sticks or data cards.
I live in the hills. Maybe I have to do it with a mobile phone.

---

### Post by NoelHC on 2009-09-15
Question for Scorp123
I have a Novatel MC950D modem, it does show up as a CD ROM drive but when I try eject it, I get a message Unable to mount media, There is probably no media in the drive.
 
This modem does have the Windows ZeroCD program that loads the MobilLink software.
I ran dmesg on the terminal as you suggested, It appears it tried v0.7.2 USB driver for GSM modems, scanned the device, and decided it was a Novatel Mass Storage CD-ROM
Any help in getting the ZeroCD shut down would be appreciated.
 
Noel

---

