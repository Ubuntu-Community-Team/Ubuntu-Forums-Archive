---
title: "Using rt2870/rt3070 staging source"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by gannggstaz on 2011-03-06
I have found numerous posts about installing the ralink rt2870/3070 drivers, and ended up stumbling upon some information. Apparently the drivers are built into the kernel under "Staging Drivers". Another handy feature is actively adding UID's to devices not natively supported by the drivers but still run the rt2870/rt3070 chipset. Generally enabling drivers on a kernel level is more stable and faster in terms of boot time so this is usually a good idea. If you already have your adapter running, you might as well stick with your compiled version of the driver.

First off, run
```
sudo -i
```
and enter your password. These instructions modify files accessible only by root. 

1)To make sure that the module is enabled, you should run
```
modprobe -l|grep rt2870sta
```
and get the output
```
kernel/drivers/staging/rt2870/rt2870sta.ko
```
if you know your wireless card is supported you can skip this next step

2)Check if your device is enabled in the driver run lsusb and find your device's UID. I have the Belkin F5D8055 v2 and will be using that as an example. Plug in your device and run:
```
$lsusb
 Bus 001 Device 005: ID **050d:825b **Belkin Compoents F5D8055 N+ Wireless Adapter v2000
```
Remember the boldfaced character string, as it identifies your device
```
modinfo rt2870sta
```
a long list of UID's will be listed. Take the first four characters of your devices lsusb (in this case 050d) and limit the results to those including that string of characters. The grep command limits results to those lines with a specific character string, and the "-i" makes it case insensitive. Note that you should replace the colon with a space in this command. 
```
modinfo rt2870sta|grep -i **050d 825b**
```
if your device's UID is listed, then ignore the following and move on to step 3. If not, read along

I found this information at [http://en.gentoo-wiki.com/wiki/Talk:Ralink_RT2870](http://en.gentoo-wiki.com/wiki/Talk:Ralink_RT2870) Run this, subsituting your uid for 050d 825b
```
echo "050d 825b" > /sys/bus/usb/drivers/rt2870/new_id
```
Congragulations, you have successfully added your uid.

3) You are now done with the hard part. Now run:
```
modprobe rt2870sta
``` 
now open a terminal and run 
```
ifconfig wlan0 up
ifconfig wlan0
``` 
Your network interface should be up, followed by some blinkenlights from the network adapter. 

4) To make the module autoload on boot edit /etc/modules and add the module you want to load. In this case add the line rt2870sta. Next time you boot your device should be running and you can now configure your network. 
This might work with other ralink chipsets, though I have no devices that run any other chipsets so if anybody is willing to test them using the in-kernel modules please respond with your results

---

### Post by Radon on 2011-03-09
Thank you very much!

I have no idea what a recent update for 10.04 did, but it stopped my Linksys WUSB600N stopped resetting itself every few minutes. I'm finally a happy camper!:D

---

