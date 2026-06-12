---
title: "Card incompatible?"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by xXxBlender3DxXx on 2009-02-21
Can someone help me configure my wireless USB card?

I have the driver installed, the system sees the USB device, but it won't let me configure it!

It says, "[COLOR="YellowGreen"]No network configuration software found[/COLOR]" or something like that.

If this has anything to do with it, I have a:

[COLOR="DarkOrange"]D-Link DWA-120 Wireless USB Adapter[/COLOR]
[COLOR="DeepSkyBlue"]Ubuntu 8.10 64-bit (downloaded and installed yesterday from [www.ubuntu.com](www.ubuntu.com))[/COLOR]

Thanks in advance!

---

### Post by Crafty Kisses on 2009-02-21
Hey there, let's see if we can't get your wireless card up and running with ndiswrapper, if you haven't done so already, you need to install ndiswrapper, run the following:
```
sudo apt-get install ndiswrapper-common
```
Once you have ndiswrapper installed, you need to get the driver, which you can download it right [here.]("ftp://ftp.dlink.com/Wireless/DWL120/Driver/dwl120_driver_225_02.zip") When you download the driver, save it to your desktop and look for the .inf file when you extract the file, once you have the .inf file, run the following:
```
sudo ndiswrapper -i dwl120.inf
```
I'm just assuming that's what the .inf file is called, but you need to substitute the actual name. Once you have done that, you need to make sure the driver installed correctly, so run the following:
```
sudo ndiswrapper -l
```
If the driver is installed correctly, you should get results similar to this:
```
Installed ndis drivers:
{name of driver} driver present, hardware present
```
Now we have to load the ndiswrapper modules, so what you want to do is run the following commands:
```
sudo depmod -a
sudo modprobe ndiswrapper
```
Once you have done that, you're almost done, you need to make sure the modules load at every start, so run the following commands:
```
sudo ndiswrapper -m
sudo ndiswrapper -ma
```
Once the all the modules are loaded and have the correct names, you can now run the following and try to connect to your connection:
```
sudo ifdown wlan0
sudo ifup wlan0
```
Once you have done that, you should be able to connect to your wireless connection using your D-Link.

---

### Post by xXxBlender3DxXx on 2009-02-22
Oops! Ubuntu 64-bit doesn't support the drivers! Only driver is a Vista 64-bit. Here comes Ubuntu 32-bit...

---

