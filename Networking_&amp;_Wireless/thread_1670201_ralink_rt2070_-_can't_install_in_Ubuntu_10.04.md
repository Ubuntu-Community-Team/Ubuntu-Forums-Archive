---
title: "ralink rt2070 - can't install in Ubuntu 10.04"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by woodrow667 on 2011-01-18
[COLOR=black][FONT=Verdana][SIZE=1]I am a total newb with linux and ubuntu. It was recommended for my older Compaq desktop with a Celeron processor and 256mb of ram. I got the windows driver installer installed, but it was looking for a inf file and the driver I have on the cd is an executable file for an installer, so it wouldn't work. The cd also has a linux driver, but I do not know how to use terminal to install it. I'm at my wits end. I feel pretty stupid, because I know nothing about linux. Can someone help a new guy out? I do apologize if this post is in the wrong place or in the wrong format.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=1]Thanks,[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=1]Woody[/SIZE][/FONT][/COLOR]
[SIZE=1][/SIZE] 
[SIZE=1]Forgot to say that this is a wirless usb dongle I'm trying to install.[/SIZE]

---

### Post by chili555 on 2011-01-18
> I know nothing about linux.All of us, at one time, even me and Linus Torvalds, knew nothing about Linux. No worries.

As fun as compiling a driver from an old, stale tar.gz might be, let's see if there isn't an easier way. Please insert your device and open Applications > Accessories > Terminal and do:```
lsusb
```Post the resultant output and we'll see what needs to be done.

---

### Post by woodrow667 on 2011-01-18
okay, I did that and had to take a pic as that computer is not connected yet. I'll try to attach the pic.

---

### Post by chili555 on 2011-01-18
This is supposed to work with the driver rt2800usb, although I am not sure it's the case in Ubuntu 10.04. Find out with:```
modinfo rt2800usb | grep 3370
```If it returns your usb.id like this, then 10.04 claims it.```
 modinfo rt2800usb | grep 3370
alias:          usb:v**148F**p**3370**d*dc*dsc*dp*ic*isc*ip*
```Let's load it and see what happens:```
sudo modprobe rt2800usb
iwconfig
```Is a wireless interface created, typically wlan0? Please post:```
dmesg | grep -i rt2
```The pipe symbol | is on the right side of my US keyboard along with \.

---

### Post by woodrow667 on 2011-01-18
Thanks, I'll go and try it

---

### Post by woodrow667 on 2011-01-18
okay, ran modinfo and it didn't give me anything

---

### Post by chili555 on 2011-01-19
Do you have wired ethernet access, even temporarily, if we need to download things? What is the name of the Linux driver on the disk? Depending on these answers, we will decide how to proceed.

---

### Post by woodrow667 on 2011-01-19
chili, i borrowed a wireless pci card and have internet access with it now. I am installing ubuntu 10.10 on another hard drive right now. I read so many fixes and have probably put so many codes in the other one that it's probably as lost as I am. Wish I had a system restore button. lol

---

### Post by chili555 on 2011-01-19
Shall I wait until 10.10 is installed before we fix your wireless?

---

### Post by woodrow667 on 2011-01-19
Wow! I can't get 10.10 to install on this clean hard drive. I'll put the other drive back in and bring it up. Please be patient. :-)

---

### Post by woodrow667 on 2011-01-19
okay, I'm back on the machine with 10.04 and on the net through the borrowed wireless pci card.

---

### Post by chili555 on 2011-01-19
What does it do or not do? I will be patient; I have to run to the PO and lunch.

---

### Post by woodrow667 on 2011-01-19
okay, I'm back on the machine with 10.04 and on the net through the borrowed wireless pci card.

---

### Post by woodrow667 on 2011-01-19
may be a while before i get back to you. I'm gonna have to take the computer in to the house and hard wire it. I'm sorry to be such a pain. be back soon.

---

### Post by woodrow667 on 2011-01-19
may be a while before i get back to you. I'm gonna have to take the computer in to the house and hard wire it. I'm sorry to be such a pain. be back soon.

---

### Post by woodrow667 on 2011-01-19
may be a while before i get back to you. I'm gonna have to take the computer in to the house and hard wire it. I'm sorry to be such a pain. be back soon.

---

### Post by woodrow667 on 2011-01-19
may be a while before i get back to you. I'm gonna have to take the computer in to the house and hard wire it. I'm sorry to be such a pain. be back soon.

---

### Post by woodrow667 on 2011-01-19
may be a while before i get back to you. I'm gonna have to take the computer in to the house and hard wire it. I'm sorry to be such a pain. be back soon.

---

### Post by woodrow667 on 2011-01-19
don't know if the other posts got through. i'm taking the computer in to the house to hard wire it using the hard drive with 10.04. couldn't get 10.10 to install.

---

### Post by woodrow667 on 2011-01-19
don't know if the other posts got through. i'm taking the computer in to the house to hard wire it using the hard drive with 10.04. couldn't get 10.10 to install.

---

### Post by woodrow667 on 2011-01-19
sorry there are so many repeat posts! Guess I was having technical difficulties. :-)

---

### Post by woodrow667 on 2011-01-19
Did some back peddling and ran some of the codes you posted earlier and here they are. Maybe it will help?
administrator@ubuntu:~$ sudo modprobe rt2800usb
administrator@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

administrator@ubuntu:~$ dmesg | grep -i rt2
[   23.388373] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   23.427291] usbcore: registered new interface driver rt2870
[ 1245.402722] usbcore: registered new interface driver rt2800usb
administrator@ubuntu:~$

---

### Post by chili555 on 2011-01-19
What is the name of the Linux driver file on the CD? We need to know if it's old and stale or if it can probably be used. Also, please post:```
uname -r
```In anticipation of compiling the file, while you are connected to the wire, do:```
sudo apt-get install linux-headers-generic build-essential
```Thanks.

---

### Post by woodrow667 on 2011-01-19
Hope this is what you're looking for on the cd. The linux driver is DPO_RT3070_LinuxSTA_V2.3.0.4_20100604

---

### Post by woodrow667 on 2011-01-19
Hope this is what you're looking for on the cd. The linux driver is DPO_RT3070_LinuxSTA_V2.3.0.4_20100604

---

### Post by woodrow667 on 2011-01-19
administrator@ubuntu:~$ uname -r
2.6.32-27-generic

---

### Post by chili555 on 2011-01-19
Well, I believe we can install that just fine. Drag and drop it from the CD to your desktop. Then right click it and select 'Extract here.' Now double-click the 2010etc. folder it creates to open it and go to os/linux/ and open the file config.mk with the text editor. Change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently '=n.' Proofread, save and close the text editor.

Open a terminal and type:```
cd Desktop/2010
```Press Tab; the remainder of the long title will automagically fill in. Now do:```
sudo su
make
make install
modprobe rt3370sta
exit
```There may be a few warnings, but if there is an error, note it and post back. 

Let us know your progress.

---

### Post by chili555 on 2011-01-19
Well, I believe we can install that just fine. Drag and drop it from the CD to your desktop. Then right click it and select 'Extract here.' Now double-click the 2010etc. folder it creates to open it and go to os/linux/ and open the file config.mk with the text editor. Change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently '=n.' Proofread, save and close the text editor.

Open a terminal and type:```
cd Desktop/2010
```Press Tab; the remainder of the long title will automagically fill in. Now do:```
sudo su
make
make install
modprobe rt3370sta
exit
```There may be a few warnings, but if there is an error, note it and post back. 

Let us know your progress.

---

### Post by chili555 on 2011-01-19
Well, I believe we can install that just fine. Drag and drop it from the CD to your desktop. Then right click it and select 'Extract here.' Now double-click the 2010etc. folder it creates to open it and go to os/linux/ and open the file config.mk with the text editor. Change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently '=n.' Proofread, save and close the text editor.

Open a terminal and type:```
cd Desktop/2010
```Press Tab; the remainder of the long title will automagically fill in. Now do:```
sudo su
make
make install
modprobe rt3370sta
exit
```There may be a few warnings, but if there is an error, note it and post back. 

Let us know your progress.

---

### Post by chili555 on 2011-01-19
Sorry about the duplicates. The forum is being a pain today.

---

### Post by woodrow667 on 2011-01-19
was doing fine until I got to make install. Here is what it said:
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# make install
make -C /home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: cannot stat `/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux'
make: *** [install] Error 2
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604#

