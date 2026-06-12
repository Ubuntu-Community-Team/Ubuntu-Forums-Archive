---
title: "Which &quot;device&quot; is my usb on?"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by olwe on 2011-01-21
I'm trying to set up 1-wire on my Ubuntu. It needs a usb port to be associated with a device. The instructions say to run lsusb to see your usb's. Then run dmesg to see which device the usb is attached to. The example output of dmesg says "usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0". My trouble is I'm not getting any indication what device my usb is attached to. Nowhere in the dmesg output am I seeing "...attached to..." How can I find this out?

---

### Post by lykeion on 2011-01-21
/dev/ttyUSB0 maybe?

Is 1-wire some kind of temperature sensor?
Maybe these links will help: 
[https://help.ubuntu.com/community/1wire](https://help.ubuntu.com/community/1wire)
[http://automation.binarysage.net/?p=1244](http://automation.binarysage.net/?p=1244)
[http://www.technotes.se/?p=26](http://www.technotes.se/?p=26)

---

### Post by olwe on 2011-01-21
I just need a command to know what my usb is attached to. No, there is no usb0. lsusb gives:
> 
Bus 001 Device 010: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter
Bus 001 Device 008: ID 050d:0304 Belkin Components 
Bus 001 Device 007: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

But dmesg doesn't give any info on devices -- for anything actually. Yes, this is a temp sensor kit. It's the first one (Bus 001...) The command to run it is:
> /opt/owfs/bin/owfs /dev/ttyUSB0 /var/1-Wire

But as you see, I need the proper device.

---

### Post by lykeion on 2011-01-21
You probably need to load the usbserial driver first (notice how I got the vendor/product id from your lsusb output):
```
sudo modprobe usbserial vendor=0x0f4a product=0x2490
```
Then you should see "attached to ttyUSB0" in dmesg

---

### Post by olwe on 2011-01-21
I don't think we need to load a module. The usb ports are working on the machine. It's just that I can't find out which devices are associated with them. dmesg isn't giving me that info on anything....

---

### Post by lykeion on 2011-01-22
Your USB ports are working out-of-box, but I figured that the reason you don't see that your serial USB adapter is attached to a port is that don't have the module loaded.
In any case it doesn't hurt to try and load the module and see if it works. The name of the module seems to be ds2490. You can get some info about the module with:
```
modinfo ds2490
```
And load it with:
```
sudo modprobe ds2490
```
The module will only be loaded for the current session. If you want to autoload it at startup you'll need to add it to the /etc/modules file

After some googling around I found that you also can use udev. see these links:
[http://www.domogik.org/tiki-index.php?page=plugin_onewire&offset=&sort_mode=filename_desc&atts_show=y#Permissions_DS9490R_example_](http://www.domogik.org/tiki-index.php?page=plugin_onewire&offset=&sort_mode=filename_desc&atts_show=y#Permissions_DS9490R_example_)
[http://ubuntuforums.org/archive/index.php/t-429100.html](http://ubuntuforums.org/archive/index.php/t-429100.html)

---

