---
title: "Qualcomm 3g modem not connecting"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by b-boy on 2010-09-13
Hi 

I have a Lenovo W510 Laptop with Ubuntu 10.04. The laptop has  an on board Qualcomm 3g modem. I have managed to install the Qualcomm firmware and Network Manager detects the 3g device but when I try to connect it disconnects after a few seconds. My syslog has the error

```
Got failure code 100: Unknown error
```


please HELP

---

### Post by b-boy on 2010-09-15
Hi Guys 

I have finally solved this. The error I was getting previously was because I did not enable wireless on the laptop which is also the radio for the 3g. My bad did not know that.

So let my explain 

**HOW TO Get Qualcomm onboard 3g card Working Ubuntu 10.04 Lenovo W510**

1. I got the windows driver from Lenovo (I just search for Qualcomm) and installed it in a windows PC
2. I then copied the the 3 files (amss.mbn apps.mbn UQCN.mbn) from the C:/
/Program Files/QUALCOMM/Images/Lenovo
there is alot of these files there. I used the ones from the 6 and  UMTS folders
3. I then created a director /lib/firmware/gobi and copied the 3 files in this DIR
4. I the add backports to my sources.list 
```
deb http://archive.ubuntu.com/ubuntu lucid-backports main universe multiverse restricted

``` and add the packages 
```
linux-backports-modules-wwan-2.6.32-25-generic (2.6.32-25.22)
linux-image-2.6.32-25-generic (2.6.32-25.43)
```
5. I rebooted
6. I downloaded the gobi_loder [http://www.codon.org.uk/~mjg59/gobi_loader/download/]("http://www.codon.org.uk/~mjg59/gobi_loader/download/")
7. I then loaded the driver 
```
./gobi_loader-0.5/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/

```
make sure the sim card is in and reboot
and thats it

**Pleas make sure the wireless radio is switch on ..the switch on the the side of the laptop**

---

### Post by MaindotC on 2010-09-15
Glad that your modem is working and even better that you figured it out by yourself!  Please mark the thread as solved.

---

