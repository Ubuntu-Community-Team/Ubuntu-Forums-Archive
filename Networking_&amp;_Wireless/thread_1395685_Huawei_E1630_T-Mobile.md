---
title: "Huawei E1630 T-Mobile"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by jalirious on 2010-02-01
Hello folks, I'm trying to use the above mobile wireless device with 9.04 ubuntu.

Following online advice I tried the following steps,

>lsusb
(gives "Bus 002 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd.")

>modprobe usbserial vendor=0x12d1 product=0x1446
(accepts, no response)

>ls -la /dev/ttyU*
(gives "ls: cannot access /dev/ttyU*: No such file or directory")

- Also not recognised by sudo wvdialconf.

I had no issue with the huawei e220, auto-recognised on jaunty, wvdial'd fine on hardy. Any advice? Cheers.

---

### Post by pdc on 2010-02-02
most of these devices need flipping; so they are NOT seen as CD-ROM; instead seen as modems;

your device seems to have the same ID as the Huawei Huawei E270+  (HSPA+ modem) and Huawei E1762 and Huawei E1820

(not sure where you got your online ID for it from);

as Ubuntu is debian-based, I suggest you download and install the latest debian version of usb_modeswitch;

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

sid (unstable) version 1.0.7.1 ........ don't worry about the prefix of unstable: we can cite others for whom this has worked fine;

read the usb_modeswitch home page whilst you are at it;

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

the beauty of this latest version is it seems to autoinstall; autoconfigure, and recognise the devices plugged into it;

it should flip your modem;

give it 30-60secs to run; 

after that, run 

> ls /dev/ttyUSB*

if you get some positive results, try your wvdial script

let us know how it all goes

---

### Post by jalirious on 2010-02-02
Well, i'm writing this using the new modem, so I guess this is solved.

In case it is of help to anyone, here are my steps..

Synaptic: installed all [4] libusb packages available (2 would probably suffice)
          installed tcl
          installed udev-extras (likely not needed)
{also install wvdial if haven't already}

Downloaded usb-modeswitch-1.1.0.tar.bz2, usb-modeswitch-data and usb_modeswitch.conf (all from [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) -this is supposed to maintain links to the very latest versions).

mkdir new_directory
put all downloaded files in a new_directory, cd new_directory 

sudo su
cd usb-modeswitch-1.1.0
make install
cd ../usb-modeswitch-data-20100129
make install
cd ..
mv usb_modeswitch.conf /etc

-> plug in mobile dongle, wait 1 min.
ls /dev/ttyUSB*
[gives similar to 
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3  /dev/ttyUSB4]

wvdialconf
wvdial [connected]

pdc = :KS

---

### Post by pdc on 2010-02-02
well done jilarious; very helpful post; glad it worked for you; usb_modeswitch keep updating very rapidly;

which port are you using on wvdial.conf?

---

### Post by jalirious on 2010-02-03
I attach here my .wvdialconf. Cheers :)

---

