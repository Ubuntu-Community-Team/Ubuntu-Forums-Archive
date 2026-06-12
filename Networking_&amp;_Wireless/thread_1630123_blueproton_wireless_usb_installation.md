---
title: "blueproton wireless usb installation"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by the_doctor1994 on 2010-11-24
i have a blueproton high power 802.11b/g/n USB adapter with a driver disk and a desktop computer with ubuntu 10.10 but do not know how to install the drivers to make it work with my wireless network. pls help me :D

---

### Post by Kernelingus on 2010-11-24
The first thing you'll want to know is what chipset your adaptor is using.  Find out by plugging it into one of your USB ports, then open up a terminal and type

> lsusb

The output will list all the ports on your USB root hub and any devices connected to it.  Once we know what chipset you're working with, then we can start looking for drivers.  (You might already have them... it might even have kernel support.)

But start by doing the above.

---

### Post by gamebusterzade on 2010-11-24
i would use WINE unless it is Linux compatible

if it is, there should be a tarball(*.tar) on the CD u will need to dig for it

---

### Post by Kernelingus on 2010-11-24
No, don't do that.  WINE won't do anything for your Windows drivers on Linux.  (ndiswrapper might, but that's another matter, and oughtn't be at the top of anyone's list of solutions.)

Just plug the little sucker in.  If its chipset is something like the RealTek 8187 (and I bet it is), it'll just work--the drivers are already part of your kernel.

Microsoft has managed to trick a lot of people into thinking everyone ought to install whatever's on the CD that comes with whatever they buy in the store.  This couldn't be further from the truth.  If this little adapter doesn't "just work," I assure you that getting it to work won't take too much wrangling.  :)

---

### Post by gamebusterzade on 2010-11-24
> **Kernelingus said:**
> Just plug the little sucker in.  If its chipset is something like the RealTek 8187 (and I bet it is), it'll just work--the drivers are already part of your kernel.

well tell me then why my blueproton usb didn't work in Linux and it has a realtek RTL8187L
chipset in it 

it works fine in windows

id use WINE to cheat(and then all works)

or if i have time i would use the programs they sent with it 

there should be a folder buried on the disk with the tarball(*.tar) need to do so

---

### Post by chili555 on 2010-11-24
I am not aware of how to use the Windows install disk with Wine to get a wireless device to work in Linux. Are you using Wine to extract the .inf and .sys file to use in ndiswrapper? Please help us understand.

---

### Post by the_doctor1994 on 2010-11-25
if it helps, i know the adapter is compatible and the installation disk has a folder in it that is named linux. i know the drivers are in there, i just dont know how to install them from the disk. there is also a README in the linux folder with an inventory but it does not explain how to install

---

