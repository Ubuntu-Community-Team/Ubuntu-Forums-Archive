---
title: "Vodafone USB Modem"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by petrocles on 2009-09-01
I am a very inexperienced ubuntu user. i like the potential but have always used windows in the past. i have installed  hardy ubuntu 8.04 which uses  kernel linux 2.6.24.-24 generic and gnome 2.22.3 onto a laptop and recently purchased vodafone usb modem which is payg and model k3565 ev2 (hsdpa usb stick)

i have installed and used various commands from searched pages but maybe i am just missing the absolute basics because when i plug in the usb modem nothing happens. windowlised maybe but i expect to be prompted or see something happen.

i connect wirelessly to my home network but would like to be able to use modem outside.

what should i be doing to use this device?

typed lsusb

Bus 005 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:000

typed ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1

---

### Post by petrocles on 2009-09-01
i believe that the problem now is that the connection is not recognised certainly when i left click th wireless network connection icon it does not appear as an option. when i right click edit wireless networks it opens p a box which has only two boxes availabe which says name and bsssids.
i will find out what bssids is befor i mess with these settings. do not want to lose wireless connection!

---

### Post by petrocles on 2009-09-02
bump

---

### Post by Neill_R on 2009-09-02
Hi 
I am also new to ubuntu being a long time frustrated user of Windows. I run Xubuntu 9.04 on a laptop and have an orange UK Option ICON 225 USB modem. On right clicking my NetworkManager icon on the task bar I can choose edit connections and set up the connection to Orange that way. What you says does not square with my experience but then you are not on the latest OS.

---

### Post by ad_267 on 2009-09-02
I don't have any experience with Vodafone Modems, but here is probably a good place to start: [http://www.betavine.net/bvportal/resources/datacards](http://www.betavine.net/bvportal/resources/datacards).

It looks like your device (k3565) is listed under the data cards supported, although there's a few similar model numbers so it's hard to say for sure.

---

### Post by gradinaruvasile on 2009-09-02
> **petrocles said:**
> I am a very inexperienced ubuntu user. i like the potential but have always used windows in the past. i have installed  hardy ubuntu 8.04 which uses  kernel linux 2.6.24.-24 generic and gnome 2.22.3 onto a laptop and recently purchased vodafone usb modem which is payg and model k3565 ev2 (hsdpa usb stick)

i have installed and used various commands from searched pages but maybe i am just missing the absolute basics because when i plug in the usb modem nothing happens. windowlised maybe but i expect to be prompted or see something happen.

i connect wirelessly to my home network but would like to be able to use modem outside.

what should i be doing to use this device?

typed lsusb

Bus 005 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:000

typed ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1

[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu](http://www.betavine.net/bvportal/resources/datacards/os/ubuntu)

---

### Post by petrocles on 2009-09-08
thank you
 
 
i click on the vodafone mobile connect card driver for linux and get the following message:
 
disconnected from internet
 
vodafone mobile connect card driver for linux has given up asfter trying to connect three times to internet. this might be provoked by a problem in the configuration or just the fact that theres no carrier

---

