---
title: "Freecom DVB-T USB Stick Problems"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by maxmurdock on 2006-07-10
Hello, I'm having problems with my new Freecom DVB-T USB Stick in my Kubuntu Dapper. It seems to be a new revision or something because I followed the step-by-step linux v4l-vbd guide ([http://www.linuxtv.org/wiki/index.php/HOW_TO_Installing_DVB](http://www.linuxtv.org/wiki/index.php/HOW_TO_Installing_DVB)) and I can't get it work. I have all the necessary stuff installed, but when I plug the stick, no "/dev/dvb" node is created.
This device appears in the DVB USB device list from linuxtv.org, but labeled as "old rev": [http://www.linuxtv.org/wiki/index.php/DVB_USB](http://www.linuxtv.org/wiki/index.php/DVB_USB)
So maybe I have a different revision.

This is all information I can get:

Commercial name: **Freecom DVB-T & Analog USB Stick**

This is a part of what I get with "lsusb -v":
```

Bus 003 Device 010: ID 14aa:0620 AVerMedia (again) or C&E
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x14aa AVerMedia (again) or C&E
  idProduct          0x0620
  bcdDevice            0.01
  iManufacturer          16 Hybrid TV Receiver (TM6000)
  iProduct               32 Hybrid TV Receiver (TM6000)
  iSerial                64 2.0
  bNumConfigurations      1

```

ID: **14aa:0620**. It shows as "Avermedia"???
Someone had the same problem or can help me? Thanks

---

### Post by Paul Lattimer on 2006-11-27
I'm having no luck with this device. Has anyone had success with this device (or another brand with the same USB ID's)? 
Same LSUSB output.

Thanks

---

### Post by janmartin on 2006-12-29
It might be you have the wrong firmware?

This is what happened to me:

Written down from the package, I bought a:
[b]Freecom DVB-T USB Stick
Digital terrestial TV & Radio Receiver / USB 2.0
Win XP and MCE[/b]

OK, 

so I did a 
```
lsusb -v
```
to find out what firmware I need.

From the result 
```
Bus 001 Device 007: ID 14aa:0226 AVerMedia (again) or C&E
```

I thought this might be the right one. (Only one with "aver" in its name):
dvb-usb-avertv-a800-02.fw

but I got the same errors as you: Nothing working at all and no
/dev/dvb

So i tried 
```
dmesg
```

and got this:
```
...
dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware

dvb-usb: did not find the firmware file. (**dvb-usb-wt220u-fc03.fw**) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
...
```
After getting the right firmware I rebooted and presto, the light went on at the USB stick, and the /dev/dvb appeared:
```

/dev/dvb/adapter0
/dev/dvb/adapter1

```
I did 
```
dmesg
```
again to check everything went well. it seems so.
Now I am installing Kaffeine to go on.

Good luck, and let me know if this helps.

---

### Post by puccaso on 2007-03-11
yea
iv done all of that
but kaffine still says that it cannot find any DVB components


even scantv doesnt find it

any ideas?


i had this working before
with no problems.

this is very tedious :@

---

