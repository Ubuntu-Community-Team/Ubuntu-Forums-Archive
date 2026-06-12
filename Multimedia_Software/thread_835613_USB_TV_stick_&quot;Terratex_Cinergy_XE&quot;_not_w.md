---
title: "USB TV stick &quot;Terratex Cinergy XE&quot; not working"
date: 2008-06-20
forum: Multimedia Software
---

### Post by roy.nico on 2008-06-20
Hi everybody.

I'm trying to get working, on my Ubundtu Hardy, a Digital TV USB 
 stick : "Terratec T Cinergy XE". I know there exist 2 versions, supported under linux by two different drivers. I think i have the rev2, because of the following :
```

$ lsusb -v

Bus 004 Device 002: ID 0ccd:0069 TerraTec Electronic GmbH 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0ccd TerraTec Electronic GmbH
  idProduct          0x0069 
  bcdDevice            2.00
  iManufacturer           1 TerraTec
  iProduct                2 Cinergy T USB XE Ver.2
  iSerial                 3 10012007

... 

```
I followed the (in Spanish) tutorial [HTML] http://www.ubuntu-es.org/index.php?q=node/76680 [/HTML] and installed :
* the driver (module) dvb-usb-af9015
* the firmware dvb-usb-af9015.fw

Something is working, when i plug the stick in, i can see : 
```

$ dmesg 
    526.867432] usb 3-6: new high speed USB device using ehci_hcd and address 3
    [  526.935499] usb 3-6: configuration #1 chosen from 1 choice
    [  526.935751] af9015_usb_probe: interface:0
    [  526.941247] af9015_read_config: IR mode:0
    [  526.942476] af9015_read_config: TS mode:0
    [  526.943884] af9015_read_config: [0] xtal:2 set adc_clock:28000
    [  526.945966] af9015_read_config: [0] IF1:36167
    [  526.948044] af9015_read_config: [0] MT2060 IF1:1220
    [  526.949147] af9015: af9015_read_config: tuner id:133 not supported, please report!

```
The last line reporting an error with the tuner is well-known, as i read on several forums. I will try to fix it later, since i have a more serious problem :
When i plug the stick, nothing is created in /dev. As far as i know, we should expect a /dev/dvb/adapter0/ and several things inside. But i have noting. Therefore something is wrong with udev. 
Notice that following the Spanish tutorial, i created a file udev.rules and a script which read as follow:
```

$  more /etc/udev/rules.d/udev.rules
    # dvb devices KERNEL="dvb*", PROGRAM="/etc/udev/scripts/dvb.sh %k", NAME="%c", GROUP="video", MODE="0777"

$    more /etc/udev/scripts/dvb.sh
    #!/bin/sh
    /bin/echo $1 | /bin/sed -e 's,dvb\([0-9]\)\.\([^0-9]*\)\([0-9]\),dvb/adapter\1/\2\3,'

```

I think there is a problem in these scripts... but i'm a newbie with these udev matters...

Could somebody help me ?
Thanks in advance...

nicolas

---

### Post by xc3RnbFO8P on 2008-06-20
Look at this:
[http://linuxtv.org/wiki/index.php/User:Sandybutt]("http://linuxtv.org/wiki/index.php/User:Sandybutt")

---

### Post by roy.nico on 2008-06-20
> **Ringi said:**
> Look at this:
[http://linuxtv.org/wiki/index.php/User:Sandybutt]("http://linuxtv.org/wiki/index.php/User:Sandybutt")

Hi ringi, thanks for your answer. I followed step by step the above link. After plugging in, i have the following in dmesg :
```

[12922.403788] usb 4-6: new high speed USB device using ehci_hcd and address 7
[12922.471773] usb 4-6: configuration #1 chosen from 1 choice
[12922.471942] af9015_usb_probe: interface:0
[12922.473118] af9015_read_config: IR mode:0
[12922.480109] af9015_read_config: TS mode:0
[12922.481492] af9015_read_config: [0] xtal:2 set adc_clock:28000
[12922.484058] af9015_read_config: [0] IF1:36167
[12922.486110] af9015_read_config: [0] MT2060 IF1:1220
[12922.487108] af9015: af9015_read_config: tuner id:133 not supported, please report!
[12922.626838] dvb_af901x: disagrees about version of symbol dvb_usb_device_init
[12922.626847] dvb_af901x: Unknown symbol dvb_usb_device_init

```
The last two lines are new. It seems to me that the drivers i installed before (af9015) are still loaded. This may cause the problem... but i don't know how to get rid of them :-(
The only thing i did is to remove a line ```
dvb-usb-af9015
``` which was in /etc/modules.
What do i have to do ?
thanks in advance.

---

### Post by xc3RnbFO8P on 2008-06-20
Did you do this:
> Create a file "af_patch" in the **dvb_cinergy** folder and insert the following lines:

--- bak/af901x-core.c	2008-06-20 15:12:37.000000000 +0200
+++ af901x-core.c	2008-06-20 15:12:52.000000000 +0200
@@ -63,9 +63,6 @@
 }

 static struct usb_driver af901x_driver = {
-#if LINUX_VERSION_CODE <=  KERNEL_VERSION(2,6,15)
-	.owner = THIS_MODULE,
-#endif
 	.name       = "dvb_usb_af901x",
 	.probe      = af901x_probe,
 	.disconnect = dvb_usb_device_exit,

issue the following commands:

patch < ./af_patch
make && sudo make install

---

### Post by roy.nico on 2008-06-20
Sorry. I rebooted, and now, it seems to be better. Now, i can see the devices in /dev/dvb.
Let's go on...

---

### Post by roy.nico on 2008-06-20
I'm watching TV on my Ubuntu... That's great !

Thanks a lot !
nico

---

### Post by xc3RnbFO8P on 2008-06-20
Glad to help :)

---

### Post by Loeckchen on 2008-07-01
I have the unsupported tuner message, to. How to fix this?

---

### Post by plooo on 2008-10-10
I have the same TV-card and I have the device in /dev/dvb .
I have tried with Kaffeine and it detects my TV-card but I can not tune in any channels. What application do you use?

---

### Post by xc3RnbFO8P on 2008-10-10
You can try Me-TV in Add/Remove (all available application).

---

### Post by plooo on 2008-10-13
Hi Ringi.

Thanx for the tip. Me-TV works great!

---

