---
title: "Micromax MMX 352G USB 3G Modem not showing in ubuntu 11.04"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by gaigoleb2 on 2011-04-30
I use ubuntu 11.04 on my laptop, which I upgraded yesterday itself. After plugging in the usb modem, lsusb shows 1c9e:f000. its product if is 9605. As it should be switching to 9605, but it doesnt. It doesnt show up in Computer as usb modem disk. Moreover, it also doesnt create any ttyUSB file in /dev.
Whereas when I plug in the terracom usb 3g modem, it gets detected, switched and works fine. Kindly suggest as I am trying to solve this problem since 4 days with all the methods posted all over the internet, but nothing seems to work...

---

### Post by alexfish on 2011-05-01
Hi

Can post results of usb-devices command
```
usb-devices
```

you have posted only one usb ID product= "9605". is the vendor ID the same "1c9e"
also need to know if usb_modeswitch was required to switch the device

If you have an alternate Internet connection can also try updating the usb Ids
```
sudo /usr/sbin/update-usbids
```

alexfish

---

### Post by gaigoleb2 on 2011-06-17
Here's a quick guide which I think you should try.
[http://hashprompt.blogspot.com](http://hashprompt.blogspot.com)

---

### Post by gaigoleb2 on 2011-07-02
a detailed description to configure mmx 352g 3g usb modem with bsnl 2g/3g sim is for ubuntu 11.04 is provided in below mentioned link.
[http://hashprompt.blogspot.com](http://hashprompt.blogspot.com)
With this guide you can build any kind of modem with ubuntu 11.04

---

### Post by chandra2730 on 2012-09-23
Open terminal
type the following codes
"sudo gedit /etc/modules"

and then at the end of the line
type this

"usbserial
option"




and then restart your computer and connect the modem
then you'll see your modem
now create a new mobile broadband profile clicking on the edit connections and add new on mobile broadband tab
you must put RIGHT APN for your carrier


for
Indian carriers


TATA DOCOMO=tata.docomo.internet
AIRTEL=airtelgprs.com
AIRCEL=aircelweb
BSNL=bsnlnet
VODAFONE=www
VIRGIN MOBILE=vinternet.in





---------THIS WORKS FOR MY MICROMAX 352G MODEM WITH UBUNTU 12.04.

---

