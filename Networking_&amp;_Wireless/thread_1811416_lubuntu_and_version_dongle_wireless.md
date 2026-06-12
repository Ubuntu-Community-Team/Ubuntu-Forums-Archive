---
title: "lubuntu and version dongle wireless"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by naylor on 2011-07-24
hi all,
im going over to my sons house this coming weekend to install lubuntu.
he currently has xp installed on a 120 gig hd.
he has verison wireless with a usb dongle and im wondering what i need to do to get lubuntu to recofnize his wireless?
what info do you need to help?
thanks,
N

---

### Post by naylor on 2011-07-29
hi all,
tried to install Lbuntu and no internet connection.
using sprint wireless 'dongle'.
to use sprint with xp i must double click the sprint icon and wait till it pops up, then cick connect.
maybe if i could set sprint to autoconnect i could get farther?
how would i set it to connect automatically? i think if it auto connects then i can search for drivers in Lububtu?
sprint wireless
model: u301
sku rec301dox1
thanks,
naylor

---

### Post by naylor on 2011-07-31
i would like to thank all who helped.
i have deleted the lubuntu partion on my sons pc and ran 'fixmbr' so he is now back to W7. it took 3 yrs of bragging about ubuntu to get him to go for linux, what a waste of time!!
i have used ubuntu since 6.06 as my main system but i have deleted it from my main hd and my test hds. i am now using a linux that is not a derivative of ubuntu and there are many out there.
with a weeks heads up no one even asked what version of lubuntu i was going to install so from the beginning no one cared.
oh well life goes on...without ubuntu or any derivative of ubuntu!
after 4 hrs drive time and waiting 8 days to get an answer ive had enough!
to any mod who might just happen to read this, close this thread and delete my account ASAP!

---

### Post by pdc on 2011-08-02
sounds like you are really brassed off and upset that no-one helped you; and you were left alone

[http://lmgtfy.com/?q=ubuntu+sprint+wireless+model%3A+u301](http://lmgtfy.com/?q=ubuntu+sprint+wireless+model%3A+u301)

have a look at this

---

### Post by pdc on 2011-08-02
and as I have had a bit of spare time, I researched this a bit more;

a rather complicated device;

if Josh; moderator of the usb_modeswitch forum, thinks it is complicated ...

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=591&sid=6d7d69bd044f3399055385265eb50ab7](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=591&sid=6d7d69bd044f3399055385265eb50ab7)

see final post ....................

> yup. here is the steps to make sure things are well documented:

After you plug the Sprint / Novatel u301 in, you get two usb devices:

Bus 001 Device 062: ID 16d8:6008 CMOTECH Co., Ltd.
Bus 001 Device 058: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB

The device is in active CDMA / 3G mode when plugged in.

You also get four usb serial interfaces (option driver):
/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2
/dev/ttyUSB3

To make it enter 4G mode, you connect to one of the four serial ports (it seems to change, but /dev/ttyUSB1 seems most likely to accept AT commands on initial plugin)

You type atz to reset the at command terminal, and type ' at+4gmode=1 ' to enable the 4G chipset. After entering this the 4G light illuminates. You can also type ' at+4gmode=0 ' to disable the 4G chipset. I found the command by giving at&v which shows all the at registers, there are a few other AT 4G registers such as 4gusername/4gpswd.

After providing the AT command to enable the Beceem WiMAX device, a new USB device also becomes visible...

Bus 001 Device 066: ID 198f:0220 Beceem Communications Inc.
Bus 001 Device 065: ID 16d8:6008 CMOTECH Co., Ltd.
Bus 001 Device 063: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB

The 198f:0220 device is a standard Beceem WiMAX device that should work with the Beceem WiMAX driver in staging. It seems most likely that the at command simply triggers something to enable the power to the Beceem chipset.

The 16d8:6008 is the option CDMA device (Qualcom) with the serial interfaces.

The 1a40:0101 looks to be an internal usb hub connecting everything. It might be where the CD mass storage device shows up from as well.

Good luck!

---

