---
title: "WUSB100 V2 Almost Working!"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by no_content on 2010-10-21
Hi,

After much internet searching, trial and and error and fresh installs, I've finally got my WUSB100 V2 to work on 10.10....... Sort of!

The method I've used to get it working is shown below however the problem is that every time I restart, or if the dongle gets unplugged I have to go through the whole process again as it will no longer connect and does that thing where it tries for ages then blames it on a bad password.

If anyone has any idea as to how to solve this last little problem it would be much appreciated.

Thanks,
Rob

> **flash63 said:**
> Hello,
a little Trick to add the ID **1737:0078** for the WUSB100v2 to the System and simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

First remove the new compiled driver if necessary:
```

cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall

```
If you previously did not manually compile the driver from Ralink start here. 

Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```
The solution works? Ok, load the driver at startup
```

echo rt2870sta | sudo tee -a /etc/modules

```
alternativ automatic driver load when the stick was plugged in:
```

sudo gedit /etc/udev/rules.d/10-wusb100.rules

```
contents:
```

# UDEV-Rule for wusb-100v2 ID 1737:0078
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0078", RUN+="/sbin/modprobe rt2870sta"

```
make it ready to work
```

sudo service udev reload 

```.. or restart

Link: [http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

greetings and a happy new year :)

Rainer

---

### Post by no_content on 2010-10-21
From playing around with it a bit more, I've realised that on start up, to get it to work I only need to enter:

> sudo service udev reload

However, if I disconnect or remove the USB dongle, I have to do a complete restart and enter the above line again to make it work.

Again if anyone has any advice it'd be much appreciated!!

Thanks

---

### Post by richdog on 2010-10-23
You are my hero I have been trying to get my wsub100v2 going for a couple days now.  As soon as I ran the

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

it started up.  Thank you

---

### Post by bernardfrancois on 2010-11-14
Thanks. This did the trick for me as well in Ubuntu 9.04. Now I can finally upgrade to a newer Ubuntu version! Lol

---

### Post by noran on 2010-11-24
Can't express how much I love you right now :D Thanks! I've been trying to get it to work for a couple of weeks now.

---

### Post by Mr.Bl on 2010-12-14
> **noran said:**
> Can't express how much I love you right now :D Thanks! I've been trying to get it to work for a couple of weeks now.

@Noran

Does your 10.04 v detects the usb?, mine no, i just jumped to 10.10 and everything is ok :o

---

### Post by noran on 2011-01-20
> **Mr.Bl said:**
> @Noran

Does your 10.04 v detects the usb?, mine no, i just jumped to 10.10 and everything is ok :o

Yes it does, following the instructions. Only problem is, I have to remove the USB before I turn on my laptop, or else Ubuntu boots in terminal mode, and display won't show until I remove the USB. Any thoughts on that?

Haven't tried 10.10 yet because there's problems with my Nvidia card.

---

### Post by noran on 2011-01-20
> **Mr.Bl said:**
> @Noran

Does your 10.04 v detects the usb?, mine no, i just jumped to 10.10 and everything is ok :o

Yes it does, following the instructions. Only problem is, I have to remove the USB before I turn on my laptop, or else Ubuntu boots in terminal mode, and display won't show until I remove the USB. Any thoughts on that?

Haven't tried 10.10 yet because there's problems with my Nvidia card.

---

