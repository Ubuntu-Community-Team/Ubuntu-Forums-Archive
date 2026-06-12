---
title: "Hdtv usb dvb-t"
date: 2010-10-16
forum: Multimedia Software
---

### Post by sohlinux on 2010-10-16
Hello, I have a HDTV USB DVB-T which works fine in Windows but how can I make it work in Ubuntu 10.4?

Thanks
Tom

---

### Post by sohlinux on 2010-10-17
if it helps im using a sony vaio laptop pls help

---

### Post by efflandt on 2010-10-17
You have not given any specific information about it, like make/model, what shows up in dmesg for it, or any errors there, when you plug it in, what shows up for it in lsusb.

Start here and look for your hardware and how to set it up and test it [http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

If you post text that is long or formatted put code tags around it by highlighting it and clicking # icon at top of Message window.

---

### Post by sohlinux on 2010-10-17
the make and model is Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick

the output of lsusb=

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b14e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

the output of dmesg = 

[ 1406.576280] usb 2-1.3: new high speed USB device using ehci_hcd and address 4
[ 1406.688912] usb 2-1.3: configuration #1 chosen from 1 choice
[ 1406.692993] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
[ 1406.693423] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.1/input/input13
[ 1406.693562] generic-usb 0003:15A4:9016.0003: input,hidraw2: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-1.3/input1
[ 1406.725473] af9015: tuner id:179 not supported, please report!
[ 1406.725532] usbcore: registered new interface driver dvb_usb_af9015

so the question is where can I find the correct driver? at the moment kaffeine doesnt show up any tv device installed.

Thanks
Tom

---

### Post by sohlinux on 2010-10-17
:confused:

---

### Post by sohlinux on 2010-10-18
:confused:

---

### Post by xc3RnbFO8P on 2010-10-18
Read this thread:
[http://www.uluga.ubuntuforums.org/showthread.php?t=606487&page=16]("http://www.uluga.ubuntuforums.org/showthread.php?t=606487&page=16")

---

### Post by heyho on 2010-10-18
What app are you using?

I found Kaffeine worked like a charm for my random no-name USB DVB-T stick.

---

### Post by sohlinux on 2010-10-18
> **Ringi said:**
> Read this thread:
[http://www.uluga.ubuntuforums.org/showthread.php?t=606487&page=16]("http://www.uluga.ubuntuforums.org/showthread.php?t=606487&page=16")


thanks I will check that out :)

---

### Post by sohlinux on 2010-10-18
> **heyho said:**
> What app are you using?

I found Kaffeine worked like a charm for my random no-name USB DVB-T stick.

tried Kaffeine but it doesnt show any device so will continue trying :mad:

---

### Post by jimmers on 2010-10-19
Try installing gxine, I find that Kaffeine works for me with my AverMedia DVB-T USB.

---

### Post by sohlinux on 2010-10-19
> **jimmers said:**
> Try installing gxine, I find that Kaffeine works for me with my AverMedia DVB-T USB.

thanks but it didn't work. any more ideas?

Thanks:P

---

### Post by sanderj on 2010-10-21
Get the script [http://www.appelboor.com/af9015/usb-dvb-make-script.sh]("http://www.appelboor.com/af9015/usb-dvb-make-script.sh") and run it as root (thus with "sudo ..."). 

Attention: does only work with Ubuntu up to 10.04, does NOT work on Ubuntu 10.10 and newer...

---

### Post by sohlinux on 2010-10-21
> **sanderj said:**
> Get the script [http://www.appelboor.com/af9015/usb-dvb-make-script.sh]("http://www.appelboor.com/af9015/usb-dvb-make-script.sh") and run it as root (thus with "sudo ..."). 

Attention: does only work with Ubuntu up to 10.04, does NOT work on Ubuntu 10.10 and newer...

thanks for that but I installed 10.10 yesterday thinking it may fix it but it didn't :(

---

### Post by sohlinux on 2010-10-23
anyone know of a fix for this?

---

### Post by sanderj on 2010-10-23
> **sohlinux said:**
> anyone know of a fix for this?

Yes: install 10.04, and run the script. Done.

---

### Post by sohlinux on 2010-10-23
> **sanderj said:**
> Yes: install 10.04, and run the script. Done.

not funny

---

### Post by sanderj on 2010-10-23
> **sohlinux said:**
> not funny

Indeed. However, it's the reality.

---