---

### Post by chili555 on 2011-01-19
> cp: cannot stat `/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat': No such file or directoryIn that folder, do you have a file called, by chance, RT2870STA.dat? If so, please do:```
sudo su
cp RT2870STA.dat RT3070STA.dat
make install
modprobe rt3370sta
exit
```Any improvement?

---

### Post by woodrow667 on 2011-01-19
> **chili555 said:**
> In that folder, do you have a file called, by chance, RT2870STA.dat? If so, please do:```
sudo su
cp RT2870STA.dat RT3070STA.dat
make install
modprobe rt3370sta
exit
```Any improvement?
  It did not like the modprobe:
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# modprobe rt3370sta
FATAL: Module rt3370sta not found.
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604#

---

### Post by chili555 on 2011-01-19
> root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# modprobe rt3370staPlease run again:```
make install
``` Make note of the module it creates; it may be rt3070sta instead of rt3370sta. Modprobe what it built.

---

### Post by woodrow667 on 2011-01-19
> **chili555 said:**
> Please run again:```
make install
``` Make note of the module it creates; it may be rt3070sta instead of rt3370sta. Modprobe what it built.
here is what it said:
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-27-generic/kernel/drivers/net/wireless/rt3070sta.ko): Device or resource busy
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604#

---

### Post by chili555 on 2011-01-19
Please show us:```
lsmod | grep -e rt2 -e rt3
iwconfig
```Thanks.

We're very close!

---

### Post by woodrow667 on 2011-01-19
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# lsmod | grep -e rt2 -e rt3
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
rt2870sta             461811  0 
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# 

getting excited!

---

### Post by woodrow667 on 2011-01-19
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# lsmod | grep -e rt2 -e rt3
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
rt2870sta             461811  0 
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# 

getting excited!

---

### Post by chili555 on 2011-01-19
Wow! It looks like rt2870sta AND rt2800usb and all their friends have come to the party. Please run:```
lsusb
```Confirm that your usb.id is indeed 148f:3370. Now run:```
modinfo rt2870sta | grep 3370
```Any output? If not, remove it:```
sudo rmmod -f rt2870sta
```Next, do:```
modinfo rt2800usb | grep 3370
```If no output, remove it and its pals:```
sudo rmmod -f rt2800usb
sudo rmmod -f rt2x00usb
sudo rmmod -f rt2x00lib
```Now reinsert rt3070sta:```
sudo modprobe rt3070sta
iwconfig
```If the modules do not want to leave peacefully, reboot. Then run:```
sudo modprobe rt3070sta
iwconfig
```Is the wireless working now?

---

### Post by woodrow667 on 2011-01-19
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:3370 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# modinfo rt2870sta | grep 3370
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# sudo rmmod -f rt2870sta
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# modinfo rt2800usb | grep 3370
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# sudo rmmod -f rt2800usb
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# 
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# sudo rmmod -f rt2x00usb
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# sudo rmmod -f rt2x00usb
ERROR: Removing 'rt2x00usb': No such file or directory
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# sudo rmmod -f rt2x00lib
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# sudo modprobe rt3070sta
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604#

---

### Post by chili555 on 2011-01-19
Something, obviously, is amiss. Let's see if there are any messages:```
dmesg | grep -i rt2
dmesg | grep -i rt3
```Thanks.

---

### Post by woodrow667 on 2011-01-19
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# dmesg | grep -i rt2
[   23.388373] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   23.427291] usbcore: registered new interface driver rt2870
[ 1245.402722] usbcore: registered new interface driver rt2800usb
[19049.076330] Error: Driver 'rt2870' is already registered, aborting...
[19049.076340] usbcore: error -16 registering interface     driver rt2870
[19256.384650] Error: Driver 'rt2870' is already registered, aborting...
[19256.384659] usbcore: error -16 registering interface     driver rt2870
[22663.121735] usbcore: deregistering interface driver rt2870
[22704.071195] usbcore: deregistering interface driver rt2800usb
[22776.963161] usbcore: registered new interface driver rt2870
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# dmesg | grep -i rt3
root@ubuntu:/home/administrator/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# 

should I reboot?

---

### Post by chili555 on 2011-01-19
Most definitely. Please run and post afterwards:```
dmesg | grep -i rt2
dmesg | grep -i rt3
```

---

### Post by woodrow667 on 2011-01-19
administrator@ubuntu:~$ dmesg | grep -i rt2
[   26.894028] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   26.931163] usbcore: registered new interface driver rt2870
administrator@ubuntu:~$ dmesg | grep -i rt3
administrator@ubuntu:~$ 

thank you so much for helping me.

---

### Post by chili555 on 2011-01-19
Now how about:```
lsmod | grep -e rt2 -e rt3
```You are entirely welcome.

---

### Post by woodrow667 on 2011-01-19
administrator@ubuntu:~$ lsmod | grep -e rt2 -e rt33
rt2870sta             461811  0 
administrator@ubuntu:~$

---

### Post by chili555 on 2011-01-19
I don't understand why rt2870sta is loading. Are you sure the module you built was rt3070sta? What does this tell us?```
cat /etc/modules
```Thanks.

---

### Post by woodrow667 on 2011-01-19
administrator@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt2870sta
rt2870
administrator@ubuntu:~$ 

Could be because of the stuff I tried before I found you. Might be in over my head here.

---

### Post by woodrow667 on 2011-01-19
i did notice that in the main folder of the driver on the cd there is a file called rt2870sta.dat if that helps.

---

### Post by chili555 on 2011-01-19
Well, it's helping me get to 8,000 posts, isn't it. Please do:```
sudo gedit /etc/modules
```Remove the two rt2870 lines; proofread, save and close gedit. Now do:```
sudo rmmod -f rt2870sta
sudo modprobe rt3070sta
iwconfig
```Do you have a wireless interface, ra0 perhaps?

Any other confessions? We have all sinned and fallen short, etc.

---

### Post by woodrow667 on 2011-01-19
administrator@ubuntu:~$ sudo gedit /etc/modules
[sudo] password for administrator: 
administrator@ubuntu:~$ sudo rmmod -f rt2870sta
administrator@ubuntu:~$ sudo modprobe rt3070sta
administrator@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

administrator@ubuntu:~$ 
 pulling what hair I have left out. lol

---

### Post by chili555 on 2011-01-19
I have to take a break. See you tomorrow.

---

### Post by woodrow667 on 2011-01-19
okay. Thanks and sorry to be such a bother.

---

### Post by woodrow667 on 2011-01-20
chili, I got xubuntu to install on the empty hard drive. Through my reading, see I do read :-), I found that it is a lighter version of ubuntu and since that computer only has 256mb of ram, i figured it would run better. I'm trying to load the driver per your earlier instruction. I'll let you know how it turns out. 
 
Woody

---

### Post by woodrow667 on 2011-01-20
chili, I got xubuntu to install on the empty hard drive. Through my reading, see I do read :-), I found that it is a lighter version of ubuntu and since that computer only has 256mb of ram, i figured it would run better. I'm trying to load the driver per your earlier instruction. I'll let you know how it turns out. 
 
Woody

---

### Post by woodrow667 on 2011-01-20
chili, I got xubuntu to install on the empty hard drive. Through my reading, see I do read :-), I found that it is a lighter version of ubuntu and since that computer only has 256mb of ram, i figured it would run better. I'm trying to load the driver per your earlier instruction. I'll let you know how it turns out. 
 
Woody

---

### Post by woodrow667 on 2011-01-20
Well, I tried but it was a no go. Guess I'm just gonna have to buy a wireless pci card. :-(

---

### Post by woodrow667 on 2011-01-20
Well, I tried but it was a no go. Guess I'm just gonna have to buy a wireless pci card. :-(

---

### Post by woodrow667 on 2011-01-20
Still can't get the driver to install. If I posted the read me file that is on the disc, would that help?

---

### Post by chili555 on 2011-01-21
I am quite familiar with the driver. I have read the READMEsta many times. However, if there is some other file you think might help, I'd be glad to read it.

What exactly do you meaan when you say you can't install it? What step made an error? Let's do a full diagnostic. We'll create a text file, zip it up and you can post it so my colleagues and I can examine it. Please reboot and do:```
sudo modprobe rt3070sta > wood.txt
dmesg >> wood.txt
lsmod >> wood.txt
cat /etc/modules >> wood.txt
cat /etc/modprobe.d/blacklist.conf >> wood.txt
modinfo rt3070sta >> wood.txt
zip wood.zip wood.txt
```In your user directory, you will find a zip file wood.zip. Attach it to your reply. Thanks.

---

### Post by woodrow667 on 2011-01-21
when I say it doesn't install, I mean that the usb adapter doesn't work. Here is the zip file. Thanks.

---

### Post by chili555 on 2011-01-21
(The private chili, under his breath, sayeth: "Someone ought to slap the manufacturer of this poor guy's device. The driver doesn't even support the device! Now I have to rewrite it.")

Th public chili sayeth:
 Hey, Woodrow! Let's have some fun. Open the file you extracted and go to common and open rtusb_dev_id.c with a text editor. We are going to add one line in exactly the correct place without changing or disturbing anything else. Look for the section I've quoted and add the part I've highlighted. Spacing, braces, etc. must be perfect.```
