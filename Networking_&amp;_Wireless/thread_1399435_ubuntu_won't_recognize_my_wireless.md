---
title: "ubuntu won't recognize my wireless"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by august north on 2010-02-05
hey guys, i know this gets posted on alot, but i've spent the last 5 hours reading similar posts and got nothing. Last night I installed Kubuntu 9.10 using wubi (dualboot with Windows 7). There were no network connections available, even though I have two that can be used when I switch to Windows. After two hours I got tired of trying to fix the problem and rebooting to no avail, so i uninstalled and installed Ubuntu instead. I've still got the same problem, and after hitting a hole in my wall and shaving my head, I have no idea how to fix the problem. How do i get Ubuntu to recognize my wireless network? any suggestions at all are appreciated, and thanks in advance.
 
-august

---

### Post by imrazor on 2010-02-05
Most likely neither your wireless nor your wired NIC is supported by Linux. If you'll post the output of this command, folks might be able to help you more:```
bash> lspci
``` I'm not familiar with wubi, so it's possible it's doing some sort of hardware virtualization that's masking your network cards from Ubuntu.

---

### Post by august north on 2010-02-05
i just typed in "bash> lspci" into the terminal and nothing at all came up, just another line for me to enter something into the terminal. I tried it again, and the same thing happened. anything else?
 
wubi is just a software that installs Ubuntu directly into a windows computer so you don't have to use a cd. 
 
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by imrazor on 2010-02-05
Sorry, my syntax may have confused you. "bash>" just represents the command prompt in Terminal.  So to be a little clearer, try typing this in:```
lspci
``` at a prompt in the Terminal.

---

### Post by august north on 2010-02-05
here we go...
 
 
 
[EMAIL="august@ubuntu:-$"]august@ubuntu:-$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host -Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/Er (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/Er (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/Er (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/Er (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801 EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801 EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R)AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
02:08.0 Ethernet controler: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:0e.0 FireWire (IEEE 1394): NEC Corpration uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

---

### Post by imrazor on 2010-02-05
Ah ha! You have a Broadcom 4318 wireless chipset. The problem with a Broadcom 43xx is that there is some proprietary code in the Windows driver that can't be included (for legal reasons) in the standard repositories. First, you'll need to enable one of the non-standard repositories. I *think* the package you're looking for is in the restricted (aka, Proprietary drivers for devices) repository. From the Ubuntu menu (at the top right of your screen), go to System>Administration>Software Sources and enable the restricted repository. You may be prompted to update something at that point. Then go to a Terminal prompt and type:```
sudo apt-get install b43-fwcutter
``` In that package are several standard firmware images, one of which will probably match your card. To test your new firmware, reboot and check to see if anything shows up in the top right of your Ubuntu menubar. If not, fire up Terminal and type:```
ifconfig
```Post the output when you get a chance. If anything shows up besides "lo0", things are looking up.

---

### Post by glvortex on 2010-02-05
home@home-desktop:~$ lsusb
Bus 001 Device 003: ID 0846:9040 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Ive tried everything, cant seem to get this one to work, seems like a driver error
its a netgear wna1000 usb g/n card

---

### Post by august north on 2010-02-05
The Proprietary drivers for devices box was already checked. When I typed "sudo apt-get install b43-fwcutter" into the terminal, this is what I got-
 
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package b43-fwcutter
 
 
Was the box supposed to be unchecked instead, is that why it couldn't find the package?
I went ahead and rebooted anyways, and found nothing in the top corner. when I typed in "ifconfig" I got this-
 
 
eth0    Link encap:Ethernet   HWaddr 00:0e:a6:8d:29:c9
          UP BROADCAST MULTICAST   MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 frame:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
 
lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 frame:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
 
 
Atleast its wasn't lo0
How am I looking?

---

### Post by imrazor on 2010-02-05
OK, I went back and checked my facts and it looks like b43-fwcutter should be in the main repository. What version of Ubuntu are you using? You can check by typing in:```
lsb_release -a
``` I've been operating under the assumption you had Ubuntu 9.10 installed. You might also want to check in the upper right hand corner of your screen to see if Ubuntu is offering to install any restricted drivers.

---

### Post by bkratz on 2010-02-05
See post 9 of this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by august north on 2010-02-06
imrazor, i do have 9.10. its the desktop version. and ubuntu wasn't offering to install anything. 

bkratz, i did step for step what the other guy did, except after the initial install his hardware driver was detected, just not doing what he wanted it to do. Mine's not getting detected in the first place. i'm guessing that's a problem...

---

### Post by bkratz on 2010-02-06
did you do the steps in the first post (last half), it tells you how to get b43-fwcutter from the installation disk, since you can't seem to download it.

---

### Post by imrazor on 2010-02-06
Actually, bkratz is right. If you don't have a network connection, you won't be able to download anything from the repositories (DOH!) However, the "ifconfig" output you posted earlier seems to indicate that your wired connection is functional, but not configured.  Do you have a live network jack handy? Post a few details about your *wired* Internet connection. Is it a direct connection to the Internet, or do you have a router? Is it set up to hand out DHCP addresses?

As for your wireless connection, it sounds like you're saying you found a B43 driver under System>Administration>Hardware Drivers, but it's reported as inactive. Is that true, or am I misunderstanding what you're saying? If you fire up Terminal and run:```
sudo modprobe b43
``` what do you get?

---

### Post by FixIt PeteC on 2010-02-15
Here's the fix that worked for me! 1. Download and install compat-wireless-2010-02-01, 2. go to the compat-wireless-2010-02-01/drivers/net/wireless/ath/ar9170 folder, 3. open the file "usb.c" at line 62 there will be a list of devices with their device IDs, 4. Edit one of the existing devices to "Netgear WNA1000" and device ID "0x0846, 0x9040" you have to edit one of the existing devices since a usb driver can only control 18 devices, which are already listed. 

The ar9170usb driver is the closest match for the WNA1000, but it must recognize your device ID. If for some reason your WNA1000 device ID is different, use you IDs. I had to plug mine into a windows pc and look at its properties first.

Mine looks like: 

static struct usb_device_id ar9170_usb_ids[] = {
/* Atheros 9170 */
{ USB_DEVICE(0x0cf3, 0x9170) },
/* Netgear WNA1000 */
{ USB_DEVICE(0x0846, 0x9040) },
/* TP-Link TL-WN821N v2 */
{ USB_DEVICE(0x0cf3, 0x1002) },

If everything else in the system is correct, just reboot and there it is!

Good luck!

Don't use ndiswrapper

---

