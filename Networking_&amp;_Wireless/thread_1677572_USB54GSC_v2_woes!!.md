---
title: "USB54GSC v2 woes!!"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by rajn on 2011-01-28
:( Please help:
I would like to connect wirelessly but....
purchased this USB stick and followed a web advice.

Step 1 - Install the essentials

Step 2 - Build ndiswrapper
sudo make uninstall
make
sudo make install
sudo ndiswrapper -m


Step 3 - Getting the driver 
The only drivers in the CD are ndiswdm.sys and ndiswdm.inf. And of course I see the .cab files in Utility folder.

Step 3b - unshield to grab .cab files
sudo apt-get install unshield
In the terminal, change to the "Utilities' directory containing the .cab files and run;

unshield x data1.cab
unshield x data2.cab

:( This step failed !!!!!!!!!!!!!
However, this gives me 'Aborted' in the terminal . 
Therefore I installed the software in a different computer which has windows 7 and extracted usb8023.sys which I am not even sure is correct and another two files rndismp.sys and wusb54gscv2_amd64.sys which I see.


Step 5 - Installing drivers:confused: Not sure which are the right files???????????
In the terminal, "cd" into 'MyDrivers' directory and run this command to install the drivers:

sudo ndiswrapper -i ndiswdm.inf

sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsc/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsc/
sudo cp ndiswdm.sys /etc/ndiswrapper/wusb54gsc/


Step 6:
ndiswrapper -l

ndswdm : driver installed
wusb54gsc: invalid driver - so I removed this driver.



Step 7 -some power management of some sort???
sudo modprobe ndiswrapper
sudo nano -w /etc/udev/rules.d/99-custom.rules

BUS=="usb", SYSFS{idProduct}=="0075", SYSFS{idVendor}=="1737",  RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"




Step 8 - Configure the wireless.  
reboot

Step 9
Plug in the adapter and wait for a few moments.
ndiswrapper -l

The terminal returns

wusb54gsc : driver installed
device (1737:0075) present:P




sudo ifconfig 
only see eth 0 and loop

sudo iwconfig
lo          no wireless extension
eth0      no wireless extension


Not sure what is to be done next. I do not obviously see my wireless usb card!!!!!!!!!!:mad:

Please help either by suggesting another USB card which WILL WORK either out-of-box or with some easy efforts.
Thank you,

---