#endif // RT3070 //
#ifdef RT3370
	[COLOR="Red"]{USB_DEVICE(0x148F,0x3370)}, /* Ralink 3370 */[/COLOR]
	{USB_DEVICE(0x0DF6,0x0050)}, /* Sitecom 3370 */
#endif // RT3370 //
	{ }/* Terminating entry */
};
```Proofread three or four times carefully. Save and close the text editor. Now open a terminal. Assuming you have downloaded the file to your desktop, do:```
cd Desktop/2010   <--Press Tab
sudo su
make clean
make
make install
rmmod -f rt3070sta
modprobe rt3070sta
exit
```Now is it working?

If you encounter any difficulty or problem, stop and post back.

---

### Post by woodrow667 on 2011-01-21
Here is what is in that file. I may be dumb, but I don't see the line in there that is under the line that you highlighted.
/*
 *************************************************************************
 * Ralink Tech Inc.
 * 5F., No.36, Taiyuan St., Jhubei City,
 * Hsinchu County 302,
 * Taiwan, R.O.C.
 *
 * (c) Copyright 2002-2007, Ralink Technology, Inc.
 *
 * This program is free software; you can redistribute it and/or modify  * 
 * it under the terms of the GNU General Public License as published by  * 
 * the Free Software Foundation; either version 2 of the License, or     * 
 * (at your option) any later version.                                   * 
 *                                                                       * 
 * This program is distributed in the hope that it will be useful,       * 
 * but WITHOUT ANY WARRANTY; without even the implied warranty of        * 
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         * 
 * GNU General Public License for more details.                          * 
 *                                                                       * 
 * You should have received a copy of the GNU General Public License     * 
 * along with this program; if not, write to the                         * 
 * Free Software Foundation, Inc.,                                       * 
 * 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             * 
 *                                                                       * 
 *************************************************************************

    Module Name:
    rtusb_dev_id.c
 
    Abstract:
 
    Revision History:
    Who        When          What
    ---------  ----------    ----------------------------------------------
 */

#include "rt_config.h"

/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT3070
    {USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
    {USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
    {USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
    {USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x871C)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x822C)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x871B)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x822B)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
    {USB_DEVICE(0x0DF6,0x0048)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0047)}, /* Sitecom 3071 */
    {USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
    {USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
    {USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
    {USB_DEVICE(0x083A,0xA701)}, /* SMC 3070 */
    {USB_DEVICE(0x083A,0xA702)}, /* SMC 3072 */
    {USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
    {USB_DEVICE(0x1740,0x9707)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9708)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9709)}, /* EnGenius 3072 */
    {USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
    {USB_DEVICE(0x13D3,0x3305)}, /* AzureWave 3070*/
    {USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
    {USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
    {USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
    {USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
    {USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
    {USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
    {USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
    {USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
    {USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
    {USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C16)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C17)}, /* D-Link 8070 */
    {USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
    {USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
    {USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x04BB,0x0947)}, /* I-O DATA 3070 */
    {USB_DEVICE(0x04BB,0x0948)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
    {USB_DEVICE(0x20B8,0x8888)}, /* PARA INDUSTRIAL 3070 */
    {USB_DEVICE(0x0B05,0x1784)}, /* Asus 3072 */
    {USB_DEVICE(0x203D,0x14A9)}, /* Encore 3070*/
    {USB_DEVICE(0x0DB0,0x899A)}, /* MSI 3070*/
    {USB_DEVICE(0x0DB0,0x3870)}, /* MSI 3070*/
    {USB_DEVICE(0x0DB0,0x870A)}, /* MSI 3070*/
    {USB_DEVICE(0x0DB0,0x6899)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x3822)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x3871)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x871A)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x822A)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x3821)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x821A)}, /* Ralink 3070 */
    {USB_DEVICE(0x5A57,0x0282)}, /* zintech 3072 */    
    {USB_DEVICE(0x083A,0xA703)}, /* IO-MAGIC */
    {USB_DEVICE(0x13D3,0x3307)}, /* Azurewave */
    {USB_DEVICE(0x13D3,0x3321)}, /* Azurewave */
    {USB_DEVICE(0x07FA,0x7712)}, /* Edimax */
    {USB_DEVICE(0x0789,0x0166)}, /* Edimax */
    {USB_DEVICE(0x148F,0x2070)}, /* Edimax */
#endif // RT3070 //
    { }/* Terminating entry */
};

INT const rtusb_usb_id_len = sizeof(rtusb_dev_id) / sizeof(USB_DEVICE_ID);

MODULE_DEVICE_TABLE(usb, rtusb_dev_id);

---

### Post by woodrow667 on 2011-01-21
Hopefully there are no smilies in this one. :-)

/*
 *************************************************************************
 * Ralink Tech Inc.
 * 5F., No.36, Taiyuan St., Jhubei City,
 * Hsinchu County 302,
 * Taiwan, R.O.C.
 *
 * (c) Copyright 2002-2007, Ralink Technology, Inc.
 *
 * This program is free software; you can redistribute it and/or modify  * 
 * it under the terms of the GNU General Public License as published by  * 
 * the Free Software Foundation; either version 2 of the License, or     * 
 * (at your option) any later version.                                   * 
 *                                                                       * 
 * This program is distributed in the hope that it will be useful,       * 
 * but WITHOUT ANY WARRANTY; without even the implied warranty of        * 
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         * 
 * GNU General Public License for more details.                          * 
 *                                                                       * 
 * You should have received a copy of the GNU General Public License     * 
 * along with this program; if not, write to the                         * 
 * Free Software Foundation, Inc.,                                       * 
 * 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             * 
 *                                                                       * 
 *************************************************************************

    Module Name:
    rtusb_dev_id.c
 
    Abstract:
 
    Revision History:
    Who        When          What
    ---------  ----------    ----------------------------------------------
 */

#include "rt_config.h"

/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT3070
    {USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
    {USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
    {USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
    {USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x871C)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x822C)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x871B)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x822B)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
    {USB_DEVICE(0x0DF6,0x0048)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0047)}, /* Sitecom 3071 */
    {USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
    {USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
    {USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
    {USB_DEVICE(0x083A,0xA701)}, /* SMC 3070 */
    {USB_DEVICE(0x083A,0xA702)}, /* SMC 3072 */
    {USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
    {USB_DEVICE(0x1740,0x9707)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9708)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9709)}, /* EnGenius 3072 */
    {USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
    {USB_DEVICE(0x13D3,0x3305)}, /* AzureWave 3070*/
    {USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
    {USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
    {USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
    {USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
    {USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
    {USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
    {USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
    {USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
    {USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
    {USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C16)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C17)}, /* D-Link 8070 */
    {USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
    {USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
    {USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x04BB,0x0947)}, /* I-O DATA 3070 */
    {USB_DEVICE(0x04BB,0x0948)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
    {USB_DEVICE(0x20B8,0x8888)}, /* PARA INDUSTRIAL 3070 */
    {USB_DEVICE(0x0B05,0x1784)}, /* Asus 3072 */
    {USB_DEVICE(0x203D,0x14A9)}, /* Encore 3070*/
    {USB_DEVICE(0x0DB0,0x899A)}, /* MSI 3070*/
    {USB_DEVICE(0x0DB0,0x3870)}, /* MSI 3070*/
    {USB_DEVICE(0x0DB0,0x870A)}, /* MSI 3070*/
    {USB_DEVICE(0x0DB0,0x6899)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x3822)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x3871)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x871A)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x822A)}, /* MSI 3070 */
    {USB_DEVICE(0x0DB0,0x3821)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DB0,0x821A)}, /* Ralink 3070 */
    {USB_DEVICE(0x5A57,0x0282)}, /* zintech 3072 */    
    {USB_DEVICE(0x083A,0xA703)}, /* IO-MAGIC */
    {USB_DEVICE(0x13D3,0x3307)}, /* Azurewave */
    {USB_DEVICE(0x13D3,0x3321)}, /* Azurewave */
    {USB_DEVICE(0x07FA,0x7712)}, /* Edimax */
    {USB_DEVICE(0x0789,0x0166)}, /* Edimax */
    {USB_DEVICE(0x148F,0x2070)}, /* Edimax */
#endif // RT3070 //
    { }/* Terminating entry */
};

INT const rtusb_usb_id_len = sizeof(rtusb_dev_id) / sizeof(USB_DEVICE_ID);

MODULE_DEVICE_TABLE(usb, rtusb_dev_id);

---

### Post by chili555 on 2011-01-21
(Chili picks up his sledge hammer and acetylene torch...) Why let's just add it and see what happens. Please amend as follows.> {USB_DEVICE(0x07FA,0x7712)}, /* Edimax */
{USB_DEVICE(0x0789,0x0166)}, /* Edimax */
{USB_DEVICE(0x148F,0x2070)}, /* Edimax */
#endif // RT3070 //
[COLOR="Red"]#ifdef RT3370
	{USB_DEVICE(0x148F,0x3370)}, /* Ralink 3370 */
#endif // RT3370 //[/COLOR]
{ }/* Terminating entry */
};

INT const rtusb_usb_id_len = sizeof(rtusb_dev_id) / sizeof(USB_DEVICE_ID);

MODULE_DEVICE_TABLE(usb, rtusb_dev_id); Everything else, except what we added remains unchanged.

---

### Post by woodrow667 on 2011-01-21
still not working, but i didn't see any errors. gonna reboot. be right back.

---

### Post by woodrow667 on 2011-01-21
okay, still not working. Just a thought. In the folder there is a file RT2070STA.dat that you had me copy as RT3[COLOR=Red]0[/COLOR]70STA.dat. Should I copy that as RT3[COLOR=Red]3[/COLOR]70.dat?
Just a thought.

---

### Post by chili555 on 2011-01-21
dmesg will be our friend. Please run and post:```
dmesg | grep -i rt2
dmesg | grep -i rt3
```Thanks.

We may have better luck with a newer version of the driver.

---

### Post by woodrow667 on 2011-01-21
administrator@ubuntu:~$ dmesg | grep -i rt2
administrator@ubuntu:~$ dmesg | grep -i rt3
administrator@ubuntu:~$

---

### Post by chili555 on 2011-01-21
I think I know the probable outcome, but try:```
sudo modprobe rt3070sta
dmesg | grep -i rt2
dmesg | grep -i rt3
```In anticipation of things to come, download the attached to your desktop, please.

---

### Post by woodrow667 on 2011-01-21
administrator@ubuntu:~$ sudo modprobe rt3070sta
administrator@ubuntu:~$ dmesg | grep -i rt2
[ 3678.962199] usbcore: registered new interface driver rt2870
administrator@ubuntu:~$ dmesg | grep -i rt3
administrator@ubuntu:~$ 

Got the downloaded file on desktop ready to go.

---

### Post by chili555 on 2011-01-21
While I write, please do:```
cd Desktop/2010   <--Press Tab
sudo su
make uninstall
exit
```That will uninstall the version that, obviously doesn't work.

---

### Post by woodrow667 on 2011-01-21
I stand ready my lord.

---

### Post by chili555 on 2011-01-21
Discard the older version you have on your desktop; both the .tar.gz and the folder. Be careful not to discard the one you just downloaded. Please do:```
cd Desktop
tar xvf 2010*
```A folder will appear. Go to os/linux/ and open the file config.mk with the text editor. Change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently '=n.' Proofread, save and close the text editor. Now do:```
cd Desktop/2010  <--Press Tab
sudo su
make
make install
modprobe rt3370sta
exit
```I believe, this time, the module is now rt3[COLOR="Red"]3[/COLOR]70sta. Note any errors and post back your result.

PS - What kinda geek is sitting around on Friday night compiling a tarball? I need a life.

---

### Post by woodrow667 on 2011-01-21
Got to be close. Just one error. Isn't........this your life? I'm so glad you are here. :-)

 modprobe rt3370sta
FATAL: Error inserting rt3370sta (/lib/modules/2.6.32-27-generic/kernel/drivers/net/wireless/rt3370sta.ko): Device or resource busy

---

### Post by chili555 on 2011-01-21
> Device or resource busyThis generally means some other driver is claiming the device (!!) We had a problem getting *anything* to claim it! Let's just reboot.

---

### Post by woodrow667 on 2011-01-21
Whoo Hoo!!!!!!!!! Conection established!!!!! You da man Chili. I can't thank you enough!

---

### Post by woodrow667 on 2011-01-21
One more question. My other hard drive has xubuntu and I tried to load the other driver to it. Can I follow these instructions to load the driver to it?

---

### Post by chili555 on 2011-01-21
Woo hoo indeed! Thanks for being patient and persistent. You can follow the same instructions. Post back if it doesn't go well.

When a new kernel image is installed by Update Manager, you'll need to build the module for the newer kernel with:```
sudo su
make clean
make 
make install
modprobe rt3370sta
exit
```Eventually, a native driver will claim the device and no rebuild will be required.

---

### Post by woodrow667 on 2011-01-21
Thank You so much!

---

### Post by woodrow667 on 2011-01-21
Well, everything install in xubuntu and it tries to connect, but it keeps asking for the network password. At least the driver is working. Do I have to go into that common file and add the line you posted? I'll try again tomorrow.

Never mind. That line is already there.

---

### Post by woodrow667 on 2011-01-22
Update: After restarting ubuntu, the usb wireless adapter will not connect to the network. It tries and then asks for the password over and over. Don't know what else to do now.

---

### Post by megavolt500 on 2011-01-22
chili555 could you please help me too.

I am also a total newbie, running Ubuntu 10.10 (upgraded). I have been trying to get my TP-Link wn321g ver4 working for more than a week, but with no success. I followed all sorts of directions that I found in the forums, and all sorts of drivers. Then I found this:

[http://ubuntuforums.org/showthread.php?t=1285828&page=13](http://ubuntuforums.org/showthread.php?t=1285828&page=13)

and I followed the directions on top by pesarak, but it's just not working for me.

All was going well until I tried "make install". I then got this:

make -C /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [install] Error 2

I did the manual file copying, but when I got to:
sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/

I got:
cp: cannot stat `./rtk3070sta.ko': No such file or directory

