---
title: "SN9C103 webcam driver intallation- help?"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by What_the_deuce on 2007-06-21
Ok, I recently found a driver for the "SN9C103" webcam, but it requires a lot of editing files and such that i don't know how to do. here re the instructions, if anyone can make a more detailed howto, specifically for feisty, It would be very appreciated.

```
5. Driver installation
======================
As noted above, kernel 2.6.19 is the minimum for this driver; for it to work
properly, the driver needs kernel support for Video4Linux and USB.

The following options of the kernel configuration file must be enabled and
corresponding modules must be compiled:

	# Multimedia devices
	#
	CONFIG_VIDEO_DEV=m

To enable advanced debugging functionality on the device through /sysfs:

	# Multimedia devices
	#
	CONFIG_VIDEO_ADV_DEBUG=y

On the contrary, to disable the debugging functionality, it's necessary to both
set CONFIG_VIDEO_ADV_DEBUG=n and remove its definition from the Kbuild file
provided with the SN9C1xx driver.

	# USB support
	#
	CONFIG_USB=m

In addition, depending on the hardware being used, the modules below are
necessary:

	# USB Host Controller Drivers
	#
	CONFIG_USB_EHCI_HCD=m
	CONFIG_USB_UHCI_HCD=m
	CONFIG_USB_OHCI_HCD=m

The SN9C103, SN9C105 and SN9C120 controllers also provide a built-in microphone
interface. It is supported by the USB Audio driver thanks to the ALSA API:

	# Sound
	#
	CONFIG_SOUND=y

	# Advanced Linux Sound Architecture
	#
	CONFIG_SND=m

	# USB devices
	#
	CONFIG_SND_USB_AUDIO=m

Moving along to the SN9C1xx driver: after having downloaded the package,
decompress and compile:

	[user@localhost home]$ tar xvzf sn9c1xx-v.vv.tar.gz
	[user@localhost home]$ cd sn9c1xx-v.vv

(where "v.vv" has to be substituted with the version of the package just
downloaded)

It is necessary to properly configure your particular kernel source tree before
compiling the driver. The modular building process is used; therefore you must
have read and write access to your kernel source tree. If not, log in as root
before running the following commands:

	[user@localhost sn9c1xx-v.vv]$ make clean
	[user@localhost sn9c1xx-v.vv]$ make modules

If the commands fail, control the Makefile and change the path to the kernel
source tree or to any other files, according to your system configuration;
then run the previous commands again.

If everything went well, the SN9C1xx driver can be used either immediatly
(skip to the next paragraph) or be installed.

The driver will not be installed in the default directory reserved for modules
being built outside the kernel. This means that the possible version of the
driver present in the official Linux kernel tree might be overwritten during
the installation process.

To install the driver, run as root:

	[root@localhost sn9c1xx-v.vv]# make modules_install
```

I would like to be able to use this with aMSN, so if anyone can help with that too, it would be nice

---

### Post by What_the_deuce on 2007-06-22
For a start, could someone tell me where the kernel configuration file is?

---

### Post by protorox on 2008-04-28
kernel configuration file is at:
/usr/src/linux-headers-x.x.xx-xx/.config

---

### Post by Skretch on 2008-04-29
I couldn't create a new Thread so I am posting my information here:
I was trying to setup a Intuix Webcam that has so many different names like emtec, microdia, truemedia and so on.
After connecting my webcam to a usb port on my computer I did "lsusb"(lsusb lists all usb ports on the computer with information on the connected clients(hardware)) with the following result:
```
Bus 001 Device 006: ID 0c45:6011 Microdia
```
(only the interesting to us result is showed above)
After ID there is the following statement: 0c45:6011.
0c45 -every manufacturer has his own id coded in hex.0c45 stands for Microdia
6011 - is the product ID. in our cast Microdia has many products and by using 6011 we can find our product among others.

I tried all possible drivers out there and no one worked for me. I found a patch for gspca v1-2007 12 24
and after applying, compiling, and testing it, I attached it to the forum.
You will need to have the linux sources before trying to compile it on your computer: 
```
sudo apt-get install kernel-package linux-source build-essential
```

Download the archive and unzip it with the following command:
```
tar -zxvf gspcav1-20071224-0c45:6011.tar.gz
```
the go in to the extracted folder:
```
cd gspcav1-20071224/
```
and compile the patched source:
```
make
```
then before testing the driver type the following:
```
sudo  modprobe fuse
```
```
sudo modprobe videodev
```
```
sudo modprobe compat-ioctl32
```
the try the compiled module by issuing:
```
sudo insmod ./gspca.ko
```
Plug-in your webcam and test it. My webcam worked fine with Skype.
If the test was successful install the module by running:
```
sudo make install
```

Comment and make it better :)
In case you are wondering what's inside your webcam:
```
**Bridge:** SN9C101
**Image sensor:** OV6650
```

**[SIZE="6"]Patched Source:[/SIZE]**
```
http://www.cspath.com/gspcav1-20071224-0c45:6011.tar.gz
```

---