### Post by chili555 on 2010-11-25
> **the_doctor1994 said:**
> if it helps, i know the adapter is compatible and the installation disk has a folder in it that is named linux. i know the drivers are in there, i just dont know how to install them from the disk. there is also a README in the linux folder with an inventory but it does not explain how to installAs was requested, please plug the device in and run:```
lsusb
```I'd also love to see:```
sudo modprobe rtl8187
iwconfig
```Thanks.

---

### Post by the_doctor1994 on 2010-11-30
"lsusb" reads: ID = 0bda:8174  Realtek Semiconductor Corp

"sudo modprobe rtl8187" reads: blank
iwconfig reads: no wireless extensions

---

### Post by chili555 on 2010-11-30
Ah, ha! Unlike our colleague above, your device is not an RTL8187L chipset. Yours is a Realtek 8192 chipset. It is supposed to work with the driver module r8192s_usb. Sometimes, it doesn't spring to life because of missing or wrong firmware. Please do:```
sudo modprobe r8192s_usb
dmesg | grep 819
```If firmware is the issue, can you please post the result so we can troubleshoot.

---

### Post by the_doctor1994 on 2010-11-30
"sudo modprobe r8192s_usb" reads blank

"dmesg" reads the following
"[  129.159521] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  129.169867] ieee80211_crypt: registered algorithm 'NULL'
[  129.169873] ieee80211_crypt: registered algorithm 'TKIP'
[  129.169876] ieee80211_crypt: registered algorithm 'CCMP'
[  129.169879] ieee80211_crypt: registered algorithm 'WEP'
[  129.169881] 
[  129.169882] Linux kernel driver for RTL8192 based WLAN cards
[  129.169884] Copyright (c) 2007-2008, Realsil Wlan
[  129.169938] usbcore: registered new interface driver rtl819xU"

and "grep 819" did nothing. it looked like it was going to do something but then the curser just blinked until i stopped it

---

### Post by chili555 on 2010-11-30
```
dmesg | grep 819
```This is all one command. Did you run it that way?

---

### Post by the_doctor1994 on 2010-11-30
sorry i'm so noobish >.<

this is what it printed:
[    0.095819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[  129.159521] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  129.169882] Linux kernel driver for RTL8192 based WLAN cards
[  129.169938] usbcore: registered new interface driver rtl819xU

---

### Post by chili555 on 2010-11-30
No worries; we were all noobish at one time. Please let me see:```
dmesg | grep -i firmware
ls -al /lib/firmware/RTL8192SU
```We'll get to the bottom of this!

------------------

Hint to chili: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034)

Post #35

---

### Post by the_doctor1994 on 2010-11-30
the first command simply skipped a line with no output

the second command said "ls: cannot access /lib/firmware/RTL8192SU: no such file or directory"

---

### Post by chili555 on 2010-12-01
The module r8192s_usb is correct for your device and I wonder why it doesn't grab your device and take off. The firmware that's required to drive your device is not present (however, that's easily fixable) and yet there are no complaints in the kernel messages, *dmesg*. Let's run a test. Open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you remove and re-insert the device. Messages will appear in the terminal showing dis- and re-connection. Copy and paste the messages into a text document (Applications > Accessories > Text Editor). Post the text here. Thanks.

---

### Post by the_doctor1994 on 2010-12-05
Dec  5 11:39:13 grayson-desktop kernel: [   36.882291] type=1505 audit(1291567153.115:13):  operation="profile_load" pid=760 name="/usr/sbin/cupsd"
Dec  5 11:39:13 grayson-desktop kernel: [   36.895455] type=1505 audit(1291567153.127:14):  operation="profile_load" pid=761 name="/usr/sbin/mysqld-akonadi"
Dec  5 11:39:13 grayson-desktop kernel: [   37.638313] [drm] Initialized drm 1.1.0 20060810
Dec  5 11:39:13 grayson-desktop kernel: [   37.646980] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 11:39:13 grayson-desktop kernel: [   37.648458] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
Dec  5 11:39:13 grayson-desktop kernel: [   37.650547] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
Dec  5 11:39:13 grayson-desktop kernel: [   37.650571] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Dec  5 11:39:13 grayson-desktop kernel: [   37.650643] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Dec  5 11:41:31 grayson-desktop kernel: [  175.600023] usb 1-8: new high speed USB device using ehci_hcd and address 3
Dec  5 11:41:31 grayson-desktop kernel: [  175.735151] usb 1-8: configuration #1 chosen from 1 choice
Dec  5 11:43:54 grayson-desktop kernel: [  318.250333] usb 1-8: USB disconnect, address 3
Dec  5 11:44:00 grayson-desktop kernel: [  324.024033] usb 1-7: new high speed USB device using ehci_hcd and address 4
Dec  5 11:44:00 grayson-desktop kernel: [  324.158648] usb 1-7: configuration #1 chosen from 1 choice

---

### Post by chili555 on 2010-12-05
I am mystified. I see no indication at all that it's a wireless device or any identifiers at all. What is on the driver CD? Can you please attach the README to your reply?

---

### Post by the_doctor1994 on 2010-12-05
2 attatchments. the readme file and a screenshot of the contents of the "driver" folder

---

### Post by chili555 on 2010-12-05
Let's see if we can get the firmware in the right place before we take more drastic steps. Drag and drop the .tar.gz file to your desktop. Right-click it and select 'Extract here.' Inside the folder that gets created should be the firmware file; perhaps in its own folder. Open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192SU
cd Desktop/rtl8712
```Press 'Tab' and the remainder will fill in. If the firmware is in its own folder, do:```
cd firmware_folder
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
sudo modprobe r8192s_usb
dmesg | grep 819
```Any activity? Improvements? Good news?

