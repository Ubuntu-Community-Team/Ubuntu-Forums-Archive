---
title: "Ubuntu Karmic 32bit Realtek 8192SU driver"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by ChasCrabtree on 2010-04-28
First post, and I'm going to make it a good one. I think I've done very well as very new Linux user. These forums have been a big help and I've been able to find all my answers until now. So it was time to join.
 
I have a Trendnet TES-649UB USB wireless g/b/n Ethernet adapter. It is hardware version 1.0. My research has shown that it is built on the Realtek 8129SU chipset. So far, I've followed Chili555's instructions in this thread ([http://ubuntuforums.org/showthread.php?t=1425697](http://ubuntuforums.org/showthread.php?t=1425697)) and the thread referenced within the first post. However, I did all the commands as root (sudu su).
 
I downloaded the attached driver that was posted in a different Linux forum. I assumed the commands would be the same. The tarball was moved to /root/Realtek and then the command 'tar -xvzf <file>.tar.gz' was executed. I moved into the folder created and executed commands 'make' and then 'make install'. The module created is 8712u.ko. It does show in the list when the command 'lsmod' is run.
 
After some more searching, I ran accross two more similar instances. Both were related to a firmware file. For some reason, there was no firmware folder contained in my tarball.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034) POST 23
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html) POST20
 
This is where the rest of the instructions failed (./wlan0up, etc.) and I got lost. I'm attaching all the information I can.
 
-Charles
 
