---
title: "Problem with my wireless card on ubuntu 11.10"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by Drew44 on 2011-12-10
Hi i have just installed Ubuntu 11.10
 and my wireless card is not detected which luckily for me my wireless card has a driver disk which from the information it gives me says it has a linux driver but the instructions it has given me are not very clear for me could somebody here guide me thorough the driver installation process on ubuntu 11.10 so i can get my wireless card working ?

---

### Post by Drew44 on 2011-12-10
Anyone ?

---

### Post by bogan on 2011-12-10
> **Drew44 said:**
> Hi i have just installed Ubuntu 11.10
 and my wireless card is not detected which luckily for me my wireless card has a driver disk which from the information it gives me says it has a linux driver but the instructions it has given me are not very clear for me could somebody here guide me thorough the driver installation process on ubuntu 11.10 so i can get my wireless card working ?
Hi! ,** Drew44**
Please post detail of:
 Wireless card or dongle, Type, Model, Vendor.
 Your computer and the systems you have installed.
 ( eg. is it  Dual boot with Windows? Edit: Is it a new Install of UBUNTU 11.10, or an upgrade from a different previous working version ? )
Do you have direct internet access from this computer, eg by wired Ethernet?
Has the wireless worked with other installations, Windows or Linux?
Please post output from>  lsusb [ if card is a USB device; otherwise post>  lspci or both if you are not sure. ]

I am not the expert you need but I may be able to steer you, in any case such details are necessary.
There is a well-known acronym: RTFM! applicable to computers as well as other devices: but in the case of these Forums it should be: FRTFS!  == FIRST READ THE forum STICKIES ! 
See **bapoumba **above.

CHAO!** , bogan**

---

### Post by Drew44 on 2011-12-15
Here is the details it gave me after i entered the specified command :

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 06a3:0728 Saitek PLC 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1532:0017 Razer USA, Ltd

---

### Post by Drew44 on 2011-12-15
Here is the details it gave me after i entered the specified commands 

first command :

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 06a3:0728 Saitek PLC 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1532:0017 Razer USA, Ltd 

Second command :

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF110 [GeForce GTX 570 HD] (rev a1)
01:00.1 Audio device: nVidia Corporation GF110 High Definition Audio Controller (rev a1)
03:00.0 USB Controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
05:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
06:00.0 Network controller: Ralink corp. Device 3062
06:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


I have a dual boot installation of ubuntu 11.10 and windows 7 64 bit home premium and the wireless card works perfectly fine 
on windows just not for ubuntu at the moment i am currently using ubuntu via a wired connection to reply to your post
and finally yes it is a recent install only a month or so.

Also here is the driver and the instructions it provided for a linux distribution :

[http://www.mediafire.com/file/jq4zd30j6a2yq7b/Linux.zip](http://www.mediafire.com/file/jq4zd30j6a2yq7b/Linux.zip)

---

### Post by bogan on 2011-12-15
Hi!, **Drew44**,
Please post what entries Windows Device Manager shows for Network Adapter and the Driver used'. [ Right click on the Adapter and select Properties.]
I am a bit out of my depth in that I do not recognize anything significant from your post, to be certain.

Chao! **bogan**,

---

### Post by ratcheer on 2011-12-15
Ok, it appears that you have an Ralink 3062, just like mine. You need to download the driver from Ralink's web site and install it according to their instructions. I will look up instructions I have posted several times before and give you a link

Tim

---

### Post by ratcheer on 2011-12-15
See post #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=1869952&highlight=rt3562sta](http://ubuntuforums.org/showthread.php?t=1869952&highlight=rt3562sta)

Tim

---

### Post by bogan on 2011-12-16
Hi! **Ratcheer**,

Thanks for intervening, I was not sure if the Ralink was a wireless Adapter or not.

I will bow out of this one.

Chao! ,** bogan.**

---

### Post by ratcheer on 2011-12-16
> **bogan said:**
> Hi! **Ratcheer**,

Thanks for intervening, I was not sure if the Ralink was a wireless Adapter or not.

I will bow out of this one.

Chao! ,** bogan.**

No problem. Feel free to stay.

Tim

---

### Post by Drew44 on 2011-12-17
i have tried to copy the instructions from the post you specified but i cannot seem to find the wireless folder you mentioned in step one is that a problem or am i just looking in the wrong area ?

Ok, did you follow all the steps to install it?

1) Copy RTA2860STA.dat to /etc/Wireless/RT2860STA/  <- i cannot find this area 

2) Made sure rt2860.bin is in /lib/firmware/ ? If not, download the firmware from Ralink, extract, and copy it there.

3) sudo make (run from the extracted driver directory, e.g., DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 on my system).

4) sudo make install (assuming step 3 works).

5) sudo modprobe rt3562sta

---

### Post by ratcheer on 2011-12-17
Sorry, you usually have to create that folder.

Tim

---

