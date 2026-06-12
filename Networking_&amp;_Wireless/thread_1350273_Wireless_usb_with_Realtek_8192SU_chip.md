---
title: "Wireless usb with Realtek 8192SU chip"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by jastonas on 2009-12-09
Is there anyone who has this chip and managed to get it working?
I have tried several ways without managing. My wireless usb adapter is Belkin F5D8053 v6 which has a different chipset from v1-5 and that made it even more confusing since there is almost nothing on the internet for the specific adapter and chipset.

I just found a driver which I havent tried yet since the computer whith the 8192su is at home
If anyone cares to try, [http://netload.in/index.php?id=10&file_id=7ZAjfzWkvE&s=4351ea142e&captcha=1](http://netload.in/index.php?id=10&file_id=7ZAjfzWkvE&s=4351ea142e&captcha=1)
But i am afraid its the 8192u driver, which I tried and didnt work, a bit modified.

---

### Post by chili555 on 2009-12-09
I couldn't get it to make. Perhaps this is the cause, from the release notes:> Release date = 2009-03-20
Operating system release = ubuntu 8.10 
[COLOR="Red"]Kernel version = 2.6.26[/COLOR]
Release driver version = 0001.0320.2009
Change history =
	1. Beta Release for 8192SU.Ubuntu 9.10 is up to kernel version 2.6.31-sumthin now.

---

### Post by BenAdamson on 2010-03-04
Hi, I'm also trying to find support for this wireless USB dongle. I found [this page]("http://linux-wless.passys.nl/query_part.php?brandname=Belkin") which seems to have some info on it (I have the F5D8053 v6). Does anybody have any info/help?

---

### Post by rairlie on 2010-04-06
I've been able to get this working in the latest kernel build (2.6.34-rc3) by adding the device ID of the Belkin to the rtl8192su driver - the patch is:

```
diff --git a/drivers/staging/rtl8192su/r8192U_core.c  b/drivers/staging/rtl8192su/r8192U_core.c 
index 7d0305c..2c068b8 100644 
--- a/drivers/staging/rtl8192su/r8192U_core.c 
+++ b/drivers/staging/rtl8192su/r8192U_core.c 
@@ -118,6 +118,7 @@ static const struct usb_device_id  rtl8192_usb_id_tbl[] = { 
        {USB_DEVICE(0x07aa, 0x0043)}, 
        /* Belkin */ 
        {USB_DEVICE(0x050d, 0x805E)}, 
+       {USB_DEVICE(0x050d, 0x815F)}, /* Belkin F5D8053 v6 */ 
        /* Sitecom */ 
        {USB_DEVICE(0x0df6, 0x0031)}, 
        /* EnGenius */ 
```I've submitted the patch to the maintainer so hopefully it'll show up soon. 

I built the kernel by following [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
As I use the nvidia proprietary driver I also had to rebuild that from source (as downloaded from the nvidia site). I'm running 9.10 on amd64, and so far so good.

Hope that helps :)

---

### Post by buminatrain on 2011-03-14
Hello, I have successfully loaded a 8192su by following the directions from this thread at linuxforums: 

[http://www.linuxforums.org/forum/red-hat-fedora-linux/163594-usb-wireless-drivers-problems.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/163594-usb-wireless-drivers-problems.html).

Follow the link to the Realtek site search 8192su and then download the source for the linux drivers.

Then find your device's USB ID, which will be different then the one used on that page by running

>  lsusb 

which will return something along these lines

>  Bus 001 Device 008: ID 07d1:3304 D-Link System 

you will need to replace 07d1:3304 with whatever your device returns, and make sure that when you get to modifying the source file you use capital letters... eg 07D1:3304. 

The usb_intf.c file is located in the /os_intf/linux/ directory of the uncompressed driver source.

All instructions should be suitable to Ubuntu, with the exception of: 

> yum install make gcc kernel-devel kernel-headers-`uname -r`

Instead run, 

>  uname -r 

to discover which kernel you are running.

then

> sudo apt-get install linux-headers-(insert what uname -r returned)

example
apt-get install linux-headers-2.6.32-29-generic 

You will most likely return some errors after running ./clean, but don't worry about them and continue with the instructions.

You will also have to run the last 4 commands as sudo.

> sudo insmod 8712u.ko

sudo chmod 644 8712u.ko

sudo cp 8712u.ko /lib/modules/(insert what uname -r returned again here)/kernel/drivers/net/wireless

sudo depmod -a


When your all done you should be up and running, flawlessly!

---

### Post by mcurran on 2011-08-04
After reading about 25 different solutions for this Belkin USB dongle F7D1101 v1, I finally got it working:  surprisingly with the least amount of editing necessary.

First download the latest firmware from realtek for the following realtek chip 8192su, which is actually the driver listed below (latest as of this writing):

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

RTL8192SU_usb_linux_v2.6.6.0.20110401.zip

Unzip, compile and install that driver:

cd <download directory>/rtl*/driver/rtl*;
make;
make install;

Also download the firmware:

[http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

Then place the firmware the the new directory RTL8192SU we will create in /lib/firmware/

mkdir /lib/firmware/RTL8192SU;
mv <download_directory>/rtl8192sfw.bin /lib/firmware/RTL8192SU/;

That's all I needed to do and I am getting amazing dB levels.  No need to add any modprobe configuration or udev rules files at all.  Here is my kernel version and desktop info:

<< back | track 5 [revolution]
2.6.38 - gnome - amd64

Unfortunately there is no injection support for this chip, as far as I know.

---