*the zip file was too big to load. It can be obtained here: [http://www.opendrivers.com/driver/2101643/realtek-rtl8191su-wireless-driver-0006-linux-free-download.html](http://www.opendrivers.com/driver/2101643/realtek-rtl8191su-wireless-driver-0006-linux-free-download.html)
(rtl8191SU_usb_linux_v2.6.0006.20100226.zip)

---

### Post by chili555 on 2010-04-28
The problem is, indeed, the firmware.> sb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.binYou may have the firmware, but it may be in the wrong place. Let's check:```
sudo updatedb
locate rtl8192sfw.bin
```updatedb will take a few moments, please be patient.

On my system and, I suspect, your system, it is found in:```
/lib/firmware/RTL8192[COLOR="Red"]SE[/COLOR]/rtl8192sfw.bin
```As you can see from above, your driver is looking for it in RTL8192[COLOR="Red"]SU[/COLOR]. Let's make a directory and copy it over.```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Now, let's reload the module and see if the driver and device are working together:```
sudo rmmod -f 8712u
sudo modprobe 8712u
```Does it work now? If not, please run:```
dmesg | grep -e rtl8 -e 8712
```Look for and post the most recent entries.

---

### Post by ChasCrabtree on 2010-04-28
Well, after I made this post this morning and followed your instructions for dmesg, I started searching again (I wish I would have seen dmesg earlier!!!).  I followed your instructions to locate the firmware.  Not present, nor was there any RTLxxx folder in my firmware folder.  So I started plugging away again with the searches.  Drilled down through a few threads and came up with this link:
[http://www.mediafire.com/?zxgmyniz2hd](http://www.mediafire.com/?zxgmyniz2hd)
This file contained the firmware.  I copied it to my /lib/firmware folder.  Removed and reinserted the USB adapter and it started flashing.  Good sign.  Then network manager shows "disconnected" under Wireless Networks now rather than "device not ready" as before.
 
Unfortunately, I don't have a wireless network at the office to try and connect, but you can bet your beans I'll be checking first thing when I get home!
 
I did run the dmsg as you requested above.  Last line:
rtl819xU:Firmware Download Success!!
 
Thanks for all your help Chili.  I'm really frustrated that it ended up being so simple (knock on wood).  The tarball for the driver really should have included the most recent firmware for that driver.  After downloading the last three versions and looking in all for the firmware, I thought I was just not doing something right.  If I knew how (tarball is about 96 hours old in my vocabulary), I'd put the firmware in the directory and make a new tarball.  I'll follow up with my results once I get home.

---

### Post by ChasCrabtree on 2010-04-28
First cup of Ubuntu?  Seriously?  I'm still trying to figure out how to use the coffee maker!

---

### Post by chili555 on 2010-04-28
Thanks for your kind comments. I am betting you will connect!

Just for the benefit of the searchers, please see attached.

---

### Post by ChasCrabtree on 2010-04-28
Works like a champ.  No problems on reboot or removal/insertion of the USB device!

---

### Post by chili555 on 2010-04-29
Good work! You will have helped the searchers, too. Have fun!

---

### Post by Joe Awsome on 2010-05-06
just thought that I would mention that the link to download the driver is the wrong one. The OP put the link for **RTL8191SU** instaed of the one for the **RLT8192SU** driver. Here is the link that I found for it on the same site.
[http://www.opendrivers.com/driver/2101644/realtek-rtl8192su-wireless-driver-0006-linux-free-download.html](http://www.opendrivers.com/driver/2101644/realtek-rtl8192su-wireless-driver-0006-linux-free-download.html)

---

### Post by qhaz on 2010-06-09
Thanks guys!  I've been mucking with this one for hours . . . all working now, on lucid.  How weird the correct firmwire files are not included with the main source for the driver!

---

### Post by Rayve on 2010-06-17
Is that supposed to be in /lib/firmware itself, or in /lib/firmware/{KERNEL_VERSION} ?  I keep trying to copy the file over into /lib/firmware proper but it doesn't stick when I reboot, and inserting the dongle while up and running or trying to boot up with it plugged in will cause computer and/or boot up to instantly hang completely.  It requires a hard reboot to restore function, I can't even Ctrl+Alt+F1 to get it going.

Also, I don't see any sort of RTL messages in dmesg.

Can I create a script to copy the file over into /lib/firmware before it tries to load the driver, or is there perhaps some other solution?

Edit: From a comment in this post here ([http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/](http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/)) I tried blacklisting a conflicting driver, but still freeze upon plugging in the dongle.  :(

Thanks!

PS: See my full issue here: [http://ubuntuforums.org/showthread.php?p=9476645#post9476645](http://ubuntuforums.org/showthread.php?p=9476645#post9476645) (3rd post)

---

### Post by Rayve on 2010-06-23
Okay, I'm still struggling with this... I downloaded the combined driver mentioned and tried to make and make install, but I get these errors (make gives me a bunch of pointer errors, and make install does this):

```

candice@candice-desktop:~/ASUS_USBN10/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511$ make install
install -p -m 644 8712u.ko  /lib/modules/2.6.31-22-generic/kernel/drivers/net/wireless/
install: cannot create regular file `/lib/modules/2.6.31-22-generic/kernel/drivers/net/wireless/8712u.ko': Permission denied
make: *** [install] Error 1
candice@candice-desktop:~/ASUS_USBN10/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511$ sudo make install
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.
candice@candice-desktop:~/ASUS_USBN10/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511$ sudo make install
Makefile:9: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.
candice@candice-desktop:~/ASUS_USBN10/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100511$ 

```

When I try to use the original 8192 driver (or rather, the one updated May 2010), I get the errors from r8192_core.c because of the 2.6.31 kernel change to net_driver_ops -- these are the lines that are troublesome, and I see a bunch of patches for other devices or VBox, but nothing yet for ASUS USB-N10.  I don't know what needs to be done to have it use the new structure vs. the old which is no longer compatible with this new kernel.

```

        dev->open = rtl8192_open;
	dev->stop = rtl8192_close;
	dev->tx_timeout = tx_timeout;
	dev->do_ioctl = rtl8192_ioctl;
	dev->set_multicast_list = r8192_set_multicast;
	dev->set_mac_address = r8192_set_mac_adr;
	dev->get_stats = rtl8192_stats;

```

Any ideas?

Here are some patches which have fixed other devices - so it should be fairly similar, no?

[http://www.virtualbox.org/ticket/4264](http://www.virtualbox.org/ticket/4264)
[http://lodge.glasgownet.com/2009/05/31/rndis-modem-linux/comment-page-1/](http://lodge.glasgownet.com/2009/05/31/rndis-modem-linux/comment-page-1/)

I also tried upgrading to 10.04, but I had too many non-related troubles with that I've gone back to 9.10 (64-bit, if that necessitates any changes)... and this is about where I am at.  Any trouble would be greatly appreciated!!

---

### Post by rocksockdoc on 2011-04-25
Yesterday, I tried to get an external WiFi radio to work in my Ubuntu 10.04 laptop (effort detailed here):
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

On my version of a ( 2.6.32-31-generic) pristine Ubuntu 10.04 laptop installation:
```
$uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux

```At first, Ubuntu would not recognize the [Amped UA600 USB WiFi radio adapter ]("http://www.ampedwireless.com/support/model/ua600.html")when it was plugged into the laptop USB port.

```

$ ifconfig | grep wlan   
...
eth0 Link encap:Ethernet  HWaddr 00:a0:c3:3a:93:38
wlan0 Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba

```First, I determined the device identifier using 'list short USB":
```

$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 

```Then, in the /var/log/messages (dmesg | tail), I determined what driver Ubuntu was (mistakenly) looking for:
```

usb 2-1: new high speed USB device using ehci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice
r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. <=== huh?
 ...
Linux kernel driver for RTL8192 based WLAN cards
Copyright (c) 2007-2008, Realsil Wlan
...
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
rtl8192_usb_probe+0x148/0x191 [r8192s_usb]       **[COLOR=DarkRed]<==== NOTE: This will be useful for the modinfo [/COLOR]**command syntax!
...
usbcore: registered new interface driver rtl819xU [COLOR=DarkRed]**  <=== NOTICE the "U" (Ubuntu has only the "E")**[/COLOR]
usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
...
usb 2-1: USB disconnect, address 3
...

```Placing that keyword into "module information", I could see the desired driver:
```

$ modinfo r8192s_usb
...
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
...

```A quick look in the  /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless directory  shows an "rtl818x" directory with the following contents:

```

$ ls -alsF /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/*
...
44 -rw-r--r--  1 root root 43176 2011-04-08 16:36 rtl8180.ko
72 -rw-r--r--  1 root root 73640 2011-04-08 16:36 rtl8187.ko

```The problem appears to be that Ubuntu is looking for the following location  (which doesn't exist):
```

$ ls /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
...
ls: cannot access /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin: No such file or directory

```The file exists (rtl8192sfw_bin); it's just in a different location on Ubuntu:
```

$ ls -alsF /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**
...
/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin

```[Post #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") and [post #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36") of [this thread]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17") provided a (different sized, same-named file):
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")



Here's what I did to obtain that differently-sized file (I guess I should call it a "driver"):
```

http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    $ gunzip rtl8192sfw.bin.gz
    $ sudo mkdir /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**
    $ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/.

```Finally, I was able to get Ubuntu to recognize the external WiFi radio when plugged in:
```

$ ifconfig | grep wlan
...
wlan0     Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
wlan1     Link encap:Ethernet  HWaddr f8:78:8c:a1:45:f4

```Now that the driver is finally working, I can get back to the original question asked in that thread:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by StevenTenLepszy on 2012-03-11
Have somebody RTL8191SU/RTL8192SU drivers which works with Monitor Mode?

I need that :/

---