When I tried to start the module I got:
FATAL: Module rt3070sta not found

I'd really appreciate any help you could give me.

---

### Post by chili555 on 2011-01-22
Do you mean these lines?> Go to os/linux/ and open the file config.mk with the text editor. Change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently '=n.' Proofread, save and close the text editor.Yes, sir; before you run 'make.' If you did not, please do:```
sudo su
rmmod -f rt3370sta
make clean
make
sudo make install
modprobe rt3370sta
exit
```Whick kernel are you running?```
uname -r
```

---

### Post by megavolt500 on 2011-01-22
The kernel that I am running is 2.6.35-24-generic

I forgot to say that the device is shown (lsusb) as:
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

I tried what you said but when I typed in:
rmmod -f rt3370sta
I got: ERROR: Removing 'rt3370sta': No such file or directory

---

### Post by chili555 on 2011-01-23
> **megavolt500 said:**
> The kernel that I am running is 2.6.35-24-generic

I forgot to say that the device is shown (lsusb) as:
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

I tried what you said but when I typed in:
rmmod -f rt3370sta
I got: ERROR: Removing 'rt3370sta': No such file or directoryRather than hijack Woodrow's thread, would you please start a new thread and send me a private message if I don't catch it quickly?

---

### Post by woodrow667 on 2011-01-23
update: This is crazy. I'm on the xubuntu hard drive now and was hooked up to the wired network and surfing. All of a sudden, my wireless connected on its own and has been working for a few hours now. I'm scared to shut it down now, but I will have to so I can move it out to my man cave. Wish me luck! Thanks again.