---

### Post by the_doctor1994 on 2010-12-05
there is no file "rtl8192sfw.bin"

---

### Post by the_doctor1994 on 2010-12-05
sorry for the re-post

---

### Post by chili555 on 2010-12-05
Your case gets more interesting by the moment! Your usb.id 0bda:8174 is claimed by both 8712u and r8192s_usb. Some blacklisting may be required. We could grab the firmware and see if we could get your device going. Or, we could compile the file provided with your device. I side with the manufacturer.

In order to compile the driver from the tar.gz file, you need to install *linux-headers-generic* and *build-essential*. Please drop your install CD in the tray and open a terminal:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
```Next, do:```
cd Desktop/rtl8
```Press Tab and the remainder will fill in.```
sudo su
make
make install
modprobe 8712u
exit
```Is your wireless working?

---

### Post by the_doctor1994 on 2010-12-05
i think i may need an internet connection to download those packages...?

---

### Post by chili555 on 2010-12-06
An internet connection would certainly make our lives easier. Can you do that?

The problem is here:> grayson@grayson-desktop:~$ sudo apt-cdrom add

[sudo] password for grayson: 

Using CD-ROM mount point /media/cdrom0/

Identifying.. [5193af64758e4c3a821510cd0204be23-2]

Scanning disc for index files..

Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?Are you sure you had the correct Ubuntu install disc in the tray? Did the CDROM drive do its usual whir and hum and recognize the CD? Did an icon appear on your desktop identifying it as Ubuntu whatever?

---

### Post by the_doctor1994 on 2010-12-09
> **chili555 said:**
> 
In order to compile the driver from the tar.gz file, you need to install *linux-headers-generic* and *build-essential*. Please drop your install CD in the tray and open a terminal:

did you mean the Ubuntu install disk? i was trying to use the realtek install disk

---

### Post by chili555 on 2010-12-09
> did you mean the Ubuntu install disk?Yes, please.

---

### Post by the_doctor1994 on 2010-12-13
i put in the ubuntu install disk and this is what the code said

---

### Post by chili555 on 2010-12-13
It wants g++ and dpkg-dev. You might try downloading here: [http://packages.ubuntu.com/maverick/g++](http://packages.ubuntu.com/maverick/g++) and here: [http://packages.ubuntu.com/maverick/dpkg-dev](http://packages.ubuntu.com/maverick/dpkg-dev)

Be sure to get the i386 or the AMD64 version of g++ as appropriate. dpkg-dev is for either architecture. I suggest you download them on a USB key and drag and drop them to the Ubuntu computer's desktop. Then in a terminal, do:```
cd Desktop
sudo dpkg -i g++*
sudo dpkg -i dpkg-dev*
```The wildcard * makes it unnecessary to fill in thee exact version. Then try again to install build-essential as above.

---

### Post by the_doctor1994 on 2010-12-13
G++ didn't want to install

```
 grayson@grayson-desktop:~/Desktop$ sudo dpkg -i dpkg-dev*
Selecting previously deselected package dpkg-dev.
(Reading database ... 146595 files and directories currently installed.)
Unpacking dpkg-dev (from dpkg-dev_1.15.8.4ubuntu3_all.deb) ...
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on libdpkg-perl (= 1.15.8.4ubuntu3); however:
  Package libdpkg-perl is not installed.
 dpkg-dev depends on xz-utils; however:
  Package xz-utils is not installed.
