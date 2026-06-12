---
title: "Can't get Belkin N300 Micro USB WiFi working in 11.10"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by RickDanger on 2012-01-11
Hi,

I have Belkin N300 Micro USB WiFi adapter, which according to posts I have found here, should work out of the box with 11.10 and 3.0.0-14-generic which I have installed. I have also installed all updates available in the update center.

After booting with the USB adapter inserted;

'lsusb' gives me:

> Bus 001 Device 002: ID 050d:2103 Belkin Components

It is not listed when I try 'ifconfig -a'

'ifconfig wlan up' gives me:

> wlan: ERROR while getting interface flags: No such device

What should I try next?

---

### Post by chili555 on 2012-01-12
I am looking at this thread: [http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=1550](http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=1550)

Look at dibl's post of 26.07.2011:> Progress today. Working with this information, it appears the correct driver to load is r8192u_usb. With that module loaded, the following sets the ID: Let's try that:```
sudo su
echo -n "050d 2103" > /sys/bus/usb/drivers/rtl819xU/new_id
exit 
```If you follow along, you will see that he got stopped by the firmware. Let's find and relocate yours:```
ls /lib/firmware/RTL8192U
```Do you have three firmware files in there? If so, skip down to 'load driver.' If not, let's find and copy some:```
sudo updatedb
locate 8192 | grep .img
```updatedb will take a few moments, please be patient. You might find the files in /lib/firmware/RTL8192[COLOR="Red"]E[/COLOR]. Let's copy them over:```
sudo mkdir /lib/firmware/RTL8192U
sudo cp /lib/firmware/RTL8192E/* /lib/firmware/RTL8192U
```Now load the driver:```
sudo modprobe rtl8192u_usb
iwconfig
```If there is still no wlan0, let's see why:```
dmesg | grep 819
```If this works, we will write two quick files and make it persistent.

---

