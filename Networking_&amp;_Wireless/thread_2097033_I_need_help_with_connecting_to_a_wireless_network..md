---
title: "I need help with connecting to a wireless network."
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by tasty pants on 2012-12-21
Hello. I have recently installed Ubuntu 12.1 on my dell latitude d630 and it is running with windows. When I boot windows, it immediately connects to my wifi, but when I boot Ubuntu and click the wireless networks button on the menu at the top, there are no networks on which I can connect. Please help.

---

### Post by TOMBSTONEV2 on 2012-12-22
I assume you are using the default connection manager? What brand is the wireless network card in question? Perhaps there is a restricted propriety driver which has not been enabled yet. Check the additional drivers. (Dash > search drivers, select additional drivers) Lol is your wireless turned on? (I tried to diagnose this same thing once and realized for some reason my wireless key just needed to be pressed after a fresh install)

If you are still having problems open a terminal and type iwconfig and rfkill list all 
Post the results of these.

---

### Post by tasty pants on 2012-12-22
I must apologize, but I don't know about half the things you said. How do I turn on my wireless key? Also, after typing iwconfig it gave me this
Eth0 no wireless extensions.
Lo no wireless extensions.
When I typed rfkill it gave me
Usage: rfkill [options] command
Options:
--version.            Show version (0.4-1ubuntu3 (Ubuntu) )
Commands:
Help
Event
List [identifier]
Block identifier
Unblock identifier
Where identifier is the index no. of an rfkill switch or one of:
<idx> all wifi Bluetooth uwb ultrawideband wimax wwan gps fm

---

### Post by TOMBSTONEV2 on 2012-12-22
My apologies, it was an error on my behalf as well. The rfkill one needed a list all after it, I made it sound like I was telling you to list all.

```
rfkill list all
```It seems to me that you have no drivers installed for your card, or the card is not being detected. 


Here is what I think will get you going after much research on this:

Open terminal type

```
sudo apt-get autoremove bcmwl-kernel-source
``` then type

```
sudo apt-get install firmware-b43-installer
```

Though you will need an internet connection for this, do you have an ethernet cable by any chance?

---

### Post by tasty pants on 2012-12-22
I do not have any drivers installed on Ubuntu. Also, the only way I can connect to the internet is wirelessly, thus i have to download any drivers from windows XP. I have been to other sites to donwnload the correct drivers and then had to save them to a flashdrive as well as any instructions I could find. The instructions I did find I could not understand.

---

### Post by TOMBSTONEV2 on 2012-12-22
Ack! These crazy broadcom drivers.

First on a computer with internet;

Go here and download Quantal Quetzal release: 

```
https://launchpad.net/ubuntu/+source/b43-fwcutter
```

Download this next

```
[http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2) 
```

Put that onto your flash drive
Boot ubuntu and insert your flash drive. Copy the downloaded files to your home folder. 

Enter this into a terminal to install b43-fwcutter:
```
sudo dpkg -i b43-fwcutter
```

Then type this to install firmware driver for your wireless card:
```
tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
```

then
 
```
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```Restart your computer

Open terminal and paste

```
sudo modprobe b43
```

In theory this will do it. I am quite confident in this.

If not refer to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Near the bottom of the page; b43 No Internet Access
Feel free to get back to me if you get terminal errors.

---

### Post by tasty pants on 2012-12-22
This was my error when entering the first code:
dpkg: error processing b43-fwcutter (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 b43-fwcutter

---

### Post by TOMBSTONEV2 on 2012-12-23
Ok, after some more searching, and brain taxing download this:

[https://launchpad.net/debian/sid/+source/b43-fwcutter/1:015-14/+files/b43-fwcutter_015.orig.tar.bz2](https://launchpad.net/debian/sid/+source/b43-fwcutter/1:015-14/+files/b43-fwcutter_015.orig.tar.bz2)

Move file to home, than right click the file and select extract.

In terminal type ```
cd /home/tombstone/b43-fwcutter-015
``` (Replace tombstone with your user name)
Then type: 
sudo make
Then 
sudo make install

This _WILL _install fwcutter, ah progress. :D

Next move the file broadcom-wl-5.10.56.27.3_mipsel.tar.bz2 (download at  "  [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2) ") to your home folder. 

In terminal type:

```
tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
```then
```
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```Restart your computer, then terminal ```
sudo modprobe b43
```Hopefully after all this you will have internet! (I'm 95% sure you will)

---

### Post by tasty pants on 2012-12-23
Another error with the first code:
bash: cd: /home/fhps/b43-fwcutter-015: No such file or directory

---

### Post by Hadaka on 2012-12-23
Hi, may we have a look at what driver your card requires?
please post the output of..

```
lspci -nn | grep 0280 
```

thanks

---

### Post by tasty pants on 2012-12-23
lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86M [Quadro NVS 135M] [10de:042b] (rev a1)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by TOMBSTONEV2 on 2012-12-23
This does not make sense as I have done the exact process on my computer. So you moved the b43-fwcutter_015.orig.tar.bz2 to your home folder, then extracted it by right clicking it and selecting extract here?

Once you extract it makes a folder in your home directory called b43-fwcutter-015. The file has to be extracted first, and there has to be a space between cd and the first slash.
cd /home/fhps/b43-fwcutter-015

---

### Post by Hadaka on 2012-12-23
Hi, here is a zipped b43 file and complete instructions..read post #2
@TOMESTONEV2, perhaps you can give help with any instructions.



[http://ubuntuforums.org/showthread.php?t=1920981&highlight=b43](http://ubuntuforums.org/showthread.php?t=1920981&highlight=b43)

---

### Post by tasty pants on 2012-12-23
It worked!! Thank you so much!:p

---

### Post by Hadaka on 2012-12-23
Great!...glad to hear.
please use thread tools and mark this thread SOLVED

thanks.

---

### Post by TOMBSTONEV2 on 2012-12-23
That's very good to hear. I'm glad you got it going. =)

---