dpkg: error processing dpkg-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 dpkg-dev
grayson@grayson-desktop:~/Desktop$ 
```

and neither did the other one

---

### Post by chili555 on 2010-12-14
I don't know what to tell you. I just downloaded the live CD and ran it. I did not connect to my wireless access point, nor did I have an ethernet connection. I added the CD as an apt source as above and installed build-essential perfectly. Of course, there were the expected errors when it was unable to reach the on line repositories.

Maybe the gods of Mark and Linus were not with you. Please try the process again. If it doesn't work, I have only one suggestion left. That is to go through each dependency and try to install it either with:```
sudo apt-get install g++
```Or get the package from Ubuntu package search: [http://packages.ubuntu.com/maverick/allpackages](http://packages.ubuntu.com/maverick/allpackages)

I have no idea why it wouldn't install from the CD.

---

### Post by the_doctor1994 on 2011-02-02
new information: dmesg grep 819 reads this...

[   85.796737] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   85.818936] Linux kernel driver for RTL8192 based WLAN cards
[   86.033332] usbcore: registered new interface driver rtl819xU
[   86.206321] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   86.206693] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   86.219482] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   86.219807] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   86.219813] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   86.250543] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   86.250752] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   86.266489] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   86.266757] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   86.266763] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

this came from the messages log
Feb  2 16:43:41 vargo3867 kernel: [ 1210.612342] usb 1-7: USB disconnect, address 3
Feb  2 16:43:44 vargo3867 kernel: [ 1213.900056] usb 1-7: new high speed USB device using ehci_hcd and address 4
Feb  2 16:43:44 vargo3867 kernel: [ 1214.072097] ==>ep_num:4, in_ep_num:1, out_ep_num:3
Feb  2 16:43:44 vargo3867 kernel: [ 1214.072101] ==>RtInPipes:3  
Feb  2 16:43:44 vargo3867 kernel: [ 1214.072104] ==>RtOutPipes:4  6  13  
Feb  2 16:43:44 vargo3867 kernel: [ 1214.072109] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
Feb  2 16:43:44 vargo3867 kernel: [ 1214.072112] 1  1  0  0  2  2  2  2  2  
Feb  2 16:43:44 vargo3867 kernel: [ 1214.251976] Dot11d_Init()

after trying to use the "make" command:

[email]root@vargo3867:/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta[/email]# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.35-22-generic/build M=/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/cmd/rtl871x_cmd.o
In file included from /home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/cmd/rtl871x_cmd.c:21:
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:347: error: implicit declaration of function &#8216;daemonize&#8217;
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:348: error: implicit declaration of function &#8216;allow_signal&#8217;
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:348: error: &#8216;SIGTERM&#8217; undeclared (first use in this function)
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:348: error: (Each undeclared identifier is reported only once
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:348: error: for each function it appears in.)
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:355: error: implicit declaration of function &#8216;signal_pending&#8217;
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:357: error: implicit declaration of function &#8216;flush_signals&#8217;
In file included from include/linux/usb.h:21,
                 from /home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_intf.h:13,
                 from /home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/rtl871x_io.h:7,
                 from /home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/drv_types.h:58,
                 from /home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/cmd/rtl871x_cmd.c:22:
include/linux/sched.h: At top level:
include/linux/sched.h:2008: warning: conflicting types for &#8216;flush_signals&#8217;
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:357: note: previous implicit declaration of &#8216;flush_signals&#8217; was here
include/linux/sched.h:2115: warning: conflicting types for &#8216;daemonize&#8217;
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:347: note: previous implicit declaration of &#8216;daemonize&#8217; was here
include/linux/sched.h:2316: error: static declaration of &#8216;signal_pending&#8217; follows non-static declaration
/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/include/osdep_service.h:355: note: previous implicit declaration of &#8216;signal_pending&#8217; was here
make[2]: *** [/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2
[email]root@vargo3867:/home/genevieve/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091013.p1.Beta[/email]# make install
make: *** No rule to make target `install'.  Stop.

---

### Post by walt.smith1960 on 2011-02-02
Perhaps this is another case  of this bug.  The error message is very similar:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

---

### Post by chili555 on 2011-02-02
> **walt.smith1960 said:**
> Perhaps this is another case  of this bug.  The error message is very similar:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)Exactly. It's simply missing the firmware. Post back if you need further aiistance.

---

### Post by the_doctor1994 on 2011-02-13
> **walt.smith1960 said:**
> Perhaps this is another case  of this bug.  The error message is very similar:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)
this worked perfectly. thank you so much!

---