---

### Post by imamsibli on 2011-04-01
hi chili555. i am from indonesia
i use UBUNTU 10.10 with Toshiba L510.
I have problem with TP link wn321g but i read your tutor. tplinks wn321g is working now in my TS. 

thanks chili. :popcorn:

---

### Post by chili555 on 2011-04-01
> i read your tutor. tplinks wn321g is working now in my TS.
Good work! I'm glad it's working. Have fun!

---

### Post by otro_claudio on 2011-05-14
Hi:

I'm trying to connect one of those rt2070 usb antennas.
I read this thread and another one ([http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)) and i don't know how far I go until now.
And i'm just a begginer using ubuntu.
The distro i'm using is 10.04 lucid.
And i have instaled the 'headers' for use make


I used this drivers (RT8070/RT3070/RT3370/RT5370/RT5372 USB,05/11/2011,2.5.0.2).
and I added the line {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */     , in rtusb_dev_id.c 
I think i miss the change the no for yes in WPA_SUPPLICANT (i understand it afther i use make and make install)

I get this on the console:
claudio@otromascongnu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

claudio@otromascongnu:~$ sudo modprobe rt3070sta

claudio@otromascongnu:~$ sudo dmesg | grep -i rt2
[  101.409354] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  101.426723] usbcore: registered new interface driver rt2870

