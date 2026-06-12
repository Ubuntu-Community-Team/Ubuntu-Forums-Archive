---
title: "TEW-645UB Noob Configuration Guide (10.10)"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by Smurferdude on 2011-02-03
Hello All,

I am new to Ubuntu and have only been using it for a couple of weeks. I installed it on my PC which has a Trendnet TEW-645UB Wireless Adaptor. I spent a couple of hours figuring out how to set it up using various guides that were not always easy to follow. So I thought I would write this guide for other Ubuntu noobs. Thanks goes to users [Jim March]("http://ubuntuforums.org/member.php?u=181148") and [flash63]("http://ubuntuforums.org/member.php?u=815324"). 

1)
Plug the adapter into the computer.

2)
Open up the Terminal:
Applications > Accessories > Terminal

3)
Identify your wireless adapter
Enter the following into the terminal window:
```
lsusb 
```This will list all USB devices connected to your computer. Look for a row with Trendnet. This is your device. The number on the right of ID is your device ID. The TEW-645UB has a device ID of 157e:3013 and hopefully yours matches that.

4) Configure the drivers by entering the following into the terminal

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "157e 3013" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```*Make sure the above text is entered as ONE line into the terminal

```
sudo modprobe -rf rt2870sta
``````
sudo modprobe rt2870sta
``````
dmesg | egrep 'rt28|usb|Phy'
```5) Now we want to automatically load the drivers when the adapter is plugged in
alternativ automatic driver load when the stick was plugged in:

```
sudo gedit /etc/udev/rules.d/10-wusb100.rules
```This will open up a text editor called gedit. Paste the code below into the file and save.

```
# UDEV-Rule for wusb-100v2 ID 157e:3013
SUBSYSTEM=="usb", SYSFS{idVendor}=="157e", SYSFS{idProduct}=="3013", RUN+="/sbin/modprobe rt2870sta"
```6) Get the device ready

```
sudo service udev reload
```Unplug your device. Wait a couple of seconds and plug it back in. You should now have wireless!

---

### Post by calande on 2011-05-22
I'm thinking about buying a TEW-645UB too, how does it work? Are you satisfied? Does it hang like the TEW-649UB? Thanks,

---

