---
title: "dialup"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by ata_kamyabi on 2009-07-20
hello any one
i am a new ubuntu user. ia dont now how to connect to internet via dialup connection. it seems that OS does not know may modem. i use scanmodem and pppconfig but i can not connect to internet might i dont know how to use them correctly. does any one help me?
thanks:confused:

---

### Post by komputes on 2009-07-20
hi ata_kamyabi,

Just to give you an overview of modems in linux I will explain a few things that may help you understand if you can use your modem to connect to the internet using ubuntu.

You have two different types of modem, hardware and software modems; hardware modems have a chip that demodulates sounds into binary data where as software modems (or softmodems, winmodems, usually on-board a laptop) use software to demodulate the sound, and the modem is simply used as an extension of the sound subsystem. The challenge with software modems is that many are proprietary (with demodulation driver/software only made available for windows. 

Now some modems do have drivers written for them, and some are available for purchase. For example, I often see Conexant modems, there is a possibility of purchasing drivers for these from [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) or getting the free throttled version. For other software modems you can check out [http://www.linmodems.org/](http://www.linmodems.org/). 

My problem is that these sites and drivers do not always work and modules usually need to be recompiled for each kernel (every time you get a kernel update, you can lose modem support). These sites just gather experiences and driver development for modems but there has never been a good infrastructure for Linux modem support and since many developers using the internet today use high speed internet, they usually mitigate the importance of modem support. Besides that, I have been told that writing modem drivers is not the simplest thing in the world. Recently it even seems that NetworkManager, the central utility for network configuration gave up dialup support. For all these reasons, we do not have a good modem infrastructure at this time. I feel that this is not helping people in developing countries that do not have bradband infrastructure but still have access to a telephone line.

I would recommend that if your computer has a serial port, that you get a hardware serial modem (these rarely fail as no software is needed). You can then install the package gnome-ppp and point it to the modem device /dev/ttys0 after that it's pretty simple, just enter the number, login and password.

If you do have a software modem, archive and upload the files that the scanmodem script outputs. For more info on modems you can check out:

Scanmodem Instructions:
[https://help.ubuntu.com/8.04/internet/C/modem-identify.html](https://help.ubuntu.com/8.04/internet/C/modem-identify.html)

Dialup modem howto:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by varun1786 on 2009-07-20
Is it a usb modem. If it is disconnect your modem wait for a few seconds then reconnect it.
Open a Terminal ( Applications -> Accessories -> Terminal)
Then type the following commands

$lsusb 

$dmesg | tail

post the output of the commands an i'll try an help you

---

