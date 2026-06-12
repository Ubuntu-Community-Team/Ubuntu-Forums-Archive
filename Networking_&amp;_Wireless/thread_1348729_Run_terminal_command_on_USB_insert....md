---
title: "Run terminal command on USB insert..."
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by kfish2oo2 on 2009-12-07
OK I wasn't sure exactly where to put this but this seemed like the best place considering my query involves a 3G USB dongle (Hauwei E1752 from o2)

Here goes: basically I want to run a command through the terminal every time the USB dongle is inserted. In order to connect I need to run the command

```
sudo usb_modeswitch
```

through the terminal so that Ubuntu will recognize the 3G capabilities of the dongle rather than seeing it as a storage device.

Is there any way to get this command to run every time the device is inserted?

---

### Post by puppywhacker on 2009-12-07
It used to be hotplug, but now replaced by udev. You have to create a rule for it, you can find the rules explained here

[http://www.draisberghof.de/usb_modeswitch/#automate](http://www.draisberghof.de/usb_modeswitch/#automate)

[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/424050](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/424050)

it will look something like this:
```
/etc/udev/rules.d/80-huawei-e1752.rules
SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"

```

---

### Post by kfish2oo2 on 2009-12-08
So I made a rule in the udev rules.d folder 
```
BUS=="usb", SYSFS{idProduct}=="12d1", SYSFS{idVendor}=="1146",
ACTION=="add", RUN+="/usr/sbin/usb_modeswitch"
```

12d1:1146 is the address of the device when its being read only as a SD Storage device under lsusb, so I assume that part of the rule is right, and I did find a file called usb_modeswitch at the address /usr/sbin/ so that looks right too... but it just doesn't seem to work. I still have to run usb_modeswitch through the terminal in order for the dongle to switch from storage mode to modem mode.

Whats more is that 9 times out of 10, I have to create a new connection through the connection wizard to connect to the net once the device *is* being read as a 3G modem.

Final thing: when I connect to the net through the dongle, and then connect to my wlan (which is set up solely for file sharing, not wireless internet), firefox and opera decide that I'm no longer connected to the web. A minor annoyance, but is there any way to fix that so that I can have both connections running without issue?

---

### Post by puppywhacker on 2009-12-09
Hi,

you swapped the vendor-id 12d1 and the product-id 1446 so I guess that is why it doesn't work, otherwise unplug and replug the device for hotplugging to work, I never had much luck when I booted with the stick plugged in (different model, same principle)

[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
```
12d1  Huawei Technologies Co., Ltd.
	1001  E620 USB Modem
	1003  E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
	1009  U120
	140b  EC1260 Wireless Data Modem HSD USB Card
	1446  E1552 (HSPA modem)

```

The 9 out of 10 times is just annoying, and I do not think very highly of these USB sticks. They seem to be cheap and rubbish. I used vodafone mobile connect, which seems to soften the blow of using the stick. Where vodafone is the sponsor of the project, so it will work for other operators as well.

When you connect to your WLAN after you have connected to UMTS the default gateway is overwritten. In the Network Manager there should be some switch at some advanced routing page that says "use this connection (or route) only locally" ... (sorry for just guessing the words here) ... this will prevent the wlan connection to override the default gateway as soon as it is enabled.

---

### Post by kfish2oo2 on 2009-12-09
OK so I edited the usb_modeswitch.rules using the other Huawei product templates so the rule now reads:

```
# Huawei E1752
#
# Contributor:
# choose one of these:
# Vendor:Product id = 0x12d1:0x1446
SUBSYSTEM=="usb", SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="1446", RUN+="/usr/sbin/usb_modeswitch --default-vendor 0x12d1 --default-product 0x1446 --detach-storage-only "
```

But that still doesn't work. When the dongle is in storage mode its vendor-product ID is 12d1:1446 and when its in 3G mode its 12d1:1001. I've tried both 1446 and 1001 as the idProduct value and no joy. Also, when its in 3G mode lsusb reads it as an E620.

Unfortunately this annoying dongle is the only way I have of connecting to the web, and the way things stand it takes at a minimum 5 minutes just to get online, and I need reliable access to the web for college.

Really appreciate the help so far guys

---

### Post by puppywhacker on 2009-12-09
I tested again with my ZTE K3565-Z which should function roughly the same. I had to experiment and reboot, and plug the stick out long enough for it to forget the weird states it was in.

The rule that worked for me is this one, which gets me out of the ZeroCD product=id 0x2000 into the proper 0x0063 mode. So I use the -v and -p not the --default-vendor, and I need a message sequence to get it to start moving and I don't know what the -R does.

I haven't found any message sequences for your stick, but maybe you will need one too.

```
SUBSYSTEM=="usb", SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/sbin/usb_modeswitch -v 0x19d2 -p 0x2000 -M 5553424312345678000000000000061b000000020000000000000000000000 -R 1"
```

Anyway, goodluck, there is not much else I can do for you :(

---

