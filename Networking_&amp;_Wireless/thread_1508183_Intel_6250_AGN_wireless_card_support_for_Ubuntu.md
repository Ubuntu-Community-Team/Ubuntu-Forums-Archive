---
title: "Intel 6250 AGN wireless card support for Ubuntu"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by usctrojan on 2010-06-12
Intel has released the wifi firmware support for 6050 series on June 2nd. Can some one please tell the steps involved in getting support enabled for this card after downloading the microcode from Intel site

Thanks a Lot

---

### Post by chili555 on 2010-06-12
I believe it's already supported in the module *iwlagn*. What is the pci.id of your device?```
lspci -nn
```Is it listed in:```
modinfo iwlagn
```Doesn't /lib/firmware contain the correct firmware file?```
ls /lib/firmware | grep ucode
```

---

### Post by chili555 on 2010-06-12
Oops, sorry. Now I see. The new firmware is 6050-xx and the firmware we currently have is 6000-xx.

Save the file to your desktop. Right-click and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/wlwifi-6050-ucode-9.201.4.1
sudo cp iwlwifi-6050-4.ucode /lib/firmware
```Now let's make sure it has the correct permission and ownership:```
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
```Now unload and reload the module:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn
```Now does your device work as expected?

---

### Post by usctrojan on 2010-06-14
Thanks a lot chili555!!!
You made my day.
worked like a charm!
Thank you!

---

### Post by Tuzenbach on 2010-07-22
Wow - thanks for that info. That was exactly what I needed to get my wifi working. 

Thanks!

---

### Post by donsalo on 2010-08-05
Thanks chili555, you are a great help.  This worked perfectly on my thinkpad sl410 running ubuntu 10.04

Now it's time to kill the touchpad...

---

### Post by calmblythe on 2010-09-05
Thank you sooooo much, chili555!! This worked flawlessly on my Dell XPS 16.

---

### Post by calmblythe on 2010-09-05
From what I see, The XPS Studio 16 picks up wireless networks now, but it can't connect to them. Also, it appears to be in a static state, so to speak. i.e. Whatever it picks up is stuck as is. So if you move into an area with new networks, they won't register. The ones that were registered at boot-up will remain, reporting whatever signal strength they had at the time [of boot-up].

So, really, my problem hasn't been fixed. :(

---

### Post by Tazdeviloo7 on 2010-12-12
Where can I find the iwlwifi-6050-4.ucode file? I tried following the /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko path but I could not open the iwlagn.ko file. I've tried finding the file elsewhere online, but can't seem to do so. This is my first time using  linux besides my rooted Android phone so everything is pretty alien to me still. Any help would be greatly appreciated.

---

### Post by Tazdeviloo7 on 2010-12-12
I think I understand now the file I need is iwlwifi-6050-ucode-9.201.4.1.tgz . intellinuxwireless.org appears to be down right now so anybody know another source to get that file?

---

### Post by Tazdeviloo7 on 2010-12-14
The intel site went back online and i managed to download the driver and do all the above steps, but the card still shows up as disabled. I made a new thread here with more details.
[http://ubuntuforums.org/showthread.php?p=10238318#post10238318](http://ubuntuforums.org/showthread.php?p=10238318#post10238318)

---

