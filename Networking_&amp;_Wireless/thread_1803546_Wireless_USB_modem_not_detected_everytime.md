---
title: "Wireless USB modem not detected everytime"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by rakeshchhikara on 2011-07-13
Hi

I am using Ubuntu 11.04 and a Huawei USB modem to connect to internet. Most of the time when I start computer it is not detected my system. 
Then I use to reboot and then it gets detected automatically. That means its drivers are now loaded.
But I don't know why drivers are not loaded when I start first time.

Please tell me solution for this so that I wouldn't need reboot again & again every time.

Thanks in advance.

---

### Post by rakeshchhikara on 2011-07-15
Any one please help...

---

### Post by Alok.Karnik on 2011-10-18
Same happens with me! Help needed!

---

### Post by mrgoodfox on 2011-10-18
Mine doesnt recognize any of my USB wireless adapters. EVER

---

### Post by gcoram on 2011-10-18
Im finding that if I boot with usb modem plugged in it does not show up on the network menu.
If I pull it out and put it back in dmesg has all the right output but still no entry in menu.
If I reboot with the modem not plugged in and wait for it to finish boot up then plug in the modem all is well.

---

### Post by mrgoodfox on 2011-10-18
That doesnt work for me at all. Im baffled at how complicated this is

---

### Post by pdc on 2011-10-18
come on chaps;(or chapesses)

we have three folks all getting distressed; 

all clamouring for attention ....

how to help each ...

if you type 

> lsusb

in a terminal, and copy and paste the result back

at least folks can know what device you have;

---

### Post by reptilezone2002 on 2011-10-19
> **rakeshchhikara said:**
> Hi

I am using Ubuntu 11.04 and a Huawei USB modem to connect to internet. Most of the time when I start computer it is not detected my system. 
Then I use to reboot and then it gets detected automatically. That means its drivers are now loaded.
But I don't know why drivers are not loaded when I start first time.

Please tell me solution for this so that I wouldn't need reboot again & again every time.

Thanks in advance.

same happens to me u restart few times then it works

---

### Post by gcoram on 2011-10-19
using fully upgraded ocelot.

my problem doesnt seem quite as serious as the others but since it is annoying and no one else is responding to pdc I'll have a go.
 
lsusb reports
Bus 002 Device 011: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

It is actually a E169 from virgin. but once I get the menu option it works great.

lsmod
> option                 25477  0 
> usb_wwan               20491  1 option
> usbserial              47107  2 option,usb_wwan
> usb_storage            57901  0 
> uas                    18027  0 

these seems to self install upon plugging the device in.

rmmod option usb_wwan usbserial
and they are gone.
plug in device they are back.

yet nowhere to be seen in network menu no mobile broadband entry at all.

---

### Post by mrgoodfox on 2011-10-19
Here is "lsub" on mine:

```


Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0411:0148 MelCo., Inc. Buffalo WLI-UC-G300HP Wireless LAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 17ef:480c Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm using a [Buffalo G300HP]("http://www.buffalotech.com/products/wireless/client-adapters/airstation-highpower-n300-compact-usb-20-wireless-adapter-wli-uc-g300hp/")

---

### Post by pdc on 2011-10-19
........well mrgoodfox.......

......your device is designed to pick up a wifi signal from a nearby wifi router......

......the thread that you have inserted your comment into..

....is all about mobile broadband devices........

......which are different........(they pick up signals from phone companies.........)

......sort of like......some cars run on petrol ....and some on diesel........... and the two are different...

so mrgoodfox.......

seems like you need the Ralink rt2800 driver; in fact rt2800usb

your device is mentioned on this page

[http://cateee.net/lkddb/web-lkddb/RT2800USB.html](http://cateee.net/lkddb/web-lkddb/RT2800USB.html)

but if you can post as much of the information as possible from here

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

folks will I am sure do their best to help you; if fact:

best start a new thread yourself; then you get more attention

.....I think there is already a driver for your device; I suspect you need to blacklist a very similar driver that may be competing......I am sure folks can help you .......

---

### Post by mrgoodfox on 2011-10-19
Thanks a lot. I'll go ahead and do that just now. 

This forum is definitely the most useful I've ever been a member of. Hopefully sometime (soon) i'll learn enough to start helping others too.

---

### Post by pdc on 2011-10-19
.........I was suggesting you start a new thread......

.....I saw you started a thread two days ago on another part of the ubuntu forum......

....it is now moved across to network .....so check it out..

praesodym from Berlin has posted: he is very good and should sort things for you quickly; we leave it to him!

---

### Post by mrgoodfox on 2011-10-28
I finally found the solution. I thought to post it on this thread too in case others are having the same issue.

When typing "***rfkill list***", I was getting the following results:

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: ye

```

Which apparently they both should be set to "No". So my wireless was really disabled and not working and it had nothing to do with the wireless card.

I had to type the following command to enable it and everything was working.

```

rfkill unblock wifi

```

---

### Post by roopeshmicasa on 2011-11-02
Hello guys.......
I faced the same problem with my ZTE AC2746 modem.
The problem is that when I start my computer with device connected it does not recognize it as the modem and is detected as a storage device. What required was to first pull out my device and then had to plug in, if lucky, it is detected as the modem and if it is again not recognized as modem I was left with no choice but had to restart the system with the hope that next time it is detected as the modem. 

The problem is that with the device connected it is not recognized as a modem but rather is detected as the mass storage device in the system. 
Here is some solutions which might help you guys....

try which ever works for you....

First solution
Don't start the system with the device connected. First boot the system with no device and when the system has started the session plug in the device and wait for 2-3 minute. If it is detected as modem then go for this procedure every time you wish to connect to the networking

Second solution 
If above thing doesn't work then install usb-mode switch from synaptic package manger and hope that this time the device is connected as a modem.


Third solution (recommend only when above thing doesn't works)
open gedit and type the following given below
-----------------------------------------------------------------------
  
ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/sbin/rmmod usb_storage"

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"


---------------------------------------------------------------------
Save this file as etc/udev/rules.d/15-zte-ac2746.rules (this path is good under ubuntu)
Reboot the system once done.
Hope that this time it is connected as the modem.

If all the three procedure doesn't work then please forgive me because I am not such a good technician :):(:)

hope this helps,
good luck

---

### Post by floridamaths on 2012-03-03
Same problem also with Huawei modem. Doesn't seem to be much interest from Ubuntu/Canonical  to solve what cannot be that big a problem. If usb modem is detected when you unplug/plug the thing, why not on startup ?? Mode switch stuff is old hat problem that was dealt with previously - maybe they've forgotten to include that 'fix' ??

---

