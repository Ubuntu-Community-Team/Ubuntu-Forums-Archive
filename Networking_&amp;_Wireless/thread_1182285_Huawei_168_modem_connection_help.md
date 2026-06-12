---
title: "Huawei 168 modem connection help"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by coyotepod on 2009-06-08
Has anyone tried connecting with a Huawei EC168? I have an Alltel plan (U.S.). I've tried using network manager and wvdial. I've taken suggestions about other Huawei cards, but have not found any post on my specific usb card.

The network manager shows a Huawei Technologies Huawei Mobile device so its at least recognizing it, and *lssub* shows:

Bus 002 Device 012: ID 12d1:1413 Huawei Technologies Co., Ltd. 


my wvdial.conf file

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Stupid Mode = 1
New PPPD = yes
ISDN = 0
Modem = /dev/ttyUSB0
Baud = 460800
Phone = #777
Username = [email]231xxxxxxx@alltel.net[/email] <- I use an actual number here
Password = alltel


Running Ubuntu 9.04 64-bit version

Any suggestions? I've got 14 more days to try it out! :-)

---

### Post by coyotepod on 2009-06-09
More info...

ls /dev/ttyUSB*

results:
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3  /dev/ttyUSB4

ls /dev/ttyU* /dev/ttyS* /dev/ttyA*

results:
/dev/ttyACM0  /dev/ttyS1  /dev/ttyS3    /dev/ttyUSB1  /dev/ttyUSB3
/dev/ttyS0    /dev/ttyS2  /dev/ttyUSB0  /dev/ttyUSB2  /dev/ttyUSB4

---

### Post by GeorgeVita on 2009-06-09
Hi **coyotepod**,

> /dev/**ttyACM0** /dev/ttyS1 /dev/ttyS3 **/dev/ttyUSB1** **/dev/ttyUSB3**
/dev/ttyS0 /dev/ttyS2 **/dev/ttyUSB0** **/dev/ttyUSB2** **/dev/ttyUSB4**

from above you must determine which port is your modem! Usually a Huawei modem uses /dev/ttyUSB0 and/or /dev/ttyUSB1 to connect. If a program "holds" a port and you remove/reinsert the modem all ttyUSBx numbering is shifted and the previous detected is not usable.

Try booting without the modem, attach it and then look at terminal command: **dmesg** (last lines) to see any note regarding the **/tty...** port attached for GSM communications. You can check also with **lsusb** before and after attaching the modem. For your tests it is better to remove any other serial communicated device from USB ports, and add it later.

Also what is the output of **sudo wvdial**? When you delete all Mobile Connections from the Network Manager icon and attach the modem, is it detected automatically starting the setup wizard? If yes, trying to connect what is the result?

Regards,
George

---

### Post by coyotepod on 2009-06-09
Connected with Huawei 168 using wvdial! 
I changed my wvdial.conf slightly; stupid mode=yes

However, I think the real reason it finally connected was I connected to the net on Windoze machine at work -- shh dont tell the tech guys -- by installing and using the Alltel QuickLink Mobile software. It asked me to activate. Obviously it had not been activated. If the guy at the store would have activated, it probably would've connected before using wvdial. I thought it was connecting then quickly disconnecting like some type of authentication issue.

Tangent -- 2 bummers. The new speed of these cards is supposed to be 3 mbs with recent network upgrades, but mine is only getting 200-350 kbs and that was in an urban area. That's about the same as my tethered cell phone I was using before. Tethered phones are $25 vs $60/month for a dedicated card. I was told the card would also have a more reliable connection in my very rural home area, but again seems to be about the same.

---

### Post by coyotepod on 2009-06-10
I had to restart for my network manager connections changes to take affect, now it works too. My wife will be happy she does not have to type those "stupid computer codes" to get online now :-)

---

### Post by Riaku on 2009-07-18
How do you figure out your username and pass? I have one as well.

---