claudio@otromascongnu:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1e:68:6a:cd:1a  iwcongig
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:27 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:308 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:308 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:23088 (23.0 KB)  TX bytes:23088 (23.0 KB)

wlan0     IEEE 802.11bg  ESSID:"RgNet_3"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



I'm not sure if i installed the antenna or not.
The wlan0 is the antenna?
I writed the essid name in the configuration file in /etc/Wireless/RT2870STA

The internet conection that i have is a static one, if the things are working i only need to configure it?
Where i put the stati ip, gateway, etc., in wlan0 with iwconfig?

Best regards, and thanks 

Claudio

---

### Post by chili555 on 2011-05-14
> I'm not sure if i installed the antenna or not.I think the module rt2870sta that's already built in to the kernel is driving your device. Let's check. Please run and post:```
modinfo rt3070sta | grep 2070
modinfo rt2870sta | grep 2070
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by otro_claudio on 2011-05-14
I ran the commands but nothing happened

claudio@otromascongnu:~$ modinfo rt3070sta | grep 2070
ERROR: modinfo: could not find module rt3070sta
claudio@otromascongnu:~$ modinfo rt2870sta | grep 2070
claudio@otromascongnu:~$ lsmod | grep -e rt2 -e rt3


Then i mount the module? and:

claudio@otromascongnu:~$ sudo modprobe rt3070sta
claudio@otromascongnu:~$ modinfo rt3070sta | grep 2070
ERROR: modinfo: could not find module rt3070sta
claudio@otromascongnu:~$ modinfo rt2870sta | grep 2070
claudio@otromascongnu:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             525366  0 


And i forgot mention earlier that i blacklisted the following in /etc/modprobe.d/blacklist.conf 
#estos los agregué yo por la antena
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

---

### Post by chili555 on 2011-05-14
Please run and post:```
sudo modprobe rt5370sta
modinfo rt5370sta | grep 2070
iwconfig
```Thanks.

---

### Post by otro_claudio on 2011-05-14
claudio@otromascongnu:~$ sudo modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
claudio@otromascongnu:~$ modinfo rt5370sta | grep 2070
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
claudio@otromascongnu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"RgNet_3"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
claudio@otromascongnu:~$ &#65279;sudo modprobe rt3070sta
claudio@otromascongnu:~$ sudo modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
claudio@otromascongnu:~$ modinfo rt5370sta | grep 2070
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
claudio@otromascongnu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"RgNet_3"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Thanks to you

---

