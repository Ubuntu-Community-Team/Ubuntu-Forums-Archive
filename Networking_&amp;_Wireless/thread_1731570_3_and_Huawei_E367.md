---
title: "3 and Huawei E367"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by jamiepierce on 2011-04-17
Hello all

I have recently purchased a Huawei E367 Mobile broadband dongle from three.co.uk.  My laptop will not detect it at all, not even as a removable storage device.

When I do lusb, this is what I get.

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15d9:0a4d Trust International B.V. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 12d1:1506 Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I am running xubuntu 11.04 on this machine, but I have also tested in on my xubuntu 9.10 netbook and it isn't detected on that, although it is recognised as a storage device.

Thanks guys.

---

### Post by Matbro on 2011-04-19
> **jamiepierce said:**
> Hello all

I have recently purchased a Huawei E367 Mobile broadband dongle from three.co.uk.  My laptop will not detect it at all, not even as a removable storage device.

When I do lusb, this is what I get.

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15d9:0a4d Trust International B.V. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 12d1:1506 Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I am running xubuntu 11.04 on this machine, but I have also tested in on my xubuntu 9.10 netbook and it isn't detected on that, although it is recognised as a storage device.

Thanks guys.

Hi Jamie
Have the same problem with Huawei E367. It is not discovered as a 3G modem in 11.04, only as a storage device, no matter what I do. (Old HP Vectra PC, can be an issue with USB 1.1)
On the other hand, the Huawei E367 modem is working in my laptop using 10.10 x64 bit Ubuntu :) !
I will try, probably this weekend, to install 11.04 on another laptop and see if the modem is recognized
/Mats

---

### Post by bysse on 2011-04-28
I have the same problem as well.
The disturbing part is that the modem is recognized on my computer at work which is having the same version as my laptop, Ubuntu 10.10. This calls for more investigation!

---

### Post by bysse on 2011-04-29
My bad, my laptop was running 10.04.
When i upgraded to 10.10 the modem is recognized correctly.

---

### Post by mahogny on 2011-05-04
solution for ubuntu 11.04

sudo modprobe vendor=0x12d1 product=0x1506

(ID taken from lsusb)
this creates /dev/ttyUSB*

pin code prompt will appear. enter pin. it will tell "operation not allowed" - but in fact it worked. just close the prompt and continue.

---

### Post by fldc on 2011-05-04
> **mahogny said:**
> solution for ubuntu 11.04

sudo modprobe vendor=0x12d1 product=0x1506

(ID taken from lsusb)
this creates /dev/ttyUSB*

pin code prompt will appear. enter pin. it will tell "operation not allowed" - but in fact it worked. just close the prompt and continue.

sudo modprobe **usbserial** vendor=0x12d1 product=0x1506

fixed that for you ;)

---

### Post by jaxxm on 2011-07-25
I go mine to work in 10.04. 
install and use: 
  
  usb_modeswitch -V 0x12d1  -P 0x1506

This switched the mode from usb memory stick to usb 3g dongle.

---

### Post by alexef on 2011-08-19
The same is needed for ubuntu natty 11.04, eventually with a:
```
sudo eject sr0
``` before modprobe, in case modem is detected as 12d1:1446

---

### Post by anttud on 2011-10-31
I have tried everything what I have found from forum and google. Not sure if i'm doing something wrong but nothing works for me. I'm running on ubuntu 10.04. 
I think the problem is that ubuntu regonizes modem as CD and I just can't get it fixed. I can't find it from network manager, though the blue light is blinking. 
```
root@john-laptop:~$ lsusb
Bus 002 Device 004: ID 12d1:14ac Huawei Technologies Co., Ltd. 

```
have also tried
```
sudo modprobe usbserial vendor=0x12d1 product=0x1506
```
and
```
sudo modprobe usbserial vendor=0x12d1 product=0x14ac
```
I can't install Oneirics modeswitch.
Error: Dependency is not satisfiable: libpipeline1 (>= 1.0.0)
This is what i get.
Also tried what Matbro suggested. Didn't work for me.
And i have no idea what to try next?

---

### Post by Gouz on 2011-12-01
anttud

the error you are getting is because you are missing a library.
An easy way to fix this is to go to the synaptic package manager search and install it. An other way is to find the package online and compile it yourself.

And you should really only need to run

sudo modprobe usbserial vendor=0x12d1 product=0x1506 OR sudo modprobe usbserial vendor=0x12d1 product=0x1506 (and install what ever it complains that is missing)

Start your computer and do not insert and usb devices. After you load gnome insert the usb modem, run the commands and install things. Set up a network connection, go right click on your network connections or open them via the panel (System -> preferences -> network connection) set up a mobile network and you are done.

Good luck

---

### Post by hma.istsupport on 2012-03-03
<hma>
hi all,

I am trying to install huawei e367 model, followed the procedure I got from the same thread. but in vein. It looks the module is not available. Somebody please advise ? Thanks.
----------------------------------------------------------------------------------------
adarsh@adarsh-vaio:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
adarsh@adarsh-vaio:~$ lsusb
Bus 002 Device 005: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
adarsh@adarsh-vaio:~$ sudo modprobe vendor=0x12d1 product=0x14ac
[sudo] password for adarsh: 
**[COLOR=Red]FATAL: Module vendor=0x12d1 not found.[/COLOR]**
adarsh@adarsh-vaio:~$ 
---------------------------------------------------------------------------------------------
</hma>

---

