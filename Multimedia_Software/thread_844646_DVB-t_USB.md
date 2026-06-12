---
title: "DVB-t USB"
date: 2008-06-29
forum: Multimedia Software
---

### Post by ntn_456 on 2008-06-29
Hello there, I'm desperately trying to get a USB DVB-t device to work in ubuntu. Its a no-name cheap thing from ebay. Tried linuxtv wiki, still no luck.
Here's the usb id:
```

ajit@ajit-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 04fc:0c25 Sunplus Technology Co., Ltd 
Bus 004 Device 002: ID 18b4:1001  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

```

```

root@ajit-laptop:/home/ajit# dmesg -c
[  747.141337] usb 4-2: new high speed USB device using ehci_hcd and address 7
[  747.173272] usb 4-2: configuration #1 chosen from 1 choice
[  747.174504] input: HID 18b4:1001 as /devices/pci0000:00/0000:00:1d.7/usb4/4-2/4-2:1.0/input/input17
[  747.225456] input,hidraw0: USB HID v1.11 Keyboard [HID 18b4:1001] on usb-0000:00:1d.7-2

```

Thankyou.

---

### Post by tpruvot on 2008-11-14
It's an e3ctech EC168 Chips (Dual tuner ?)

PC Basic USB TNT Basic LIGHT has same VID/PID

Réf. GRTNTUSBV4

Vid_18B4&Pid_1689&MI_01.DeviceDesc      = "USB DVB-T TV Tuner"
Vid_18B4&Pid_1001&MI_01.DeviceDesc      = "USB DVB-T TV Tuner"
Vid_18B4&Pid_1002&MI_01.DeviceDesc      = "USB DVB-T TV Tuner"
Vid_18B4&Pid_1002&MI_02.DeviceDesc      = "USB DVB-T TV Tuner 2nd"

also looking for the driver...

[http://www.e3ctech.com/download.html](http://www.e3ctech.com/download.html)

---

### Post by andlinux on 2009-02-24
I have the same USB dvb-t stick and I was wondering if you already found a solution to make this work in ubuntu ?

---

### Post by ntn_456 on 2009-02-24
Sorry pal, didn't bother much about it after viewing Linux USB <http://www.qbik.ch/usb/devices/showdev.php?id=4355> page. I just sticked to the idea of booting windows whenever I wanted to use it.

---

### Post by Ibn al-Hazardous on 2009-04-25
> **ntn_456 said:**
> Sorry pal, didn't bother much about it after viewing Linux USB <http://www.qbik.ch/usb/devices/showdev.php?id=4355> page. I just sticked to the idea of booting windows whenever I wanted to use it.

I just thought I'd chime in and tell you guys that this device has an experimental driver now. There was a couple of hoops to jump through, so I made a [write-up on how I did it]("http://blueturtle.nu/ibn/blog/45/htpc-or-hmc-whatever-part-deux"). Hopefully it's a pretty comprehensive guide on getting it up and running. (The only thing I have left is getting the remote working, which is kinda ironic since the device identifies itself as a keyboard...)

---

### Post by andlinux on 2009-04-25
> **Ibn al-Hazardous said:**
> I just thought I'd chime in and tell you guys that this device has an experimental driver now. There was a couple of hoops to jump through, so I made a [write-up on how I did it]("http://blueturtle.nu/ibn/blog/45/htpc-or-hmc-whatever-part-deux"). Hopefully it's a pretty comprehensive guide on getting it up and running. (The only thing I have left is getting the remote working, which is kinda ironic since the device identifies itself as a keyboard...)
Thanks for the info, I need to try that. :)

---

### Post by ntn_456 on 2009-04-26
Thanks will try it.

---

### Post by andlinux on 2009-04-26
Well it worked perfectly but after the reboot it didn't work, how can I solve that ?

Edit: It has something to do with the modules, if I do lsmod then I can see that not all the modules are loaded ?????

EDIT2: Found something new, if I insert the usb stick (dvb-t) in the usb port from the start then it will work, but not if I start ubuntu and then insert the usb stick. Who can explain this ?

---

### Post by andlinux on 2009-04-30
Well, I messed it up, I upgraded to 9.04 and now the dvb-t stick isn't working.

When I try to manualy load the modules I get with 2 mudules this message:
 sudo insmod dvb-usb-ec168.ko
insmod: error inserting 'dvb-usb-ec168.ko': -1 Invalid module format
sudo insmod ec100.ko
insmod: error inserting 'ec100.ko': -1 Invalid module format

What can I do to fix this ?

---

### Post by Ibn al-Hazardous on 2009-06-20
> **andlinux said:**
> Well, I messed it up, I upgraded to 9.04 and now the dvb-t stick isn't working.

When I try to manualy load the modules I get with 2 mudules this message:
 sudo insmod dvb-usb-ec168.ko
insmod: error inserting 'dvb-usb-ec168.ko': -1 Invalid module format
sudo insmod ec100.ko
insmod: error inserting 'ec100.ko': -1 Invalid module format

What can I do to fix this ?

You need to recompile the modules. They are compiled to work with one specfic kernel version, and when you upgraded ubuntu - the kernel got upgraded too.

As for getting the modules loaded automatically, you probably need to run 'make install' too - otherwise hotplug won't find them. The instructions I give in my blog post is about getting it working on a machine where it's always plugged in. If you run 'make install', you don't need the insmod lines in rc.local (those lines are only run on machine start - which is why it is only working if you have the usb device plugged in when you start up).

---

### Post by andlinux on 2009-06-21
> **Ibn al-Hazardous said:**
> You need to recompile the modules. They are compiled to work with one specfic kernel version, and when you upgraded ubuntu - the kernel got upgraded too.

As for getting the modules loaded automatically, you probably need to run 'make install' too - otherwise hotplug won't find them. The instructions I give in my blog post is about getting it working on a machine where it's always plugged in. If you run 'make install', you don't need the insmod lines in rc.local (those lines are only run on machine start - which is why it is only working if you have the usb device plugged in when you start up).
Indeed that was it, it's working :)

---

### Post by OpenThinking on 2010-09-25
I got my WeTech USB stick to work in Ubuntu 10.04 with the instructions on this page: [https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942]("https://www.dealextreme.com/forums/Default.dx/sku.8325~threadid.278942")

But I got two errors when doing the "make" step. To get rid of those I had to edit a file:

**nano ec168/v4l/Makefile.media **

Search for this line (with CTRL+W):

**obj-$(CONFIG_DVB_FIREDTV) += firedtv.o**

and comment out this line and the next eight lines by putting a # in front of each line. This excludes the Firewire support from the v4l package.

Next, search for this line (with CTRL+W):

**ir-core-objs := ir-keytable.o ir-raw-event.o rc-map.o**

The line has another ir-??something??.o specified, remove it so the line looks like above.

Save the file (with CTRL+O or CTRL+X). Then run the "make" command.

---

### Post by tpruvot on 2010-12-04
i made a guide for the EC168 on ubuntu 10.10 :
[http://tanguy.wdscript.fr/EC168](http://tanguy.wdscript.fr/EC168)

---

