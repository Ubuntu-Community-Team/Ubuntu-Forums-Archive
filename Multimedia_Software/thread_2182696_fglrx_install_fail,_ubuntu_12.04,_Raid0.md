---
title: "fglrx install fail, ubuntu 12.04, Raid0"
date: 2013-10-22
forum: Multimedia Software
---

### Post by seany1212 on 2013-10-22
Hi All,

I've managed to install Ubuntu 12.04 using the alternative cd with software RAID0. The problem i'm having is that whenever i'm trying to install ATI drivers (i've tried Catalyst 12.6, 13.1 and 13.4 drivers) for my HD 4770 i can issue the terminal commands to break down the .run into 3 separate .deb files but when i begin the .deb command to install the packages it gets to 'building instances /boot/...../linux-3.8.03-generic', it then hangs for a small period before then running a few more lines before trying to install that same line and then gives me a 'System Program Problem Detected' before stopping the installation.

The partitions I have are as follows and i'm not sure whether it's here where the problem lies:

RAID0 (2x320GB HDDs):
#1 8GB Swap area
#2 2GB Ext4 /boot (Bootable)
#3 630GB Ext /

The open-source packaged one works, the issue is that it incorrectly displays the size of my attached TV but also i need access to the catalyst control center in order to adjust my fan speed to consistently 100%. Hopefully i've given enough information for someone to point me in the right direction and help get my goals achieved :D

Seany

---

### Post by Yellow Pasque on 2013-10-22
Unless you installed Ubuntu 12.04.1, Catalyst isn't going to work. You need to be using a 3.2 kernel and Xserver <= 1.12.x

---

### Post by seany1212 on 2013-10-22
Is there anything that can adjust the fan speed? I just want it consistently 100%

Seany

---

### Post by Yellow Pasque on 2013-10-23
I'm note sure why you would want the fan at full blast all of the time unless you have a shoddy/inadequate cooler.

> Controlling the fan speed directly is not possible (and would be very dangerous), but it can be lowered by setting lower power profile.
-- [http://wiki.x.org/wiki/RadeonFeature/#index3h2](http://wiki.x.org/wiki/RadeonFeature/#index3h2)

---

### Post by seany1212 on 2013-10-24
> **Temüjin said:**
> I'm note sure why you would want the fan at full blast all of the time unless you have a shoddy/inadequate cooler.


Unfortunately yes, the XFX HD4770 stock cooler is pretty poo when it comes to removing heat. In Windows I was able to adjust the fan speed on-the-fly with Catalyst control center, most of the time choosing to run it at 100% as noise isn't an issue. If i do adjust the power profile though to a higher power profile does this not also increase the clock speeds?

---

### Post by Yellow Pasque on 2013-10-24
>  If i do adjust the power profile though to a higher power profile does this not also increase the clock speeds? 
Yes. If that's not what you want, then you're out of luck as far as I'm aware.

---