### Post by chili555 on 2011-05-14
> $ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:"RgNet_3"
Mode:Managed Frequency:2.427 GHz Access Point: Not-Associated
Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Well, you seem to have a wireless interface! I wonder how. Let's see:```
lsmod
```

---

### Post by otro_claudio on 2011-05-14
This is it:

            Module                              Size               Used by
  snd_hda_codec_realtek      279072         1 
  binfmt_misc                        7960             1 
  ppdev                                 6375             0 
  arc4                                   1473              2 
  snd_hda_intel                     25805            2 
  snd_hda_codec                 85759            2 snd_hda_codec_realtek,snd_hda_intel
  snd_hwdep                         6924             1 snd_hda_codec
  snd_pcm_oss                     41394            0 
  snd_mixer_oss                   16299            1 snd_pcm_oss
  snd_pcm                            87946            3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
  snd_seq_dummy                 1782             0 
  snd_seq_oss                      31191            0 
  snd_seq_midi                     5829              0 
  snd_rawmidi                      23420            1 snd_seq_midi
  snd_seq_midi_event           7267              2 snd_seq_oss,snd_seq_midi
  snd_seq                             57481            6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
  joydev                                11104           0 
  snd_timer                           23649            2 snd_pcm,snd_seq
  ath5k                                  134437         0 
  snd_seq_device                 6888              5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  fbcon                                 39270            71 
  tileblit                                 2487              1 fbcon
  font                                    8053              1 fbcon
  bitblit                                  5811             1 fbcon
  softcursor                          1565              1 bitblit
  nvidia                                 10832442      41 
  acer_wmi                            15829           0 
  uvcvideo                             62819           0 
  videodev                             40518           1 uvcvideo
  v4l1_compat                      15495            2 uvcvideo,videodev
  v4l2_compat_ioctl32         11892            1 videodev
  mac80211                         238896          1 ath5k
  video                                 20623            0 
  output                                2503              1 video
  ricoh_mmc                          3416             0 
  sdhci_pci                            6700             0 
  sdhci                                  17928            1 sdhci_pci
  snd                                    71251            16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  k8temp                              4040              0 
  ath                                      9723             1 ath5k
  vga16fb                             12757            1 
  edac_core                         45423            0 
  vgastate                             9857              1 vga16fb
  edac_mce_amd                 9278              0 
  psmouse                            64576            0 
  serio_raw                           4918             0 
  cfg80211                           148725          3 ath5k,mac80211,ath
  led_class                             3764             3 ath5k,acer_wmi,sdhci
  i2c_nforce2                        6099             0 
  soundcore                           8052             1 snd
  snd_page_alloc                  8500              2 snd_hda_intel,snd_pcm
  lp                                       9336              0 
  parport                              37160            2 ppdev,lp
  usbhid                                 41116           0 
  ohci1394                            30260           0 
  hid                                     83600            1 usbhid
  ieee1394                            94771           1 ohci1394
  pata_amd                           11962           0 
  forcedeth                           55624            0 
  ahci                                    37870           4
  


And i already have instaled and working an atheros wirelss card. But i need one external antenna to connect where i am. So i can't use the atheros wifi card (it cames with the acer notebook that i use) and i have to buy the usb antenna.

Do you think that wlan0 is the wireless interface for the usb ralink antenna?

---

### Post by otro_claudio on 2011-05-14
when i use &#65279;sudo modprobe rt3070sta first, the lsmod first line changes:

Module                  Size  Used by
rt2870sta             525366  0 
snd_hda_codec_realtek   279072  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
arc4                    1473  2 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 11104  0 
snd_timer              23649  2 snd_pcm,snd_seq
ath5k                 134437  0 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
nvidia              10832442  41 
acer_wmi               15829  0 
uvcvideo               62819  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
mac80211              238896  1 ath5k
video                  20623  0 
output                  2503  1 video
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
snd                    71251  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  4040  0 
ath                     9723  1 ath5k
vga16fb                12757  1 
edac_core              45423  0 
vgastate                9857  1 vga16fb
edac_mce_amd            9278  0 
psmouse                64576  0 
serio_raw               4918  0 
cfg80211              148725  3 ath5k,mac80211,ath
led_class               3764  3 ath5k,acer_wmi,sdhci
i2c_nforce2             6099  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
ohci1394               30260  0 
hid                    83600  1 usbhid
ieee1394               94771  1 ohci1394
pata_amd               11962  0 
forcedeth              55624  0 
ahci                   37870  4

---

### Post by chili555 on 2011-05-14
> Do you think that wlan0 is the wireless interface for the usb ralink antenna?No, I'm quite sure it's the Atheros.

Let's try to repair the 2070 install. Go back to config.mk and make the changes here:> ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.Now open a terminal and navigate to the directory that was created when you extracted the bz2; for example:```
cd Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO
sudo su
make clean
make install
modprobe rt5370sta
exit
```Note any errors and post them here. Warnings are OK.> when i use &#65279;sudo modprobe rt3070sta first, the lsmod first line changes:rt3070sta is not your driver. Please don't modprobe random, spurious stuff; it just confuses the issue.

---

### Post by otro_claudio on 2011-05-14
I have one doubt.
The antenna that i'm talking is an external antenna that cames with a 2 meter iron bar to place outside, with a usb cable to connect to the pc. And i undestand that there are ralink usb wireless cards (the usual pendrive alike ones).
The driver that we're talkink is the right one, i ask you because i don't want that you loose your time, or bother you.

---

### Post by chili555 on 2011-05-14
> The driver that we're talkink is the right one,You mean rt3070sta? I don't think so; you proved it:> $ modinfo rt3070sta | grep 2070
ERROR: modinfo: could not find module rt3070staIt didn't recognize your device.

The package you downloaded and are trying to compile creates a driver rt5370sta:> install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c [COLOR="Red"]rt5370sta[/COLOR].ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-8-generic
Yes? No??

---

### Post by otro_claudio on 2011-05-14
I thougt that 3070 were compatible, so that's the reason i was trying that driver.
I'm not so sure now.
It seems, for the way that windows recognized the device, that is 2870.

The answer to your question, i guess, is No.

Sorry for bother you. 

I'm going to make sure first what i have (is difficult, because the wifi card is sealed inside the antenna) and i only have the windows information (802.11 USB Wireless LAN card, and USB\VID_148F&PID_2070) from the device manager and a product specification that only says 2070.


Thanks for your time and sorry again to bother you.

Best regards, 

Claudio

---

### Post by chili555 on 2011-05-14
We know _exactly_ what you have from lsusb:> get this on the console:
claudio@otromascongnu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID [COLOR="Red"]148f:2070 Ralink Technology, Corp.[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
You modified the rt5370sta driver for your usb.id. Why not compile it correctly and see if it works?

---

### Post by otro_claudio on 2011-05-14
It seems that the driver is the right one. And is the same driver for a lot of different products.

The antenna i'm trying to configure is this one: [http://www.aquario.com.br/?action=produto&id=5](http://www.aquario.com.br/?action=produto&id=5)
And the drivers availables to download from the page needed a patch to compile with tha actual linux kernel (errors with make and fail on make install). There's a patch to solve that.

I'm going to try with the same drivers from before, as you say.

Thanks for your help.

---

### Post by chili555 on 2011-05-14
> I'm going to try with the same drivers from before, as you say.Post back if you get stuck or if I can help.

---

### Post by otro_claudio on 2011-05-14
This is what happened with the make install:
root@otromascongnu:/home/claudio/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO# make install
make -C /home/claudio/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux -f Makefile.6 install
mkdir: no se puede crear el directorio «/etc/Wireless»: El fichero ya existe
make[1]: se ingresa al directorio «/home/claudio/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux»
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/claudio/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-31-generic
make[1]: se sale del directorio «/home/claudio/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux»

root@otromascongnu:/home/claudio/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO# modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and iwconfig shows:
claudio@otromascongnu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"RgNet_3"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
claudio@otromascongnu:~$ modinfo rt5370sta | grep 2070
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*


And in etc/Wireless i have 2 folders now RT2070STA (empty) and RT2870STA (with the file RT2870STA.dat inside)

---

### Post by chili555 on 2011-05-14
> FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)We may have a problem because this package was built very recently, evidently April 7, 2011. On the other hand, you are running an older (in Linux terms) kernel version and gcc version. Let's check however:```
dmesg | tail -n15
```Please post the result; maybe it's something we can fix.

---

### Post by chili555 on 2011-05-14
Hey, Claudio! It's Saturday night; I have a beautiful woman sitting next to me and it's time to short-cut the whole thing. Let's abandon the not-working file you downloaded:```
cd 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.2_DPO
sudo su
make uninstall
exit
```Now check here:  [http://ubuntuforums.org/showthread.php?t=1701167&highlight=2070](http://ubuntuforums.org/showthread.php?t=1701167&highlight=2070)

Especially see posts #8 and 9!

See you tomorrow!

---

### Post by otro_claudio on 2011-05-14
[   20.759555] type=1505 audit(1305422408.609:6):  operation="profile_replace" pid=882 name="/sbin/dhclient3"
[   20.759901] type=1505 audit(1305422408.609:7):  operation="profile_replace" pid=882 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.762273]   alloc irq_desc for 27 on node 0
[   20.762278]   alloc kstat_irqs on node 0
[   20.762289] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   20.762495] eth0: no link during initialization.
[   20.763260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.763661] type=1505 audit(1305422408.619:8):  operation="profile_replace" pid=882 name="/usr/lib/connman/scripts/dhclient-script"
[   20.771344] type=1505 audit(1305422408.629:9):  operation="profile_load" pid=885 name="/usr/lib/cups/backend/cups-pdf"
[   20.771760] type=1505 audit(1305422408.629:10):  operation="profile_load" pid=885 name="/usr/sbin/cupsd"
[   20.774897] type=1505 audit(1305422408.629:11):  operation="profile_load" pid=883 name="/usr/bin/evince"
[   20.866223] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.119198] ppdev: user-space parallel port driver
[   22.421991] hda_codec: ALC268: BIOS auto-probing.
[   22.680129] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input10
claudio@otromascongnu:~$ 

thanks

---

### Post by otro_claudio on 2011-05-14
Ok, thanks a lot man.

Best regards and have a nice weekend.

Claudio

---

### Post by chili555 on 2011-05-15
I'm ready to go when you are. Let's solve this case!

---

### Post by otro_claudio on 2011-05-16
Hi again:

With the info in the last post it works.
I made teh uninstall part that you told me in your last post and the followed the thread instructions, and it worked.
Ubuntu managed the antenna and i used the network manager to do the setting part of the fix connection.

Thanks a lot.

Can you explain to me what we do to make this thing works, please, in simple words, like if i'm a 5 years old child :)
Am I using no propietary drivers for the antenna and using some 'code' that cames with ubuntu?
 
Thanks a lot again Chili.

Claudio

---

### Post by chili555 on 2011-05-16
Your device is relatively new. It's a Ralink rt2870 chipset.

The way that drivers and hardware recognize each other is the usb.id or pci.id that's hard-coded into the hardware; in your case 148f:2070.> get this on the console:
claudio@otromascongnu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID [COLOR="Red"]148f:2070[/COLOR] Ralink Technology, Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Let's look at the module information for rt2870sta:```
modinfo rt2870sta
```> filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93C0C58E1A016FE5BD4DC9F
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
etc., etc.The alias lines are usb.ids that this driver recognizes and drives. In your case, since you are running an older kernel version, your usb.id is not listed. I am running the latest version and your usb.id is listed, as you see. Therefor, we know the driver rt2870sta will effectively drive your hardware.

What we did is temporarily add your usb.id to the alias list for your earlier version of rt2870sta. That tells the driver to drive the hardware. The proof that our method is sound is that your wireless device works as expected.

As we used to say when I was a kid, about 209 years ago, is that as clear as mud?> Am I using no propietary drivers for the antenna and using some 'code' that cames with ubuntu?That's correct.

---

### Post by otro_claudio on 2011-05-16
Thanks man.

I guess that you are sitting at the right of the God of the Code :)
I still can't leve completely the Bill Gates' table, but thanks to you now i'm able to move my seat a step closer to the exit :D  

Best regards, 

Claudio

---

### Post by kendoazzikra on 2011-05-17
[img]http://cdn-u.kaskus.us/45/xowwp52i.png[/img]

Whats the Problem?

Anybody can solved this?

Sent massage ...

---

### Post by KnightAR on 2011-06-26
Hi Guys,

I've been trying to find drivers for my WUSB54GC V3 RT2070L Usb stick, and I've been trying to find working drivers that compile but haven't found any that actually work. 

I've spent a few hours already downloading, and compiling drivers and I can't seem to find any that actually works.

> Bus 004 Device 006: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L]


Debian: Wheezy
Kernel version: 2.6.39-2-amd64

# modinfo rt2800usb | grep 2070
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*

# modinfo rt2800usb | grep 1737
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*


Thanks!

---

### Post by chili555 on 2011-06-26
> # modinfo rt2800usb | grep 2070
alias: usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*

# modinfo rt2800usb | grep 1737
alias: usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias: usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias: usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*

> Bus 004 Device 006: ID [COLOR="Red"]1737:0077[/COLOR] Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L] 

Please check:```
modinfo rt2870sta | grep 0077
modinfo rt2800usb | grep 0077
```I don't know anything about Wheezy, but in Ubuntu rt2870sta *and* rt2800usb both claim your device and conflict. All it takes to get things right is to blacklist rt2800usb and reboot. Post back if you'd like specifics.

---

### Post by jasekshaw on 2012-07-14
i dont no if you will ever see this chili... but, i officialy love you.., you have saved me so much time and money.. thank you, its not often someone spends so much time helping another

---

### Post by chili555 on 2012-07-14
Thank you so much for your kind comments. I enjoy helping you all and your words of appreciation make it all worthwhile. I'm glad it's working.

---

### Post by jasekshaw on 2012-07-15
Thanks :) well, after i got it working, it updated my version of ubuntu! N it wont work again Hopefully if i repeat what you said, it will work again ha, havnt got time till later tho.

---

### Post by Yumi on 2012-11-02
Thanks for the thread. Got my old RT2070 USB working following the instructions on page 1 straight away.

Michael

---

