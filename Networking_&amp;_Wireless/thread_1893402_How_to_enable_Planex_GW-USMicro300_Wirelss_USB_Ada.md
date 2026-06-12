---
title: "How to enable Planex GW-USMicro300 Wirelss USB Adapter on Ubuntu 10.04 64 bit"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by TongVigilante on 2011-12-10
I've been searching for a while for a mini USB Wireless N 300 device which would support all three major operating systems - Linux is usually the one which is forgotten when it comes to driver support.
Even though Planex do not support Linux on this device I bought it anyway and figured out a way to get the Ralink RT3070 driver working on Ubuntu by looking on various Japanese websites and general googling!
Anyway thought I'd post this guide to how I did it - it's my first ever post on the Ubuntu forum.
It worked for me on my setup - can't say if you will need to do a few more tweaks to get it up and running on your particular build but if not I think it shouldn't take much more than a few minor tweaks to get it working.


**Planex GW-USMicro300 RT3070 Driver Installation Guide**

My Machine
#Acer Revo r3610 
# Ubuntu Linux 10.04.1 LTS 64 bit wubi install on Windows 7 64 bit
# Kernel - Linux 2.6.34-020634-generic (64 bit)


1. Download Ralink RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB Drivers from [http://www.ralinktech.com](http://www.ralinktech.com)  (find drivers in Support -> Linux)

2. Extract Tar to a folder.

3. Connect GW-USMicro300, in Terminal
$ lsusb
Make a note of the line for the Planex wireless device

in particular ID aaaa:bbbb, you'll need the values aaaa and bbbb e.g

Bus 001 Device 003: ID 2019:ab29 PLANEX  

4. In extracted driver folder open \common\rtusb_dev_id.c find and edit entry for Planex RT3070 to aaaa and bbbb

e.g change USB_DEVICE(0x2019,0xAB25) to USB_DEVICE(0x2019,0xAB29)

Save file and close

5. In extracted driver folder open \os\linux\config.mk edit entries as follows:
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Save and close file.

6. Install required packages so that you can compile source code if you have n't got them already:
$ sudo apt-get install build-essential fakeroot dpkg-dev
and also Linux kernel headers so that you can compile kernel device drivers
$ sudo apt-get install linux-headers-$(uname -r) 

7. Change directory to extracted driver folder e.g
$ cd /home/username/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3
or whatever your extracted folder is called..

8. Compile the Driver
$ make
You'll probably get lots of warnings, maybe the odd error message - don't worry.

9. Install Driver
$ sudo make install 
Might also get some error messages here, but you can ignore them, seems to work anyway.

10. Reboot machine with GW-USMicro300 plugged in - wireless light should now be flashing if device driver is working
Set up your new wireless device in Network Connections manager - WPA SSID etc.
Enjoy!

Troubleshooting:

NOTE: I did not have any native default ralink drivers already installed on my machine so it worked straight away, but if you have then you might need to disable them to stop them conflicting with RT3070.
$ sudo vi /etc/modprobe.d/blacklist.conf 
then add any drivers that already installed to the list.
e.g blacklist rt2800usb

Save, close and reboot your machine

Also take a look at the README_STA_usb file in the extracted driver folder - if you need to make a few more changes to the build installation if your system is different to mine, this is the place to look. 

Hope this helps anyone else out there struggling like I was!

Good Luck! 

TongVigilante

---

### Post by owhong on 2012-02-28
Thank you!  It worked perfectly with two minor issues at my side:

1.  the folder name, where driver files are, should not contain parenthesis, e.g. /.... (2)/; make error will complain about the expected ')'

2.  I had to ran make with sudo, i.e. sudo make

Thank you very much!

---

