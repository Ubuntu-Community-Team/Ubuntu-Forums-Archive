---
title: "HOWTO: Cricket Wireless A600 Broadband Modem"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2009-05-02
**Easy Method for Installing (pre-compiled debs):**

Attached are the debs and a flipflop.sh to get this working do the following -

*Step 1:*
Download the .deb file for your selected architecture ([32bit](http://ubuntuforums.org/attachment.php?attachmentid=130985&d=1254841714) or [64bit](http://ubuntuforums.org/attachment.php?attachmentid=130984&d=1254841714)) && install it

*Step 2:*
Download the [flipflop.sh](http://ubuntuforums.org/attachment.php?attachmentid=130987&d=1254841832) (for the A600) or the [cricketum185c.sh](http://ubuntuforums.org/attachment.php?attachmentid=137459&stc=1&d=12590893217) (for the UM185C), 

**A600** Now right click on the file and select "properties". Click over to the "permissions" tab, and check the box "allow executing file as a program". Now double click it and select "Run", enter your password. Wait a few moments and poof! Your 3g modem should now be appearing in your network manager.

**UM185C** Now we just need to execute the cricketum185c.sh, it is in the directory of files you extracted, by running the following: ```
sudo ./cricketum185c.sh
``` (Please note you need to first make this file executable by running ```
chmod +x cricketum185c.sh
```

*Notes:*

On Ubuntu 9.04 and earlier. You will need to run the .sh file every time you connect your modem. Starting with 9.10 the networkmanager auto detects when a modem that has already been attached gets connected and it takes care of "flipping" for you after the first time.

Before this guide will work for you, you do need to load the device on a Windows/Mac system and install the software for the device and activate it. (I have a Windows VM for just such occasions, it worked fine)

**Installing from Source (A600 Only):**
This is a quick how to, for getting the latest Cricket Wireless 3g Modem working under Ubuntu (with out first booting into Windows). I've spent the better part of 4 days trying to get this little bugger to work under Ubuntu natively, so I figured I would share my findings so other people do not have to go through the same head ache. 

This has been tested under Ubuntu 8.10 32bit & 64bit as well as Jaunty(9.04) 32bit and 64bit and Karmic 32bit, how ever I do not see any reason why it should not work under any distro/version of *buntu. 

*Step 1:* 

Download the [archive](http://ubuntuforums.org/attachment.php?attachmentid=112148&d=1241271539) attached to this post and extract the contents to your preferred directory.

*Step 2:*

Open up terminal and use cd to change into the directory of the extracted files.

32 bit Users - Install usb_modeswitch with the following command: ```
sudo make install
```

64 bit Users - We need to recompile modeswitch to work on the 64bit platform. Run the following commands in terminal to do so ```
sudo apt-get install build-essential libusb-dev
rm usb_modeswitch
make
sudo make install
```

*Step 3:*

Plug in your Cricket A600 to an open USB port, wait a moment for it to be detected as a CD drive/the auto play menu to pop up. Now we just need to execute the flipflop.sh, it is in the directory of files you extracted, by running the following: ```
sudo ./flipflop.sh
``` (Please note you need to first make this file executable by running ```
chmod +x flipflop.sh
```

After running the flipflop.sh you need to wait about 12 seconds (while it works it's magic) and then poof! Your Cricket device should now appear in your network manager as a connection option.

*Notes:*

You will need to ```
sudo ./flipflop.sh
``` each time you attach the device for it to work.

Before this guide will work for you, you do need to load the device on a Windows/Mac system and install the software for the device and activate it. (I have a Windows VM for just such occasions, it worked fine)

I played around with udev some trying to automate this process when you play the device in, but I could not get it to work properly, if someone smarter/experienced than myself would like to figure that out I'd be more than happy to add it to this guide.

Trouble Shooting - 
If this guide does not work for you try first opening up the flipflop.sh and increasing the sleep time from 10 seconds to 20 - some systems require a longer delay.



**UPDATE/FYI:**
I no longer have my cricket A600 and I have not tried it under 10.04 (which people seem to be having issues with) feel free to post in the thread and hopefully someone else will be of help - but for best results I suggest using Ubuntu 9.10 or older with the modem.

~Jeff Hoogland

---

### Post by rotoghost on 2009-05-03
That worked perfectly, thanks very much!

---

### Post by goshock on 2009-05-07
Hopefully someone can help me finish this upu today.  I followed this guide and it all worked, but in the messages file, when I try to connect, this is the output:

```

May  7 15:21:58 acer pppd[12028]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
May  7 15:21:58 acer pppd[12028]: pppd 2.4.5 started by root, uid 0
May  7 15:21:58 acer pppd[12028]: Removed stale lock on ttyACM0 (pid 11735)
May  7 15:21:58 acer pppd[12028]: Using interface ppp0
May  7 15:21:58 acer pppd[12028]: Connect: ppp0 <--> /dev/ttyACM0
May  7 15:22:02 acer pppd[12028]: No CHAP secret found for authenticating us to 
May  7 15:22:03 acer pppd[12028]: CHAP authentication succeeded
May  7 15:22:03 acer pppd[12028]: CHAP authentication succeeded
May  7 15:22:03 acer pppd[12028]: local  IP address 10.99.142.161
May  7 15:22:03 acer pppd[12028]: remote IP address 172.28.5.5
May  7 15:22:03 acer pppd[12028]: primary   DNS address 172.28.221.53
May  7 15:22:03 acer pppd[12028]: secondary DNS address 172.28.221.54
May  7 15:22:14 acer pppd[12028]: Terminating on signal 15
May  7 15:22:14 acer pppd[12028]: Connect time 0.2 minutes.
May  7 15:22:14 acer pppd[12028]: Sent 0 bytes, received 0 bytes.

```

I am running ubuntu 9.04 on an Acer Aspire One Netbook.
Does anyone have any ideas?  Thanks beastrace91 for your help over PM.

---

### Post by beastrace91 on 2009-05-08
As your issue does not pertain to making Ubuntu see the device (which is the point of this guide) maybe posting a new topic describing your issue would be a better idea and would keep this one on topic.

~Jeff

---

### Post by bjacer on 2009-05-12
Jeff,
Thank you very much for this great HOWTO. 
I used it at installing SAMSUNG SGH-Z810 modem under ubuntu-9.04.

I failed with my acer notebook first time. But I found a 'solution' later. I modified your flipflop.sh. I repeated the first two lines of your flipflop.sh at the end of the script. Then I inserted another 'sleep 10' after the third line. I am still not sure if all these changes are necessary, but it WORKS for me this way! 

Thanks again
Jozsef

---

### Post by beastrace91 on 2009-05-12
Good to know :)

I wish these major companies would take the short bit of extra time themselves and make their devices detect properly on Linux in the first place as it does not need the drivers that are on the auto play USB :/

Ahh well in the mean time modeflip works just fine.

As a side note for ease of use I add an icon to my internet tab in my menu and add an exception using sudo visudo so I do not need to enter my root password to flip my device.

~Jeff

---

### Post by e_rene@yahoo.com on 2009-05-19
Dang!, it does not work for me. I am using Ubuntu 9.04 and this does not work anymore. The USB device gets online when I execute the ./flipflop.sh script but, it never appears in the Network Manager... Even  if I reboot my laptop it does not work, because my laptop reboots the USB modem as well :( and it gets offline once again. I am using the cricket A600 USB Modem device.

In additon, I have another laptop which does not reboot the USB device when rebooting the system (the USB modem does not get offline) and when I go back to Ubuntu, the Broadband USB device does appears in the Network Manager. 


I tried to restart the Network interfaces but it does not solve the issue.

Please let me know if you guys know how to solve this...

thanks!

---

### Post by beastrace91 on 2009-05-19
Can you please post what the flipflop.sh is out putting in terminal when you run it? I know on my one laptop I had to increase the sleep time in the script by about 5 seconds so it would have enough time for the device to fully "flip" before it runs the hard reset.

Like I said post the output and hopefully we can help you figure this out :)

~Jeff

---

### Post by e_rene@yahoo.com on 2009-05-20
Hi again!,

First off, thanks for your help Jeff...

There you have my output:


flipflop.sh
===================

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 Found a default device NOT in target class mode
Prepare switching, accessing device 002 on bus 003 ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x08 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 003 on bus 003 ...
Resetting usb device .
 OK, device was reset
-> Run lsusb to note any changes. Bye





lsusb
=============================


Bus 001 Device 003: ID 5986:0100 Acer, Inc OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1f28:0020  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




As I told you before, this was working on Ubuntu 8.10 but stopped working after the 9.04 upgrade.

Regards.

---

### Post by beastrace91 on 2009-05-20
Strange, are you running on 64bit or 32bit? I tested this on Ubuntu 9.04 NBR and it worked just fine. From the output of your flipflop.sh is it flipping/resetting properly so perhaps it is an issue with your network manager. Try removing the entry for the cricket device from your network manager (right click, edit connections, broadband tab, delete) and then hooking the device up and running flipflop.sh again.

Did u upgrade from 8.10 to 9.04 or did u do a fresh install?

~Jeff

---

### Post by e_rene@yahoo.com on 2009-05-20
Actually, the Cricket device never appears in the Broadband tab... I have removed and reinstalled the Network Manager and the problem persists... I even installed Wicd insted of Network Manager and the same issue happens.

I upgraded from 8.10 to 9.04, it is the 32 bits version.


I think it is gonna be a Kernel recession, but I don't know.

---

### Post by beastrace91 on 2009-05-20
Perhaps you could back up your data and do a fresh install of 9.04? I know there are some issues with upgrades some times. Also I know Ubuntu NBR is 32bit, so if it works on there I do not see much reason why it should not work on normal 32bit.

~Jeff

---

### Post by e_rene@yahoo.com on 2009-05-20
hmm, interesting... I just tried to setup the A600 USB modem from the Ubuntu 9.04 Live CD and it worked!... I wonder what's wrong when using an upgraded 8.10-9.04 version....

I need to find another way to solve this, I don't wanna erase everything and pimp my beauty ubuntu distro again... It takes some time to do so..:P

---

### Post by beastrace91 on 2009-05-21
I figured as much. As a rule of thumb when ever I want to upgrade an operating system (regardless of whether it's windows or nix) I always wipe it clean. Of course I do love the smell of a fresh operating system in the morning ;)

~Jeff

---

### Post by paintbalforjesus on 2009-07-03
Thank you very much.  I have used this on ubuntu 9.04 32- and 64-bit and 8.10 32-bit and it works perfectly on all of them.

Does anyone know if using cricket on Ubuntu still allows Cricket to track how much data you use?  They limit it to 5 gb/month, but I don't know if they keep track of it somehow using the windows program or by another method.  Anyone know?

---

### Post by beastrace91 on 2009-07-03
I'm about 99% sure they keep track of how much bandwidth you are using in a month on their end. As for monitoring it you can add an applet to your Gnome menu bar that will keep track of network traffic.

~Jeff

---

### Post by jlj59f9c on 2009-07-07
I'm so happy to be able to use my modem with my Eee PC. Thanks, Jeff. I did have a couple of questions though. The first is what applet would one use for monitoring network usage and is there one that writes a log file to keep track of total usage? My second question is how would one send/recieve text messages while running under Linux? Do I always have to connect under Windows in order to do this, or do you know of another way? Thanks in advance. :-)

---

### Post by beastrace91 on 2009-07-07
Glad it worked for you. As for the applet right click on your gnome panel and select "add to panel" and then select "network monitor". As for writing the data to a log I am not sure how exactly but perhaps [this thread](http://ubuntuforums.org/showthread.php?t=305672) will have some helpful hints for you. Unfortunately there is no way that I know of to text message with the device while on Ubuntu/Linux, but I can honestly say I have not really looked into it because I have unlimited texting on my cell phone so I use that.

~Jeff

---

### Post by jlj59f9c on 2009-07-07
Thanks for the reference to the other thread. I'm looking it over now. I doubt I would exceed the five GB limit since I can't use BitTorrent or Apache and what have ya, but there is always the chance that between system upgrades, YouTube and anything else the Web may hold, I may find a way to actually go over. Well, it's a matter of time and patience before things work smoothly. If you find out anything let us know and I'll do the same. :-D

---

### Post by mhurst102282 on 2009-07-19
I am running Ubuntu 9.04 and I have followed the instructions, but when I get to the part where you plug the modem in the auto run never pops up. So I tried running the flipflop.sh and it did turn the modem on, but I never got annything in the network manager nor does it connect to the internet. Any ideas?

---

### Post by beastrace91 on 2009-07-19
After you plug the modem in wait a moment and then click into your "places" on your bar and see if there is a "A600" listed there - if there is then click into it to manually trigger the device. After doing so run ```
sudo ./flipflop.sh
``` from the directory the file is in.

If it is not listed in places please open a terminal and run ```
lsusb
``` while the device is connected.

~Jeff

---

### Post by mhurst102282 on 2009-07-20
Here is the lsusb when the device is plugged in.

```
 	 	 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 004: ID 046d:092f Logitech, Inc. QuickCam Express Plus  
 Bus 003 Device 003: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse  
 Bus 003 Device 002: ID 03eb:0902 Atmel Corp.  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 1f28:0021   
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by beastrace91 on 2009-07-20
Alrighty well it is detecting that the device is connected. (it is the Bus 001 Device 002: ID 1f28:0021) Does it appear in your places menu/nautilus as "A600"?

While the device is connected please trying running this command in terminal and post the output: ```
sudo /usr/sbin/usb_modeswitch
```

~Jeff

---

### Post by mhurst102282 on 2009-07-20
It does not appear in my places menu, but I am not sure about nautilus so I will check when I get home aswell as running that command.

---

### Post by mhurst102282 on 2009-07-20
I ran the code and had the same issue it goes on, but no connection here is the lsusb after the switch:

```
 	 	 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 004: ID 046d:092f Logitech, Inc. QuickCam Express Plus  
 Bus 003 Device 003: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse  
 Bus 003 Device 002: ID 03eb:0902 Atmel Corp.  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 1f28:0020   
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 


```

---

### Post by mhurst102282 on 2009-07-20
Here is the out put after typing in the command:

```

	 	  * usb_modeswitch: tool for controlling "flip flop" mode USB devices  
  * Version 0.9.7 (C) Josua Dietze 2009  
  * Works with libusb 0.1.12 and probably other versions  
 

 Looking for target devices ...  
  Found devices in target mode or class (1)  
 Looking for default devices ...  
  Found default devices (1)  
  Found a default device NOT in target class mode  
 Prepare switching, accessing device 002 on bus 001 ...  
 Looking for active driver ...  
  OK, driver found ("usb-storage") 
  OK, driver "usb-storage" detached  
 Setting up communication with interface 0 ...  
 Trying to send the message to endpoint 0x08 ...  
  OK, message successfully sent  
 -> Run lsusb to note any changes. Bye 


```

---

### Post by beastrace91 on 2009-07-20
Alright well your device is connected and switching properly. After running the ```
sudo /usr/sbin/usb_modeswitch
``` run the following command ```
sudo usb_modeswitch -v 0x1f28 -p 0x0020 -R 1
``` and then wait a moment after it finishes then check your net work manager to see if the device has been added. 

I am betting the issue is that the default wait time I have set in the flipflop.sh is too short for your system (some of them take a longer time I noticed) to make the flipflop script work simple open it with gedit and increase ```
sleep 10
``` to 15 or 20.

Hope this helps,
~Jeff

---

### Post by mhurst102282 on 2009-07-20
I have tried both of those things and neither work. The modem goes on, but it never goes into the network manager.

---

### Post by beastrace91 on 2009-07-20
Alrighty I know this may sound kinda redundant but just want to make sure I understand what you are doing.

Run the following two commands in order: ```
sudo /usr/sbin/usb_modeswitch

sudo usb_modeswitch -v 0x1f28 -p 0x0020 -R 1
```

Please post the out put after each command.

~Jeff

---

### Post by mhurst102282 on 2009-07-20
OK here it is :

```

	 	  * usb_modeswitch: tool for controlling "flip flop" mode USB devices  
  * Version 0.9.7 (C) Josua Dietze 2009  
  * Works with libusb 0.1.12 and probably other versions  
 

 Looking for target devices ...  
  Found devices in target mode or class (1)  
 Looking for default devices ...  
  Found default devices (1)  
  Found a default device NOT in target class mode  
 Prepare switching, accessing device 002 on bus 001 ...  
 Looking for active driver ...  
  OK, driver found ("usb-storage") 
  OK, driver "usb-storage" detached  
 Setting up communication with interface 0 ...  
 Trying to send the message to endpoint 0x08 ...  
  OK, message successfully sent  
 -> Run lsusb to note any changes. Bye  
 

 mike@mike-desktop:~$ sudo usb_modeswitch -v 0x1f28 -p 0x0020 -R 1  
 

  * usb_modeswitch: tool for controlling "flip flop" mode USB devices  
  * Version 0.9.7 (C) Josua Dietze 2009  
  * Works with libusb 0.1.12 and probably other versions  
 

 Looking for default devices ...  
  Found default devices (1)  
 Prepare switching, accessing device 003 on bus 001 ...  
 Resetting usb device .  
  OK, device was reset  
 -> Run lsusb to note any changes. Bye 


```

---

### Post by beastrace91 on 2009-07-20
I'm at a loss here. Everything is running/changing exactly how it should be. The reset is going through just find - shortly after the reset it should just appear in your network manager. You are using Jaunty correct? Can you perhaps try installing modeswitch and connecting the device while booted from a LiveCD session so see if perhaps something is corrupted in your network manager applet install?

~Jeff

---

### Post by mhurst102282 on 2009-07-20
I have tried it in Hardy and in Jaunty. The Jaunty is an Alpha release because it is the only disk I have and I didnt want to use the bandwidth to download the jaunty .iso when I was hoping that I could just upgrade from there.

---

### Post by beastrace91 on 2009-07-21
You upgraded from Hardy to Jaunty? Hate to say it but this may be the issue - upgrading any OS always leads to issues and I recommend doing a fresh install. But like I said you can boot a liveCD and confirm that this is indeed your issue.

~Jeff

---

### Post by mhurst102282 on 2009-07-21
No I had a Hardy Disk and tried it and I also had a Jaunty disk and tried it an neither worked.

---

### Post by mhurst102282 on 2009-07-21
SInce the Jaunty disk I had is an alpha 6 disk I started to download a 9.04 final disk before I left for work today and I will try it again when I get home today.

---

### Post by beastrace91 on 2009-07-21
Alrighty, if it doesn't work off the LiveCD then perhaps there is some sort of issue with your hardware/Ubuntu. I'm actually booted off a Live Jaunty disc now (and using my Cricket Modem on it) to post this - so I know it works.

~Jeff

---

### Post by mhurst102282 on 2009-07-21
I believe it will work as long as I get a good burn. The jaunty disk I have now freezes up in the terminal a lot which is what I think the problem is. I will let you know because I really want to ditch my Windows install.

---

### Post by mhurst102282 on 2009-07-21
That was easy. I install Ubuntu 9.04 and since my card was already flipped from being in WIndows Ubuntu saw the card right away and now I can just use Ubuntu cool!

---

### Post by beastrace91 on 2009-07-21
If you are going to remove Windows you may want to double check and make sure the flipflop works for you in Ubuntu first - cause if you ever disconnect the modem and plug it back in you will need to reflip the device.

~Jeff

---

### Post by mhurst102282 on 2009-07-21
I just did and it does work :)

---

### Post by kcjames on 2009-07-22
This may be a bit off topic, but I've purchased a Netgear MBR624GU 3G wireless router.  Unfortunately, Cricket's A600 and the UM100C are unsupported.
 
However, the firmware is completely open source, available here:
[ftp://downloads.netgear.com/files/GPL/MBR624GUv6.00.22.14NA.tar.bz2.zip](ftp://downloads.netgear.com/files/GPL/MBR624GUv6.00.22.14NA.tar.bz2.zip)
 
So support can be added.
 
I wonder if anyone has tried modifying this to get the A600 to work with it.  Im afraid I don't know a bunch about modifying this stuff.

---

### Post by beastrace91 on 2009-07-23
Can't say that I've tried. Sorry.

~Jeff

---

### Post by maverick6740 on 2009-07-29
im confused i went to accessories and then terminal then in the command line i typed sudo make install and when i did i got "***No rule to make target install'. stop am i in the right place to start it. also i downloaded that app in 1st screen and there is no way to install

---

### Post by mhurst102282 on 2009-07-29
You must first change the directory in the terminal to the directory of the extracted files by tping ```
cd /then the directory its in 
```

---

### Post by beastrace91 on 2009-07-30
Yes you need to be sure to change into the place where you extracted the zip archive to. By default firefox will download to you desktop and if you also extracted the files there the folder you want will be there. Use ```
cd ~/Desktop
``` to get to your desktop and then use the ```
ls
``` command to see what files are on your desktop to find the folder the files extracted to.

~Jeff

---

### Post by deh_p3000 on 2009-08-11
I am completely new to ubuntu and I really want to use my cricket a600, When I tried the steps in your post I received error messages for each step I am using the 64 bit 9.04  build can you help? is there A remote login on ubuntu as well?  if so I would gladly let someone help me live.  here is what happens when I try the steps.

________________________________________________________________________________
garry@Ubuntu-Desktop:~$ cd cricket
garry@Ubuntu-Desktop:~/cricket$ sudo apt-get install build-essential
[sudo] password for garry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
garry@Ubuntu-Desktop:~/cricket$ sudo apt-get install libusb-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libusb-dev
garry@Ubuntu-Desktop:~/cricket$ rm usb_modeswitch
rm: cannot remove `usb_modeswitch': No such file or directory
garry@Ubuntu-Desktop:~/cricket$ make
make: Warning: File `Makefile' has modification time 1.4e+08 s in the future
gcc -l usb -o usb_modeswitch usb_modeswitch.c
usb_modeswitch.c:60:17: error: usb.h: No such file or directory
usb_modeswitch.c: In function ‘main’:
usb_modeswitch.c:327: error: dereferencing pointer to incomplete type
usb_modeswitch.c:327: error: dereferencing pointer to incomplete type
usb_modeswitch.c:328: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘switchHuaweiMode’:
usb_modeswitch.c:517: error: ‘USB_TYPE_STANDARD’ undeclared (first use in this function)
usb_modeswitch.c:517: error: (Each undeclared identifier is reported only once
usb_modeswitch.c:517: error: for each function it appears in.)
usb_modeswitch.c:517: error: ‘USB_RECIP_DEVICE’ undeclared (first use in this function)
usb_modeswitch.c:517: error: ‘USB_REQ_SET_FEATURE’ undeclared (first use in this function)
usb_modeswitch.c: In function ‘switchSonyMode’:
usb_modeswitch.c:577: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘checkSuccess’:
usb_modeswitch.c:647: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘search_devices’:
usb_modeswitch.c:721: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:721: error: dereferencing pointer to incomplete type
usb_modeswitch.c:723: error: dereferencing pointer to incomplete type
usb_modeswitch.c:723: error: dereferencing pointer to incomplete type
usb_modeswitch.c:724: error: dereferencing pointer to incomplete type
usb_modeswitch.c:724: error: dereferencing pointer to incomplete type
usb_modeswitch.c:726: error: dereferencing pointer to incomplete type
usb_modeswitch.c:728: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘find_first_bulk_output_endpoint’:
usb_modeswitch.c:745: error: dereferencing pointer to incomplete type
usb_modeswitch.c:748: error: dereferencing pointer to incomplete type
usb_modeswitch.c:749: error: dereferencing pointer to incomplete type
usb_modeswitch.c:750: error: dereferencing pointer to incomplete type
usb_modeswitch.c:750: error: ‘USB_ENDPOINT_TYPE_MASK’ undeclared (first use in this function)
usb_modeswitch.c:750: error: ‘USB_ENDPOINT_TYPE_BULK’ undeclared (first use in this function)
usb_modeswitch.c:751: error: dereferencing pointer to incomplete type
usb_modeswitch.c:751: error: ‘USB_ENDPOINT_DIR_MASK’ undeclared (first use in this function)
usb_modeswitch.c:752: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘find_first_bulk_input_endpoint’:
usb_modeswitch.c:762: error: dereferencing pointer to incomplete type
usb_modeswitch.c:765: error: dereferencing pointer to incomplete type
usb_modeswitch.c:766: error: dereferencing pointer to incomplete type
usb_modeswitch.c:767: error: dereferencing pointer to incomplete type
usb_modeswitch.c:767: error: ‘USB_ENDPOINT_TYPE_MASK’ undeclared (first use in this function)
usb_modeswitch.c:767: error: ‘USB_ENDPOINT_TYPE_BULK’ undeclared (first use in this function)
usb_modeswitch.c:768: error: dereferencing pointer to incomplete type
usb_modeswitch.c:768: error: ‘USB_ENDPOINT_DIR_MASK’ undeclared (first use in this function)
usb_modeswitch.c:769: error: dereferencing pointer to incomplete type
make: *** [usb_modeswitch] Error 1
garry@Ubuntu-Desktop:~/cricket$ sudo make install
make: Warning: File `Makefile' has modification time 1.4e+08 s in the future
gcc -l usb -o usb_modeswitch usb_modeswitch.c
usb_modeswitch.c:60:17: error: usb.h: No such file or directory
usb_modeswitch.c: In function ‘main’:
usb_modeswitch.c:327: error: dereferencing pointer to incomplete type
usb_modeswitch.c:327: error: dereferencing pointer to incomplete type
usb_modeswitch.c:328: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘switchHuaweiMode’:
usb_modeswitch.c:517: error: ‘USB_TYPE_STANDARD’ undeclared (first use in this function)
usb_modeswitch.c:517: error: (Each undeclared identifier is reported only once
usb_modeswitch.c:517: error: for each function it appears in.)
usb_modeswitch.c:517: error: ‘USB_RECIP_DEVICE’ undeclared (first use in this function)
usb_modeswitch.c:517: error: ‘USB_REQ_SET_FEATURE’ undeclared (first use in this function)
usb_modeswitch.c: In function ‘switchSonyMode’:
usb_modeswitch.c:577: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘checkSuccess’:
usb_modeswitch.c:647: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘search_devices’:
usb_modeswitch.c:721: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:721: error: dereferencing pointer to incomplete type
usb_modeswitch.c:723: error: dereferencing pointer to incomplete type
usb_modeswitch.c:723: error: dereferencing pointer to incomplete type
usb_modeswitch.c:724: error: dereferencing pointer to incomplete type
usb_modeswitch.c:724: error: dereferencing pointer to incomplete type
usb_modeswitch.c:726: error: dereferencing pointer to incomplete type
usb_modeswitch.c:728: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘find_first_bulk_output_endpoint’:
usb_modeswitch.c:745: error: dereferencing pointer to incomplete type
usb_modeswitch.c:748: error: dereferencing pointer to incomplete type
usb_modeswitch.c:749: error: dereferencing pointer to incomplete type
usb_modeswitch.c:750: error: dereferencing pointer to incomplete type
usb_modeswitch.c:750: error: ‘USB_ENDPOINT_TYPE_MASK’ undeclared (first use in this function)
usb_modeswitch.c:750: error: ‘USB_ENDPOINT_TYPE_BULK’ undeclared (first use in this function)
usb_modeswitch.c:751: error: dereferencing pointer to incomplete type
usb_modeswitch.c:751: error: ‘USB_ENDPOINT_DIR_MASK’ undeclared (first use in this function)
usb_modeswitch.c:752: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘find_first_bulk_input_endpoint’:
usb_modeswitch.c:762: error: dereferencing pointer to incomplete type
usb_modeswitch.c:765: error: dereferencing pointer to incomplete type
usb_modeswitch.c:766: error: dereferencing pointer to incomplete type
usb_modeswitch.c:767: error: dereferencing pointer to incomplete type
usb_modeswitch.c:767: error: ‘USB_ENDPOINT_TYPE_MASK’ undeclared (first use in this function)
usb_modeswitch.c:767: error: ‘USB_ENDPOINT_TYPE_BULK’ undeclared (first use in this function)
usb_modeswitch.c:768: error: dereferencing pointer to incomplete type
usb_modeswitch.c:768: error: ‘USB_ENDPOINT_DIR_MASK’ undeclared (first use in this function)
usb_modeswitch.c:769: error: dereferencing pointer to incomplete type
make: *** [usb_modeswitch] Error 1
garry@Ubuntu-Desktop:~/cricket$

---

### Post by beastrace91 on 2009-08-11
Sorry I think I forgot to mention in my first post that you need an active internet connection for these two commands to work on the 64bit install

```
garry@Ubuntu-Desktop:~/cricket$ sudo apt-get install build-essential
[sudo] password for garry:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential
garry@Ubuntu-Desktop:~/cricket$ sudo apt-get install libusb-dev
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package libusb-dev
```

Notice how it is saying it cannot find the packages? Thats because it looks for them online. In other words you need to get a wired connection to install these packages before you can recompile usb_modeswitch for 64bit.

~Jeff

---

### Post by 00bofh on 2009-08-12
Similar issue here - jusr acquired a cricKet A600 aircard and successfully activated /connected in MS Windows.

Ubuntu 9.04 (Jaunty) 64-bit, clean install about a week after stable release.

On running 'sudo flipflop.sh' I see:

[FONT=Courier New]$ sudo flipflop.sh

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009                              
 * Works with libusb 0.1.12 and probably other versions             

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...           
 Found default devices (1)                
 Found a default device NOT in target class mode
Prepare switching, accessing device 004 on bus 002 ...
Looking for active driver ...                         
 OK, driver found ("usb-storage")                     
 OK, driver "usb-storage" detached                    
Setting up communication with interface 0 ...         
Trying to send the message to endpoint 0x08 ...       
 OK, message successfully sent                        
-> Run lsusb to note any changes. Bye                 

Tray::slotDeviceAddedNotify

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009                              
 * Works with libusb 0.1.12 and probably other versions             

Looking for default devices ...
 Found default devices (1)     
Prepare switching, accessing device 005 on bus 002 ...
Resetting usb device DeviceStore::slotDeviceRemoved   
Tray::slotDeviceRemovedNotify                         
.                                                     
 OK, device was reset                                 
-> Run lsusb to note any changes. Bye
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller            
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1199:0218 Sierra Wireless, Inc. MC5720 Wireless Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 1f28:0020
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]     

NetworkManager reports a new device:

ttyACM0

Which is in "State: Disconnected" status.

Setting up a new connection runs me through a series of screens asking for username /password (???, not needed in Windows) and setting COM port speeds.

On "Connect and Save", no errors are seen /popped, but connection never completes and status is still disconnected.

Per debug instructions in other posts I ran:

[FONT=Courier New]$ sudo /usr/sbin/usb_modeswitch

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye![/FONT]  

Again, ????

Anything I can try /test /provide to help me figure out the issue?

Thanks,

--
Ed

---

### Post by beastrace91 on 2009-08-12
Ed,

Your issue is different than the one in the above post. From what I can see the device is recognizing and "flipping" properly. You do not have to set anything up in the network manager, shortly after running the flipflop.sh (between 10 and 60 seconds I've found depending on the system) clicking on your network manager should display an "Auto Broadband Connection" selecting it should then connect your cricket device. Does this option not appear?

~Jeff

---

### Post by Expiercing on 2009-08-12
I followed your directions and it does work but it stops working whenever it wants.  It will disconnect and the network manager will say not active then i will not be able to connect to the broadband or wireless connections until i reboot and do it all over again. This is very frustrating any ideas?  thanks in advance Rick

---

### Post by Expiercing on 2009-08-12
Im running ubuntu 9.04 and i followed your directions.  Everything went as planned Ubuntu recognized my a600 and i was connected.  Then I get disconected and my network manager said not active.  When this happens i cant connect to the broadband or wireless.  Any thoughts,  Rick

---

### Post by beastrace91 on 2009-08-12
How many bars does your modem display when it randomly disconnects? The only time I have ever had any issues is when my signal strength is low. 

~Jeff

---

### Post by 00bofh on 2009-08-13
Nope - no option for "cricKet Broadband" or anything else.  Just sits there looking active but not passing traffic...

I'm pretty good at following complex direction sets, so if there's further debug commands I can issue, let me know...

--
Ed V.

---

### Post by beastrace91 on 2009-08-13
Try this, connect the device and then run the flipflop.sh after that runs successfully run the following command in terminal: ```
sudo usb_modeswitch -v 0x1f28 -p 0x0020 -R 1
``` 

After that command runs it should appear in your network manager - if it still does not at that point it is an issue with the network manager and not the flipflop script

It will appear as "Auto Mobile Broadband (CDMA) connection" in the network manager under mobile broadband (below wired networks but above wireless)

~Jeff

---

### Post by Expiercing on 2009-08-13
I have at least two bars anywhere in my house but it has happened with four when i reset the fun flip flop again it resets and works again. ?

---

### Post by beastrace91 on 2009-08-13
Huh, I am thinking this is an issue with your Network manager... does the device work perfectly fine on Windoze?

~Jeff

---

### Post by Expiercing on 2009-08-14
Windoze was fine I only used it that one time when i activated but i was online 4 a while without a problem.  Rick

---

### Post by beastrace91 on 2009-08-14
Mmm well if it works fine in Winblows but is randomly disconnecting on Ubuntu it is an issue with your network manager I hate to say :/

~Jeff

---

### Post by Vascryl on 2009-08-15
My problem is quite frustrating, i have no idea what to do when the command : "sudo make install" comes up in this forum page, everytime i try it, it says "rm: cannot remove 'usb_modeswitch': Is directory"... what do i do from here to get back on to the forum standards, to finish the main problem?
(any leads will be greatly appreciated)-Vas

---

### Post by Vascryl on 2009-08-15
Nevermind guys i just fixed it, seems my Fn key kept sticking without me knowing everytime i tried to change directories, thanks for everyone's info and help! -Vas

---

### Post by beastrace91 on 2009-08-16
Glad you have it working Vas :)

~Jeff

---

### Post by pimpinkid on 2009-08-21
Hey guys. I have followed all the steps and I still cant connect. It will try for about 30 sec to connect then says Network Disconnected. You are now offline. the flipflop seems to be working find and I see the Auto Mobile Broadband (CDMA) connection in the network manager, but after that first time it trys to connect, when I try to connect again it just says I am disconnected. Any help would be appreciated. 


Thanks,

---

### Post by beastrace91 on 2009-08-22
Have you connected the modem to a Winblows/OSX system and activated the modem already?

~Jeff

---

### Post by Tuxaby on 2009-08-23
I followed the how to without results, but through reading through the posts I found one that referenced changing the sleep time to more than default in the flipflop.sh file in the extracted files.  It was 10 so I doubled it to 20, ran the sudo .flipflop.sh.  Waited, being very patient, and finally Cricket showed up in my network connections.  Clicked on it and was connected without any more problems.

Also discovered that when restarting, I have  to cd to the extracted files before running  sudo ./flipflop.sh.


[[COLOR=Black]Thanks beastrace91[/COLOR].]("http://ubuntuforums.org/member.php?u=341545")

---

### Post by beastrace91 on 2009-08-24
Glad you got it working, I'll add those two pieces of information to the first post :)

~Jeff

---

### Post by pimpinkid on 2009-08-28
sorry for the delayed response. its working fine. mu cricket card was suspended and i had no valid connection. thanks for the help.

---

### Post by beastrace91 on 2009-08-29
> **pimpinkid said:**
> sorry for the delayed response. its working fine. mu cricket card was suspended and i had no valid connection. thanks for the help.

Not a problem. Glad to know you got it working at any rate.

~Jeff

---

### Post by SoBeLife on 2009-09-19
The problem that I'm having is the the Cricket A600 USB device does not appear in the
network manager as a connection option and still shows up in "Computer - File
Browser" mounted as a "2.0 GB Media" (while a 2.0 micro SD card is in the
device) even after I have successfully completed all of the following steps

Step 1:

Download the archive attached to this post and extract the contents to your
preferred directory.

Step 2:

Open up terminal and use cd to change into the directory of the extracted files.

32 bit Users - Install usb_modeswitch with the following command:
Code:

sudo make install

Step 3:

I plug in my Cricket A600 to an open USB port, and wait a moment for it to be
detected as "2.0 GB Media" (while a 2.0 micro SD card is in the device) and the
auto play menu pops up

I execute the flipflop.sh with the following

code:
chmod +x flipflop.sh

code:
sudo ./flipflop.sh

and I receive the following results in GNOME Terminal:
:~> cd Desktop/whatever_dir
:~/Desktop/whatever_dir> sudo make install
root's password:
mkdir -p /usr/sbin
install ./usb_modeswitch /usr/sbin
mkdir -p /etc
install ./usb_modeswitch.conf /etc
:~/Desktop/whatever_dir> chmod +x flipflop.sh
:~/Desktop/whatever_dir> sudo ./flipflop.sh


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 Found a default device NOT in target class mode
Prepare switching, accessing device 004 on bus 002 ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x08 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 005 on bus 002 ...
Resetting usb device .
 OK, device was reset
-> Run lsusb to note any changes. Bye

:~/Desktop/whatever_dir> lsusb
Bus 002 Device 005: ID 1f28:0020 
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 05fe:1010 Chic Technology Corp. Optical Wireless
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

but if I repeat the exact same steps (while a 2.0 micro SD card is NOT in the
device) the Cricket USB device still does not appear in the network manager as a
connection option, the auto play menu does NOT pop up as soon as the Cricket USB
device is detected but it does show up as an unmounted USB Drive

and I receive the following results in GNOME Terminal:
:~> cd Desktop/whatever_dir
:~/Desktop/whatever_dir> sudo make install
root's password:
mkdir -p /usr/sbin
install ./usb_modeswitch /usr/sbin
mkdir -p /etc
install ./usb_modeswitch.conf /etc
:~/Desktop/whatever_dir> chmod +x flipflop.sh

:~/Desktop/whatever_dir> sudo ./flipflop.sh
 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 Found a default device NOT in target class mode
Prepare switching, accessing device 004 on bus 002 ...
Looking for active driver ...
 OK, driver found ("usb-storage")
| <--then the GNOME Terminal insertion point just sits there indefinitely and
flashes... nothing else happens after this point

---

### Post by Tuxaby on 2009-09-19
Have you tried changing the sleep time in the flipflop.sh file?

---

### Post by SoBeLife on 2009-09-20
So if you all are really better than Windows Microsoft... than why don't you all put your money where your mouths are by connecting the Cricket A600 USB Broadband Modem to your BLASTED OS, huh?!?!?!

---

### Post by Tuxaby on 2009-09-20
> **SoBeLife said:**
> So if you all are really better than Windows Microsoft... than why don't you all put your money where your mouths are by connecting the Cricket A600 USB Broadband Modem to your BLASTED OS, huh?!?!?!

I know how frustrating getting things to work can be, but it's free, unlike Windoze, and I find having to work at it worth it.  If you really want to fix it then do as I did and read all the posts in this thread.  That's how I found my solution, increasing the sleep time in the flipflop.sh file in the extracted files folder.  It took several days to get mine working, but  was definitely worth it as it works better in Ubuntu than it ever has in Windoze.  If you are going at it over and over,   I did find  that after a failed attempt that I need to reboot before trying again or I get nowhere.   Keep in mind that this is a new piece of hardware and will undoubtedly be resolved by the community.  I know this because my Broadcom wireless on my laptop took me a month or better to get working and was difficult to reinstall on a new installation and now is listed in the Hardware Drivers list and is very easy to get working.   Hang in there, this forum has solved every problem I have come across.  It's populated by a great group of people.

---

### Post by beastrace91 on 2009-09-20
> **SoBeLife said:**
> So if you all are really better than Windows Microsoft... than why don't you all put your money where your mouths are by connecting the Cricket A600 USB Broadband Modem to your BLASTED OS, huh?!?!?!

A.) If you are going to be like this bugger off - you are not welcome here.

B.) Do you think Microsoft spent any time at all getting that Cricket A600 working on Winblows? No they did not. The face that it does not work by default on Ubuntu is actually 100% Cricket's fault, Ubuntu already contains all the drivers needed to work the modem but Cricket failed to write the code to allow it to show up as the correct device(s) when connected to a Linux system. They have Mac and Windoze drivers on that auto-connect wizard - they have nothing for Nix.

C.) Honestly being free has very little to do I feel with how much time you spend working on the OS. I work as an IT for a small office (all Winfail) and I'm spent more than a full 40 hour week chasing down bugs/errors the that terrible platform as well.

Also yes - try increasing the time in the flipflop.sh - a sleep of 10 works perfectly fine on my two laptops but yours might require a slightly longer one.

My 2 pence,
~Jeff

---

### Post by perezomail on 2009-09-21
im on fedora 10 using an acerone 1101722 in tryng some of these instructions they for the most part seemed promising however lsusb does not read the drive at all [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
said 
Cricket A600
Switches to ACM device. Might need a ResetUSB after switching - or not 
EpiValley SEC-7089 (featured by Alegro and Starcomms / iZAP)
ST Mobile Connect HSUPA USB Modem

im on here cause fedora form has no responces at all

i may be able to solves this if i knew the responces that are needed
vendor number so on

still unsure why the network manager doesnt pickit up automatically or even what info to incude if it did pick it up in soe areas

---

### Post by beastrace91 on 2009-09-22
These instructions should work on Fedora just fine. (No reason why they shouldn't) Are you running 32bit or 64bit? Did you get mode flip successfully installed? Connect the device and then post the out put from lsusb please.

~Jeff

---

### Post by kogerat on 2009-09-22
I'm a nub to Linux and Ubuntu and your directions in the first post worked without a hitch. Great work. Thanks!! I called Cricket tech support, and they said they did not have any plans to support Linux. Guss they do not like the free ware movement.

---

### Post by beastrace91 on 2009-09-22
Glad this worked for you, I tried to make the directions as simple as possible :) 

And this is [Open Source](http://en.wikipedia.org/wiki/Open_source) its still free of cost but a bit different from [freeware](http://en.wikipedia.org/wiki/Freeware) ;)

~Jeff

---

### Post by risen75 on 2009-09-25
Alright... I followed directions hoping that it would work... now i'm not using the a600, i've got the um185c from cricket..  does anyone know how to get this one working? 

for a little bit of help when i run flipflop.sh this is the output

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye!


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 No default device found. Is it connected? Bye!





Any  ideas? it shows up as a the cd rom like you said it would... 
I'm curious.. could i just run it under Wine?  otherwise.. i'm lost 
I can't seem to find any posts ANYWHERE about the um185c (it must be really new...) so i'm turning to the experts here.. (yes i read through the whole post hoping that someone else had tried this one too) otherwise.. i'm gonna have to use winblowz while mobile (BLEH! no built in ssh support :( )

---

### Post by risen75 on 2009-09-25
Alright... I followed directions hoping that it would work... now i'm not using the a600, i've got the um185c from cricket..  does anyone know how to get this one working? 

for a little bit of help when i run flipflop.sh this is the output

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye!


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 No default device found. Is it connected? Bye!


Also when here's my lsusb output:

Bus 002 Device 003: ID 106c:3b06 Curitel Communications, Inc. (This is the device.. ran with and without and this was the ONLY change between them..)


Any  ideas? it shows up as a the cd rom like you said it would... 
I'm curious.. could i just run it under Wine?  otherwise.. i'm lost 
I can't seem to find any posts ANYWHERE about the um185c (it must be really new...) so i'm turning to the experts here.. (yes i read through the whole post hoping that someone else had tried this one too) otherwise.. i'm gonna have to use winblowz while mobile (BLEH! no built in ssh support :( )

---

### Post by beastrace91 on 2009-09-26
Unfortunately it will not work under Wine, how ever if you have a Winblows license a temp fix is booting a VM and assigning the device to it, connecting it and then assigning it back to Ubuntu (it is a pain but it works)

In the mean time lets get hacking to make your um185c working with modeswitch.

First off post the section of your modem listed when you run ```
lsusb -v
``` in terminal. For instance my A600 displays as such: ```
Bus 003 Device 002: ID 1f28:0021  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1f28 
  idProduct          0x0021 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

```

Next you are going to need to go get and install [USB Snoop](http://www.pcausa.com/Utilities/UsbSnoop/default.htm) on either a Windoze VM or system you have access too. Then you are going to need to connect the modem and install a "filter" on the UNFLIPPED device using USB Snoop, then upon reconnecting it to the system it will generate a UsbSnoop.log. In this file we are looking for lines that look something like the following (your exact numbers will be different) ```
  PipeHandle           = 88bced1c [endpoint 0x00000005]
  TransferFlags        = 00000000 (USBD_TRANSFER_DIRECTION_OUT, ~USBD_SHORT_TRANSFER_OK)
  TransferBufferLength = 0000001f
  TransferBuffer       = 88c4b790
  TransferBufferMDL    = 00000000
    00000000: 55 53 42 43 90 4e d6 8a 24 00 00 00 80 00 08 ff
    00000010: 02 44 45 56 43 48 47 00 00 00 00 00 00 00 00

```

Post all the information I listed above and I'll will give you a hand editing the modeswitch so it will work with your device.

Also here is some more reading if you are wondering how I figured all this out:
[Using a UM175AL with Ubuntu](http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html)
[My thread on the modeswitch forums](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=148&postdays=0&postorder=asc&start=0)

Best of Luck,
~Jeff

---

### Post by kevcart3 on 2009-09-26
I have a question about another mobile broadband modem that has a disk mode as well. I have a Franklin CDU-680 which boots in Jaunty in disk mode, I've tried running the connect script, which gives a segmentation fault error. Could these instructions possibly solve this problem?

If not, does anyone have a post that they could link to for some help on this, I am having a lot of trouble getting this device to work under ubuntu.

---

### Post by beastrace91 on 2009-09-26
> **kevcart3 said:**
> I have a Franklin CDU-680 which boots in Jaunty in disk mode

It did a quick search and it appears your CDU-680 should work with the latest version of [usb_modeswitch](http://www.draisberghof.de/usb_modeswitch/) also be sure to read [this thread](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=69) detailing more information on your specific modem.

If you run into any bumps/trouble feel free to let me know and I'll do my best to help you along.

~Jeff

---

### Post by kevcart3 on 2009-09-26
> **beastrace91 said:**
> It did a quick search and it appears your CDU-680 should work with the latest version of [usb_modeswitch](http://www.draisberghof.de/usb_modeswitch/) also be sure to read [this thread](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=69) detailing more information on your specific modem.

If you run into any bumps/trouble feel free to let me know and I'll do my best to help you along.

~Jeff

edit: okay, back from trying a few things with no luck. Sorry if I'm kinda rusty, I haven't used Linux in about 3 years, so there's a lot I don't remember.

First off, I tried editing the .conf file to get things working, but I got several errors when executing the command, here's the output:

```
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 000 on bus 001 ...
Using endpoints 0x02 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"

Device description data (identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: not provided
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.
```

Running dmesg afterwards, I still get an entry called "CMOTECH Mass Storage", so I know it's not switching the modes correctly.

The thread linked mentioned a specific command the OP ran:

```
usb_modeswitch -v 0x16d8 -p 0x6803 -m 0x07 -M 5553424308e0408524000000800008ff524445564348470000000000000000
```

With the same output as letting the command use the .conf file.

any help is greatly appreciated, thanks a lot.

---

### Post by beastrace91 on 2009-09-26
Can you post the output of your modem's entry for ```
lsusb -v
```

Thanks,
~Jeff

---

### Post by kevcart3 on 2009-09-26
> **beastrace91 said:**
> Can you post the output of your modem's entry for ```
lsusb -v
```

Thanks,
~Jeff

Yeah sure,

```
Bus 001 Device 006: ID 16d8:6803 CMOTECH Co., Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x16d8 CMOTECH Co., Ltd.
  idProduct          0x6803 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

```

Also noticed a lot of this error popping up throughout when I run the command;

```
cannot read device status, Operation not permitted (1)

```

---

### Post by beastrace91 on 2009-09-26
Alright, all the information listed there looks ok based on the command you ran. Can you also follow the instructions in my post on page 8 for getting the info log using USBSnoop?

Thanks,
~Jeff

---

### Post by kevcart3 on 2009-09-27
> **beastrace91 said:**
> Alright, all the information listed there looks ok based on the command you ran. Can you also follow the instructions in my post on page 8 for getting the info log using USBSnoop?

Thanks,
~Jeff
Okay, when I run the usbsniff program, there are 4 devices listed on the program for my modem, I ran it for the one labeled "USB Composite Device" here was the output:

```

  PipeHandle           = 84dec50c
  TransferFlags        = 91ddea1f (USBD_TRANSFER_DIRECTION_IN, USBD_SHORT_TRANSFER_OK)
  TransferBufferLength = 00000012
  TransferBuffer       = 855ffd5c
  TransferBufferMDL    = 84deab70
    00000000: 12 01 10 01 00 00 00 40 d8 16 03 68 00 00 01 02
    00000010: 00 01

```

The Other devices listed are:
Data Modem @ CDMA (6803) 
Data Modem @ CDMA Diagnostic Serial Port (6803)
Data Modem @ CDMA GPS Port (6803)

When I run the program on those other three devices listed, the output either doesn't contain what you asked for, or I get a BSOD and have to do a system restore point in windows.

---

### Post by beastrace91 on 2009-09-27
Is there a pipe handle line in the log anywhere that contains a message end point as such: ```
PipeHandle           = 88bced1c [endpoint 0x00000005]
```

~Jeff

---

### Post by kevcart3 on 2009-09-27
This appears tons of times in the log file for the Composite Device:

```
  PipeHandle           = 8683e2dc [endpoint 0x00000007]
```

---

### Post by beastrace91 on 2009-09-27
Run ```
sudo gedit /etc/usb_modeswitch.conf
```

And try to add the following lines to the bottom of the file: ```
DefaultVendor = 0x16d8
DefaultProduct = 0x6803

MessageEndpoint = 0x07
MessageContent = "1201100100000040d8160368000001020001"
```

Then try running ```
/usr/sbin/usb_modeswitch
``` and see if it finds your device.

~Jeff

---

### Post by kevcart3 on 2009-09-27
No luck this time either. Running lsusb -v still yields the same results after running the usb_modeswitch command.

I noticed this time I ran the command, the "Product" & "Manufacturer" fields aren't blank anymore, maybe this is a step in the right direction.

```
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 006 on bus 001 ...
Using endpoints 0x07 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

Device description data (identification)
-------------------------
Manufacturer: CMOTECH CO., LTD.
     Product: CMOTECH CDMA Technologies
  Serial No.: not provided
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x07 ...
 Sending the message returned error -16. Trying to continue
 Device is gone, skipping any further commands
-> Run lsusb to note any changes. Bye.

```

still, nothing shows up in the network manager or indicates that anything has changes, the device is still displayed on the desktop as a disk.

---

### Post by beastrace91 on 2009-09-27
I am a bit lost at this point then, perhaps try registering an account on the usb_modeswitch forums as at this point it is an issue with their software :(

Sorry,
~Jeff

---

### Post by kevcart3 on 2009-09-28
> **beastrace91 said:**
> I am a bit lost at this point then, perhaps try registering an account on the usb_modeswitch forums as at this point it is an issue with their software :(

Sorry,
~Jeff

Again, thanks a lot for the help, you've been very helpful with everything.

---

### Post by beastrace91 on 2009-10-06
Updated the first post to contain .deb installers to make this easier for new users to Ubuntu/Linux

~Jeff

---

### Post by thang thang on 2009-10-06
Does the .dev installers include "package libusb-dev"?  i am trying to set up an A600 modem from cricket, but i do not have a different connection for when i run get-apt install libusb-dev, so i guess i need to download the libusb-dev package seperately in order to get this working..... note* i am able to run get-install build-essential by using the ubuntu 9.04 amd64 disc i have, but when i try to look for the libusb-dev it still says that it cannot find package libusb-dev....i am new to linux, ubuntu is my first crack at this so please go easy on me :) any help will be greatly appreciated!

---

### Post by beastrace91 on 2009-10-06
Hey There,

You don't need to install build-essential or libusb-dev if you are using the .deb installer - thats the great things about precompiled packages they contain everything you need so you don't need to compile it yourself :)

If you are using 64bit just download [this deb](http://ubuntuforums.org/attachment.php?attachmentid=130984&d=1254841714) and install it and then download the [flipflop.sh](http://ubuntuforums.org/attachment.php?attachmentid=130987&d=1254841832) and run it(while your modem is attached) - then it should work for you :)

If you have any issues feel free to let me know,
~Jeff

---

### Post by thang thang on 2009-10-07
The .deb installer worked beautifully for me! thanks for the help :P

---

### Post by beastrace91 on 2009-10-07
Glad to hear it :)

~Jeff

---

### Post by Ilya154 on 2009-10-07
How can I install the Cricket UM185C Modem in Ubuntu.  Followed your instructions with the .deb file as well as the flipflop.sh however did not work for me as it could not see the Modem.  I am a nub to Linux Ubuntu so if possible please provide a really dumb down version of instructions.  Thanks!

---

### Post by beastrace91 on 2009-10-14
So just as a heads up to everyone - after the last round of updates on the Beta Karmic I am now plugging in my Cricket device and it is being auto detected by my network manager with out any "flipping" required - Hopefully this means this tutorial will soon be out dated :)

~Jeff

---

### Post by Crafty Kisses on 2009-10-14
Good howto, thanks!

---

### Post by beastrace91 on 2009-10-15
Glad it helped :)

~Jeff

---

### Post by kitsuneboom on 2009-10-15
Okay, okay. I know it's been hashed over and over again. 
I'm running not one but two acer aspires.  One dual booting Windows XP with Sp4 and Jaunty Jackalope 9.04. The other running a straight Jackalope 9.04. Ubuntu Netbook Remix.
How?
How do caveman make glow box work?

Sorry, that's about how I feel right now. I've read over every page of this thread, and nothing...*nothing* has worked. Plz to halp me?

Edit: I typed 9.10. I was sure that was what it was. :/

---

### Post by beastrace91 on 2009-10-15
Kit,

I am slightly confused by your post - you are trying to get your Cricket A600 working on Ubuntu 9.04 correct? Also you say you have read through everything and tried it all - what exactly have you tried and at what point does it "not work"

Help me, help you,
~Jeff

---

### Post by kitsuneboom on 2009-10-15
Let me try... This computer has the original ubuntu netbook remix. and has never been online and unless I get this thing to work I cant download from ubuntu's add or remove, but I have installed the "cricket_flip_i386.deb" file from one of the sites, that I found, and the instruction after that was to run "flipflop.sh" but at that point it never asks for a passcode like the instuctions say should happen. I went to see if the wireless then worked but it never shows. (This is my girlfriends work so im not to in the loop, sorry-she was trying to help me but ended up doing more of it) 
The other thing we tried was just plugging in the modem and then put our phone number with the cricket address. and then setting the passcode to cricket and that was of no luck. Well thats about all we tried I guess. 
Dude I hope this helps you help us.

---

### Post by beastrace91 on 2009-10-15
Ahh my mistake in the instructions for using the .deb installers - after you download the flipflop.sh - right click on it and select "properties". Click over to the "permissions" tab, and check the box "allow executing file as a program"

Now double click the file and select run - it will ask you for your password. After you enter it wait a few moments and it should appear in your network manager. (Also be sure you have activated the Cricket Modem on a Windows system first)

Sorry for the confusion (I also updated the first post to reflect this information)
~Jeff

---

### Post by kitsuneboom on 2009-10-22
Hey thank you finally got it working, You Are Truly A Guitar Hero:guitar:

---

### Post by tara.chrest on 2009-10-30
**ey there... ok so I am NOT knowledgable about linux.... I actually only have it because if came with the system I bought.... I am having some outrageous issues with it and am wondering you could help me...... Please?**

---

### Post by pdc on 2009-10-31
welcome to the Ubuntu forums tara.chrest

do you believe you have Ubuntu running on your computer? 

this thread is about how to configure a Cricket Wireless A600 Broadband Modem;

are you trying to configure a Cricket Wireless A600 Broadband Modem??

---

### Post by beastrace91 on 2009-10-31
I am slightly confused as to your issue... What is it? Check the link in my sig about asking smart questions...

~Jeff

---

### Post by psnead on 2009-11-07
I know this thread is for the A600 Broadband Modem, but I've seen several posts asking about the Cricket UM185C usb modem, and I've gotten mine working.

Here are the relevant strings for the UM185C:
vendor code: 0x106c
product code: 0x3b06
message endpoint: 0x05
message content: "55534243904ed68a24000000800008ff024445564348470000000000000000"

So my usb_modeswitch command looks like this (all on one line):
sudo ./usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff024445564348470000000000000000"

After running the command, the UM185C shows up as ttyACM0.  Network Connections then allows me to add a new Mobile Broadband Connection, and the modem is a Pantech USB Modem.

I'm running Ubuntu 9.10. HTH

- Patrick

---

### Post by beastrace91 on 2009-11-07
Very awesome. I'll post a second file containing that command so people with the UM185C can use this as well.

Edit: If someone with a UM185C would be kind enough to check and see if my posted .sh files works that would be great :)

Thanks,
~Jeff

---

### Post by UwantoLinux on 2009-11-10
For Cricket, This is what I did.
I installed the Ubuntu 9.10. Before that I used Linux Mint. Which I liked better. But it had issues I don't have time to discuss.  I have Cricket broadband. I love it. My problem was I really did not want to give up my beloved linux to run it in windows. So, I found this web-page on what to do.  I now have my cricket broadband in Ubuntu linux. I did not have to use gnome PPP or any dial progam. Simply edit connections on the network icon.
 Leave #777
User name is: (501)The phone [email]number@mycricket.com[/email]. The password is: cricket. This is done in the mobile broadband of the network connection at the top right of the desktop tool bar. One way to get to it is to put your mouse on the network icon then right click on Edit connections. Then click on Mobile Broadband. Click On the add icon choose your provider.  You will have to enter your root password at some point. Then click on edit. Enter your info.
#777
 501The phone [email]number@mycricket.com[/email]   
cricket

as the instructions say. double click on the flipflop.sh. 

Note: This is a short recap. You must follow the install instructions before you can finish.
I spent 3 weeks up till now trying to get my broadband to work. So when I finally did. It was an experience I have no words to describe. Up till now. I edited the cricket connection on a separate laptop with windows XP. I then enabled sharing on the windows network icon in Windows. Then I plug-ed an ethernet cable between the two computers so I could have mobile broad band in Linux until today. When I finally got it to work using the instructions above. I would like to encourage the Ubuntu developers to put in support for mobile broad band on there next release. It really should be a top priory. I almost had to give up my beloved Linux to keep my broadband. Thanks to this 
web page I can keep Linux. Thanks to the original person or persons whom put this web page up.

---

### Post by beastrace91 on 2009-11-10
Glad to hear you got it working - just as a heads up though after running the flipflop.sh you shouldn't need any of that extra configuration you listed for the network manager, it takes care of all of it for you :)

Cheers,
~Jeff

---

### Post by pbjohnk on 2009-11-11
Okay, I'm fairly new to ubuntu/linux
I've read all 12 pages, tried EVERYTHING
but this is what comes up
Unable to mount Cricket
Error mounting: mount exited with exit code 32: mount: block device /dev/sr1 is write protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/sr1, missing codepage or helper program or other error
Please help?
I'm still having to use vista right now...
Thanks a ton

---

### Post by pdc on 2009-11-11
don't you hate it when people aren't mind-readers?

You're gonna have to tell us what you did;

and then we can tell you what to do differently

---

### Post by pbjohnk on 2009-11-11
I downloaded the .deb and .sh files from the beginning, made sure t would run as a program, installed the .deb, ran the .sh.
Didn't do anything.
checked with lsusb, i didn't really know where to go from there.
I don't know how to get around the mount issue...

---

### Post by beastrace91 on 2009-11-11
What version of Ubuntu are you running? 32bit or 64bit? Did the .deb file say it installed properly? Could you please try running the flipflop.sh file from terminal and post the out it gives when it fails to work? Could you please attached your Cricket Modem to your system and post the output of **lsusb** while it is attached. Is your modem the A600 or the newer UM185c?

Regards,
~Jeff

---

### Post by pbjohnk on 2009-11-11
9.10
64-bit AMD Turion x2
Yeah it installed proberly
Here's what happens when it doesn't work:
john@john-laptop:~$ gksudo usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff02444556434847000 0000000000000"
gksudo: invalid option -- 'v'
GKsu version 2.0.2

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
john@john-laptop:~$ 





Here's the lsusb
john@john-laptop:~$ lsusb
Bus 003 Device 002: ID 106c:3b06 Curitel Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 12f7:1a23 Memorex Products, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And it's the UM185C

---

### Post by beastrace91 on 2009-11-11
Try running the following in terminal with the modem attached: ```
sudo usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff0244455643484 7000 0000000000000"
```

Just as a heads up I only have an A600 so I'm just helping you based on the information you and others have given me.

~Jeff

---

### Post by pbjohnk on 2009-11-11
So i went off of what you did
and i edited it a little bit
but
This worked
sudo usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff024445564348470000000000000000"

I'm typing this from KK :D
EDIT:
Here's the pastebin link, it doesn't show up correctly on here.
[http://pastebin.com/f29d250f4](http://pastebin.com/f29d250f4)
Also, on KK, it has to be run every time, maybe we should make it so it doesn't?
Automation script anyone?

---

### Post by beastrace91 on 2009-11-11
I'm fairly certain thats what I said to run in my above post - at any rate glad you got it working.

I've also updated the first post with a working .sh file for the UM185C

~Jeff

---

### Post by kencorbin on 2009-11-13
usb_modeswitch is now in the Ubuntu repository.   It isn't quite perfect.  It didn't take effect until I rebooted my machine.  And still won't recognize the modem if it is installed when you boot up.  But you just unplug the modem and plug it back in and it installs the Cricket broadband network which you can activate normally.  But it is darn close.

---

### Post by beastrace91 on 2009-11-13
The reason it did not work until you rebooted is because it requires are hard reset. And the new network manager detects modems that have already been attached - so after you flip it and the disconnect and reconnect it sees it.

FYI you can just installed modeswitch from the repos and then run the flipflop.sh and it will work a-ok.

Regards,
~Jeff

---

### Post by chicagofarker on 2009-11-19
This worked perfect on 64bit karmic koala for me. Made it easier to jump from being stuck on Windows only for this service. I've saved the files to the memory stick I put in the a600 for future use on my laptop, or other machines I have Ubuntu running on.

One note for some, and I think it's already indicated. If you don't see the normal A600 CD mounted, you'll need to unplug and replug the stick back in before commuting to an installation. (Figured that out, prior to performing this instruction set.)

Thanks much for the info, etc...

---

### Post by michael.patterson14 on 2009-11-20
I tried to download the .sh file for the UM185C but the the link is broken. I would really appreciate any help you could offer.

---

### Post by michael.patterson14 on 2009-11-20
OK update I finally got .sh file to download but when i ru it in the terminal i get this message

michael@michael-laptop:~/Downloads$ sudo ./cricketum185c.sh

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Error: MessageContent hex string has uneven length. Aborting.

  
Any ideas

---

### Post by beastrace91 on 2009-11-21
Try running the following command in terminal when the device is attached: ```
sudo usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff02444556434847000 0000000000000"
```

Regards,
~Jeff

---

### Post by ReverendFreeze on 2009-11-21
I keep getting the following results:
```
dragon@dragons-lair:~/Desktop$ sudo chmod +x cricketum185c.sh
dragon@dragons-lair:~/Desktop$ sudo ./cricketum185c.sh

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Error: MessageContent hex string has uneven length. Aborting.

```

I'm trying to install a UM185C modem and every time I hook it up I get the following error message:
```
UNABLE TO MOUNT CRICKET
Error mounting: mount exited with exit code 32: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

any ideas what may be the problem?  I'm going to lose my connection this evening, so a quick response is greatly appreciated...

---

### Post by beastrace91 on 2009-11-21
It looks like Ubuntu is failing to properly initially mount your device when you attach it. When you plug in the device does anything appear in your **Places** location on your Ubuntu menu? It should read the device by default as a CD drive (or some such thing). If it is not try attaching the device to a Windows system and "safely removing" it from there.

If that still does not work post the output of **lsusb** in Ubuntu while the device is attached. I'll do my best to help you but keep in mind I only have an A600 personally so I'm just going off of what other people have reported as working for them.

EDIT: Also if time is a factor feel free to message me on AIM and I'll do my best to help you get this sorted.

Regards,
~Jeff

---

### Post by ReverendFreeze on 2009-11-21
Hey Jeff,
It shows up as a cd labeled Cricket, but it still won't mount, output of lsusb follows:
```

dragon@dragons-lair:~$ sudo lsusb
Bus 002 Device 002: ID 106c:3b06 Curitel Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dragon@dragons-lair:~$ 

```
I don't have a windows system to work with, so plugging it into one and "Safely Remove" isn't an option...I've been going round and round with Cricket over this...their salesperson scammed me into buying this card by telling me I had 30 days to return it if it wouldn't work, when the reality was that I had 3 days to return it...Now they won't give me my money back, and I'm trying to avoid eating $125...any help is greatly appreciated...

---

### Post by beastrace91 on 2009-11-21
Sorry, I'm really kind of at a loss :-/ How did you install modeswitch - from my packages I provided or the Ubuntu repositories?

Also - if you do not have a Windows system, have you already activated the modem? This has to be done under an M$ or Apple OS

~Jeff

---

### Post by scourgex on 2009-11-23
I am having the same problem myself. Winders Vista completely crapped itself and somehow, impossibly, it managed to either thoroughly corrupt the HDD or otherwise mess Ubuntu, (I was dual-booting via GRUB) and I ended up wiping the HDD and doing a fresh install of the latest 64-bit Ubuntu (v9.10) via boot cd, less any microsh*t malware. Unfortunately, until now, I was booting Vista first, starting the modem and then rebooting directly to Ubuntu without a total hard shudown, which seemed to be the only way to make it run, and also a royal pain, especially since Vista was taking FOREVER to start up, and twice again longer to shutdown. I now have no winders install whatsoever on this machine, and I'm getting the same failure to mount. I can tell you, btw, that the "Curitel Communications" bit that was referenced in the lsusb output is the um185c modem, and I have the smae thing. But it refuses to mount, and when I run the "sudo ./cricketum185c.sh" command I get the following error :

> Error: MessageContent hex string has uneven length. Aborting.


If anyone can figure this nonsense out, I would be mighty obliged, as I am now in about the same pickle as that other fella, since Cricket is my sole connection, short of finding a wifi hotspot, which is what I am doing at this moment, to post this.

---

### Post by beastrace91 on 2009-11-23
Try this command please: ```
sudo ./usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff02444556434847000 0000000000000"
```

Also as a quick fix you could install Vista via virtual box - mount the device to it and then give it back to Ubuntu after it flips - its tacky but it works (thats what I did with my A600 until I got modeswitch working)

Regards,
~Jeff

---

### Post by scourgex on 2009-11-23
First, same result. Second, no vista install disc, came preloaded OEM on the machine (Yet another source of great irritation since it was Vista 32-bit and this machine was built from the ground up to be a 64-bit machine...Anyone else smell a conspiracy?) So no chance of VM Winders install. At least until I finally get my free Windows 7 upgrade. 

However, was roaming about via my "piece of crap fancy newfangled super-dooper cell phone" thingie's internet  (or rather the cut-down half-assed Sidekick version of internet) and discovered a page I cannot find anymore, or I would link to it, but followed the instructions given there and came up with the following command:

> sudo usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff024445564348470000000000000000"It worked! Modem still refuses to mount properly, but if I pop it in and execute that command string it connects. If I weren't so darned tired I'd fiddle some more to try and make it all work automatically without the need for any fiddling about.

EDIT: Fails to display properly in quote, as I suspect yours also failed to properly display, which might explain a few things. Remove the space between the last two bunches of zeroes.

EDIT2: Upon closer inspection, the failure to display properly *DEFINITELY* explains things, since my version appears moreorless identical to yours.

---

### Post by beastrace91 on 2009-11-24
So just to confirm running this in terminal got your UM185C working: ```
sudo usb_modeswitch -v 0x106c -p 0x3b06 -m 0x05 -M "55534243904ed68a24000000800008ff024445564348470000000000000000"
```

If I am understanding correctly?

Regards,
~Jeff

---

### Post by scourgex on 2009-11-24
That would be affirmative, yes. Mighty obliged for the prompt and courteous assistance, btw. Now, how exactly would I go about making this execute automatically every time the modem is plugged in?

EDIT: To clarify, it still throws an error upon auto mount and plainly refuses to mount any whichway. But, it *does* connect through modem after using that command.

---

### Post by beastrace91 on 2009-11-24
Alrighty I fixed the cricketum185c.sh in the first post to reflect what you reported working here.

As for it working automatically - I know as of 9.10 with my A600 it auto flips itself after I manually did it the first time. Beyond that it involves editing udev properties - something I never personally read enough about to get working.

Regards,
~Jeff

---

### Post by scourgex on 2009-11-24
Hmm. Updated the file with the new one. Still makes no difference. I run it per instructions in the first post and get:
> Looking for default devices ...
 No default device found. Is it connected? Bye.
I still have to manually run that command string in the terminal every time I put in the modem, and then it connects. As soon as I pull the modem or restart I have to enter the command longhand again. I'm not sure if I'm missing something here, or what. But at least it works, I suppose.

---

### Post by beastrace91 on 2009-11-24
Thats odd... All that file does is put that same command you are running in terminal (that is said to work) and run it.

~Jeff

---

### Post by scourgex on 2009-11-26
Hmm, it seems to be working now. I don't why it ought to matter, but it seems to be a matter of timing it just right. I have to plug in the modem and execute the file right about the same time as the failure to mount notification pops up. I seem to have gotten the hang of it, and have little trouble now, except when I forget to unplug and replug the modem after a reboot. And it would still be nice to figure out a way a automate the whole affair, but I tried a couple ideas i got off the 'net, and nothing seems to work. Oh well, at least I have a good connection now. Oddly enough, I seem to have much better performance and bandwidth on Ubuntu than I ever did on Vista, though I haven't the foggiest as to how that would be possible. At any rate, if anyone figures out a way to make the whole deal automatic, I'll check in here periodically, and I really appreciate your assistance in getting this thing working, Jeff.

---

### Post by michael.patterson14 on 2009-11-26
Hey guys i found an interesting thing out today. when you insert the modem and it tells you it cant mount it, if you go to the places [COLOR=Black][COLOR=#CC0000] ***directory***[/COLOR][****]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=Wj9&ei=URsPS4T7D4u3ngfR1rTMAw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBsQBSgA&q=directory&spell=1")[/COLOR] and see ware it shows the cricket as a cd and then eject it the system will automatically recognize the modem and you should be able to connect to the net after that. But you have to do it every time you boot up. I'm using the UM185C on ubuntu 9.10, so far it has worked for both the desktop and netbook remix.

---

### Post by mrwilky on 2009-11-28
Just  got a Cricket A600 going in mythbuntu 9.04 thanks to the info I found right here.
Can't believe how simple it was. Have also learned how to share the same A600 for local network use
in windows xp more then one computer on the network

---

### Post by guru2600 on 2009-11-29
Hi Yall... I been lurking several days now here and there trying how to get the UM185c modem to work with Ubuntu 910.   After much searching...ETC. My conclusion is... Just install the modem on a windows machine then yank it out and throw it in the linux box and viola...BAM ...it works..well it did for me:)  Now granted using windows is a bad thing and ubuntu/ cricket needs to get their cr ap together. I tried everything I could to not go o a windows system but as a net addict I had to;   Good luck and happy surfing

---

### Post by duanedragon on 2009-12-12
I cannot thank you enough for this. THANKS!

ATTENTION POWERPC USERS:

I use Ubuntu 9.04 on a 12 inch PowerBook G4. I had to follow the steps for the 64 bit guys to get this to work.


I was getting a little frustrated because when I put the A600 into a USB port the processor showed a brief activity spike but then nothing happened. I was expecting to see a new volume auto-mounted like an external hard drive. It was not until I read more about installing USB devices and started using the commands "lsusb" and "dmesg | grep usb" and noticed that my A600 was in fact being treated like another drive even though the GUI tools showed no trace of a USB drive or modem. This gave me the encouragement to try again, this time using the 64 bit instructions by accident.

---

### Post by beastrace91 on 2009-12-12
Yep, yep - the 64bit build instructions should work for any architecture :)

~Jeff

---

### Post by mrwilky on 2009-12-13
Does anybody know how to get the sms feature working in Ubuntu as it works in windows A600 Cricket

---

### Post by beastrace91 on 2009-12-13
> **mrwilky said:**
> Does anybody know how to get the sms feature working in Ubuntu as it works in windows A600 Cricket

This would require Cricket to code their software for Ubuntu. You can however load the Cricket Device up via a Windows VM and have it work that way. Personally this was never a big issue for me because I have unlimited text on my cell.

Regards,
~Jeff

---

### Post by MajinHeartless on 2009-12-18
Dude, you are awesome... but it works natively, you are the brains... you made it work perfectly... I have no Windows OS in this pc... followed your guide and I connected to it....

Awesome!

Finally I can remove windows from my laptops as well.

---

### Post by beastrace91 on 2009-12-18
Glad to hear it :D

~Jeff

---

### Post by deeinmetrodc on 2009-12-22
I got two bars and the thing works with ubuntu but my d/l speeds are about half that of a typical dsl line and about 1/4 of that compared to the verizon usb760 (novatel).  Is there any way to get this sucker working at 3g speeds?  Uh, yeah, i'm using the A600.  I had the verizon working great with wvdial before 9.10.  Maybe I'll give that a try...

---

### Post by deeinmetrodc on 2009-12-22
ok wvdial was a waste of time.... but seriously, how to get more speed from this sucker?  3g should run at 240k plus typically.... not 42k...  ?????   ????? ?????

---

### Post by beastrace91 on 2009-12-22
The speeds you are seeing are linked directly to the hardware and not the software.

~Jeff

---

### Post by mrwilky on 2010-01-01
Recently I upgraded from Mythbuntu 9.04 to 9.1. In 9.04 everything worked even in Virtual Box thx to some help from Jeff. The problem in 9.1 is that once linux mounts A600 it wont show in your virtual box windows xp . I got around that by coping the cricket file's from another computer and put them in the same place in the virtual windows xp  on 9.1 host . Don't ask me how but it works for me...

---

### Post by beastrace91 on 2010-01-01
> **mrwilky said:**
> Recently I upgraded from Mythbuntu 9.04 to 9.1. In 9.04 everything worked even in Virtual Box thx to some help from Jeff. The problem in 9.1 is that once linux mounts A600 it wont show in your virtual box windows xp . I got around that by coping the cricket file's from another computer and put them in the same place in the virtual windows xp  on 9.1 host . Don't ask me how but it works for me...

Sounds like quirky behavior that I'd be betting you can blame on something in the upgrade process from 9.04 to 9.10 - this is one of the many reasons I believe in clean installs and not upgrades. At any rate glad it works for you :)

~Jeff

---

### Post by mrwilky on 2010-01-02
It was a total trash and reload going from 9.04 to 9.1. Had trouble with virtual windows seeing the usb devises , once that was fixed came the trouble with the A600. I just copied the cricket file from another windows computer, ran the driver setup in the file, created a shortcut to the software on the desktop, work like a charm. The quirk as you call it is once the A600 is working in 9.1 it hides the autorun cd. 9.1 sees it as a cd drive therefore in virtual windows xp it don't see the drive and can not load the software from that drive. The A600 is plug and play in windows

---

### Post by vrkalak on 2010-01-23
I've been playing around with the idea of getting one of these A600 USB Modems ... they're FREE from Cricket.

The other day, I finally bought an A600 USB Modem from Cricket  Communications.

Apparently, there has been lots of problems on  getting this device to work in Ubuntu.
Several threads/posts about  this USB modem and fixes noted, both here and in Ubuntu-Geek Forums.
Mainly,  because it is also, a USB storage device, as well as, a Modem. There is  a 'usb_modeswitch' fix listed.

This is the only piece of  hardware that I've tried in Mint/Ubuntu that didn't work "out of the  box" ... at least, for me.
I bought this USB Modem for my laptop that  has Mint-7 Xfce on it, as I'm not always around a Wifi site.

I've  been kinda/sorta messing around with it for the past 2 days, just  playing around, just to see if maybe, I could make it work . . . and it  just started working!!! [IMG]http://ubuntugeek.com/forum/Smileys/default/cheesy.gif[/IMG]

---

### Post by beastrace91 on 2010-01-23
> **vrkalak said:**
> Apparently, there has been lots of problems on  getting this device to work in Ubuntu.

Who ever has had issue(s) getting the A600 working under Ubuntu at this point must have issues using Google/following instructions. Searching **cricket ubuntu** yields hits to this thread, ubuntugeek, and my personal blog (the latter of two are copies of the instructions found here). It is painless since I made the .deb installers for modeswitch to get the A600 working... I've done it on at least five different computers all running various forms of Linux (ranging from Ubuntu 8.10, Ubuntu 9.10, to Fedora, to Sabayon - 32bit and 64bit) and it works with out a hitch if you follow the instructions I detail here... Both for the modem and for using it as a mass-storage device via a microSD card.

Regards,
~Jeff

---

### Post by AlphaLexman on 2010-01-26
Thanks beastrace.

Just got a new Pantech UM185 yesterday and got it working in Karmic.

---

### Post by beastrace91 on 2010-01-26
> **AlphaLexman said:**
> Thanks beastrace.

Just got a new Pantech UM185 yesterday and got it working in Karmic.

Very good, glad to hear it is working for the other modem model as I've never owned one.

~Jeff

---

### Post by foresthill on 2010-01-31
What exactly does the Deb file do? I installed it in Kubuntu with no apparent effect at all. I have used to USB_Modeswitch program in Ubuntu 9.10, Suse 11.1 and 11.2 (Gnome and KDE) but Kubuntu seems to be giving me the most trouble, for some odd reason. The USB_Modeswitch program seems to work by itself when it wants to, for the most part, so I'm curious as to what exactly the Deb file does.

I have found that the Network Manager in Kubuntu is absolutely worthless at detecting and connecting with my Cricket A600 modem. I have to use wvdial, which is not really all that terrible (it beats no internet at all). But it was a bear to get running initially, since the A600 is my only internet connection. 

Can anyone recommend any updates or tweaks to get the A600 running a little better in Kubuntu?

---

### Post by beastrace91 on 2010-01-31
All this .deb file does is install modeswitch with *just* the code for flipping the A600 (instead of all modems). I compiled it before modeswitch was in the repos.

Regarding the network manager: ```
sudo apt-get install networkmanager-gnome
```

And then run **killall knetworkmanager && nm-applet**

The KDE network manager is crap compared to the Gnome one - just use it instead.

Regards,
~Jeff

---

### Post by foresthill on 2010-01-31
So if I install the Deb file, I won't need to install the USB Modeswitch (theoretically). I worry about installing two apps that do the same thing for fear that they would be tripping over each other.

I noticed that there is a newer version of USB Modeswitch in the Debian repo, I think it's version 1.0 or something close to that. I actually installed it, but when I run the command "USB_Modeswitch" it runs the older version instead of the newer version. I'm unsure of how to uninstall the old version.

So as of now, I have the both the USB Modeswitch 0.9.7 tarball version, and the 1.0 Deb version installed. I'm able to flip the modem, but I guess I ought to get rid of one of the versions, if I can figure out how.

Thanks for the tip on the Gnome Network Manager. That KDE one is next to worthless when trying to use these modems. Does the "kill all" command keep the KDE NM from starting, or do I still have to uninstall it?

Thanks for all the work on this, these modems can be difficult as hell to get running sometimes. More difficult than a 56 k modem, due to all the USB issues you have to figure out. I would still be fighting that modem if i had not found this thread. Or using Windows (yuck) just so I could get on the internet.

---

### Post by foresthill on 2010-01-31
The command to download Gnome network manager did not work in Kubuntu, but I was able to download it through the software manager program. I also uninstalled KDE network manager. 

The result was that Gnome network manager would not start and there was no menu entry for it. So at the moment I have no network manager at all, which is fine with me since KDE network manger was not doing a damned thing anyway. 

I currently have the laptop disassembled, so I can't really mess with it. I think it's probably a matter of just adding the correct repos, unless Gnome network manager flat out will not run in Kubuntu, which is another possibility.

I hope this Network manager mess is straightened out in Linux eventually, everybody seems to have problems of some sort with the program in its various incarnations.

---

### Post by beastrace91 on 2010-01-31
Gnome network manager runs fine in KDE - Kubuntu is just Ubuntu running KDE instead of Gnome after all. As for my .deb package - it installs a slightly modded version of usb_modeswitch version 0.9.7

As for loading Gnome network manager under KDE - just run **nm-applet** in terminal (or in lancelot launcher)

Regards,
~Jeff

---

### Post by foresthill on 2010-02-01
OK, everything is working for me now in Kubuntu. The flipping process sometimes takes 4-5 tries, but I can always eventually get it to work, and the Gnome Network manager actually dials out for me, unlike the KDE Network Manager.

---

### Post by beastrace91 on 2010-02-01
Try increasing the wait time in the flipflop.sh and also I've found actually mounting the A600 drive that pops up before flipping it helps it to flip correctly if a system is having issues.

Regards,
~Jeff

---

### Post by TeckniX on 2010-03-19
I've installed all the .deb file modified the .sh so that the path to the usb_modswitch is correct. 
The script returns the correct info regarding the driver being loaded correctly and that to run lsusb to check for any changes.
The UM185c modem never shows up in the network settings (nm-applet).
I'm running Ubuntu 8.04 and have updated the network-manager and network-manager-gnome to the latest package available in the repo.

Any idea why the 3G card isn't showing up?

Thanks for any help

---

### Post by beastrace91 on 2010-03-19
Howdy There,

Are you using the newest network manager or the newest network manager for 8.04? As I stated in the first post, these scripts where never tested with *buntu versions older than 8.10, meaning maybe the older network manager in 8.04 does not support the cricket device (because the 185 is even newer than the A600 I believe.)

Could you try booting from an Ubuntu 9.xx CD and see if the install instructions work from there?

~Jeff

---

### Post by coveybrit on 2010-03-27
I have two laptops an HP with AMD64 dual core and a Toshiba AMD64 Neo single core processor using 9.10 with latest updates.  I now have both accessing the internet with the Pantech UM185c (Cricket).
The steps I used are as follows:
1. added usb-modeswitch with Synaptic
2. downloaded cricketum185.sh to Desktop
3. rebooted the system
4. turn off the wireless using network manager
5. insert UM185c - disregard and close error message
6. cd Desktop then run sudo ./cricketum185.sh
7. right click on network icon (Network Manager)
8. click on edit connetions
9. click on mobil broadband
10. click on add
11. mine shows Pantech Pantech USB Modem click forward
12. highlight your country mine is US click forward
13. highlight Cricket Communications  click on forward
14. I did not change any entries on the Mobile Broadband, PPP settings, IPV4, I just clicked apply
15. a few seconds later I was connected
16. I have to run step #6 each time I remove the 185, but it seems to work fine once that is done.  I just left click on Network Manager and click on mobile broadband - connect

I hope this helps if you are having difficulty connecting.

---

### Post by alexfish on 2010-03-28
Hi

Has anyone thought about getting the script to work at Boot Time

[http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian)

---

### Post by beastrace91 on 2010-03-28
> **alexfish said:**
> Hi

Has anyone thought about getting the script to work at Boot Time

[http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian)

Thats really only useful if your Cricket is connected at boot time. Realistically a udev rule would work better as this would run at the time the device is connected but as stated in the first post I never got this successfully working and as of Gnome 2.28 the network manager flips the modem automatically. 

~Jeff

---

### Post by ImaniUbu on 2010-03-30
I just did a clean install of Ubuntu 9.10 on my computer it's a Dell Optiplex 240...I am new to Ubuntu...so how would I change directories in the terminal so I can use the install command...thank you...

---

### Post by beastrace91 on 2010-03-30
> **ImaniUbu said:**
> I just did a clean install of Ubuntu 9.10 on my computer it's a Dell Optiplex 240...I am new to Ubuntu...so how would I change directories in the terminal so I can use the install command...thank you...

You use the **cd** command. For example to change to your desktop run: ```
cd ~/Desktop
```

Regards,
~Jeff

---

### Post by V_S_R on 2010-04-05
I have the Cricket UM185C Broadband model.
I installed it the way as it said, but when I take out an put the usb modem back in later I get this:

> **UNABLE TO MOUNT CRICKET**
Error mounting: mount exited with exit code 32: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have to run cricket_flip_i386.deb & cricketum185c.sh everytime I connect the modem to get it to work. Anyone here know what I am doing wrong?

---

### Post by beastrace91 on 2010-04-06
> **V_S_R said:**
> I have to run cricket_flip_i386.deb & cricketum185c.sh everytime I connect the modem to get it to work. Anyone here know what I am doing wrong?

What Ubuntu version?

~Jeff

---

### Post by V_S_R on 2010-04-07
> **beastrace91 said:**
> What Ubuntu version?

~Jeff
Ubuntu Desktop 9.10 (32-bit)

I thought I had to run both cricket_flip_i386.deb & cricketum185c.sh, I only have to run cricketum185c.sh to get it back to work.

Error when plugging the USB Modem
> **UNABLE TO MOUNT CRICKET**
Error mounting: mount exited with exit code 32: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

is their a fix so I don't have to keep on running cricketum185c.sh when I plug in the Cricket Modem to work?

---

### Post by beastrace91 on 2010-04-07
> **V_S_R said:**
> is their a fix so I don't have to keep on running cricketum185c.sh when I plug in the Cricket Modem to work?

You could setup a udev rule for when the device is connected - but this is a bit beyond the scope of this thread here (which is just for getting the modem to connect ;) )

Wish I could be of more help but I've never actually owned a 185 modem and I actually don't even have my A600 any longer (traded it for a cell phone that can tether)

Regards,
~Jeff

---

### Post by mjmcomputer on 2010-04-09
This worked for me to get the UM185C working for a client. 

[LIST=1]
[*]I installed the 32 bit deb, cricket_flip_i386.deb.
[*]Ran the file cricketum185c.sh
[*]Opened System/Preferences/Network Connections
[*]Click on the "Mobile Broadband" tab
[*]Click "Add" and added the PANTECH USB MODEM
[*]Chose Country and Carrier
[*]Left the Number, Username & Password as they were
[*]Checked "Connect automatically"
[/LIST]
This created "Cricket Communications connection 1" on the Mobile Broadband tab. I can then connect or disconnect through the Network Manager tray applet. When I shutdown or restart the computer or unplug the device I have to run cricketum185c.sh again after the failure to mount error. To make this simple I created a Launcher on the Desktop that points to the .sh file the client then enters his password and it connects automatically. Would be nice if it worked right at startup or plug-n-play but this way you can control when you are connected or disconnected.
Thanks for working this out Jeff you rock.:guitar:

---

### Post by pdc on 2010-04-09
well done mjmcomputer

if you spelt out exactly what you did, many would be grateful to you;

if you could spell out each detailed step, the beginners following in your wake would likely succeed

---

### Post by vrkalak on 2010-04-29
_For everyones info_:

The new Ubuntu Lucid 10.04 already has the "usb_modeswitch" application, pre-installed by default.

I have both the A600 and just got the new UM-185C ... works like a charm. :)
Both of my USB Modems work in Ubuntu, Xubuntu, LinuxMint, Debian Squeeze and Crunchbang ... with absolutely 'no problems'

---

### Post by danrael on 2010-04-29
> **vrkalak said:**
> _For everyones info_:

The new Ubuntu Lucid 10.04 already has the "usb_modeswitch" application, pre-installed by default.

I have both the A600 and just got the new UM-185C ... works like a charm. :)
Both of my USB Modems work in Ubuntu, Xubuntu, LinuxMint, Debian Squeeze and Crunchbang ... with absolutely 'no problems'


I am running Ubuntu 9.10 disguised as Lin-X 1.1 (looks/feels like Mac Leopard), and have no luck with the two files Jeff has provided to install the Cricket UM185c USB modem.   

Is it possible to upgrade my version 9.10 Ubuntu OS to 10.04 without reformatting the partition? 

If that is possible, then what is the exact procedure for getting the Cricket modem to work?

Thanks

---

### Post by thedandalion on 2010-05-01
> **danrael said:**
> .... If that is possible, then what is the exact procedure for getting the Cricket modem to work?

Thanks

[quote=vrkalak]The new Ubuntu Lucid 10.04 already has the "usb_modeswitch" application, pre-installed by default.[/quote]  I did a clean install of Lucid 10.04 (64bit) and would like to know what the exact procedures to get the cricket a600 modem to work.  I use to have the um100 but traded it out for the a600 since it seemed like people have had more luck with it than with the um100.

---

### Post by danrael on 2010-05-01
> **vrkalak said:**
> _For everyones info_:

The new Ubuntu Lucid 10.04 already has the "usb_modeswitch" application, pre-installed by default.

I have both the A600 and just got the new UM-185C ... works like a charm. :)
Both of my USB Modems work in Ubuntu, Xubuntu, LinuxMint, Debian Squeeze and Crunchbang ... with absolutely 'no problems'

I have now formatted my Lin-X (Ubuntu 9.10) partition and also performed a fresh installation of Ubuntu 10.04.  With the Cricket UM185c plugged in (light is ON), it shows up as 'CD Drive - Cricket' device icon in the 'Computer' window, but when clicked, I receive a message that:  Block device /dev/sr1/ is 'read only' and 'write protected' and cannot be mounted.  

'Cricket Communications' shows up as an embedded choice in the Network Manager under 'Mobile Broadband', but when I follow through with the installation, I get no detection of the device nor of any networks.  

Do I need to install any files beforehand?  I thought Ubuntu 10.04 had them already embedded.

One note:  I do have Windows installed on the same computer in a dual-boot config, and Cricket is already installed there, but I am in a location where I cannot get a Cricket network detection (I am working on this for a friend who lives elsewhere).  Could this be the entire source of the problem in Ubuntu?

Can you run the rest of us through a stepwise procedure to get the Cricket modems working as you did?  Much appreciated!

---

### Post by pdc on 2010-05-02
is post #1 of this thread of any use to you?

---

### Post by danrael on 2010-05-02
> **pdc said:**
> is post #1 of this thread of any use to you?

No.   I can't get it to work.  That is why I fresh-installed ver. 10.04, as it was supposed to have the files already installed, at least according to a recent post here.  Supposedly, the command line procedures are not required in 10.04.

---

### Post by beastrace91 on 2010-05-02
> **danrael said:**
> the command line procedures are not required in 10.04.

Not true. What the newer poster simply meant is that usb_modeswitch is included in the repositories now. Meaning you do not have to install my custom .deb packages for just the A600 as my changes have been added to the main package.

I no longer have my A600 (upgraded to tethering my N900 instead thehehe) but anyways I am decently sure you need to manually "flip" the A600 from CLI the first time you hook it up. If it is not automatically appearing in network manager as you are saying.

Regards,
~Jeff

---

### Post by thedandalion on 2010-05-02
> **beastrace91 said:**
> Not true. What the newer poster simply meant is that usb_modeswitch is included in the repositories now. Meaning you do not have to install my custom .deb packages for just the A600 as my changes have been added to the main package.

I no longer have my A600 (upgraded to tethering my N900 instead thehehe) **but anyways I am decently sure you need to manually "flip" the A600 from CLI the first time you hook it up. **If it is not automatically appearing in network manager as you are saying.

Regards,
~Jeff

Ok... I am extremely new at this and have been trying to get cricket to work on my system for a few months (I had to walk away or else my computer would of ended up in the neighbors yard)  I did a fresh install of 10.04 in hoping that it would help and swapped out my modem for the A600 since it seems that people have had more luck with it.  

I did the first steps in the beginning of the thread and it detected it once and I was able to connect... but I haven't been able to get it to detect it since.  So I am thinking that I did something wrong in the beginning.  

I could really use some help... I will even make you some rice crispy treats!!  Because without being able to go on the internet my computer is just a big cat warmer!

---

### Post by beastrace91 on 2010-05-02
> **thedandalion said:**
> but I haven't been able to get it to detect it since.

When you got it to connect the first time did you do so by running the flipflop.sh? If so try running this file again next time you attach the modem - I know this was not necessary in 9.10 but maybe this has changed in 10.04. As I said, I no longer have the device so I cannot confirm this.

~Jeff

---

### Post by danrael on 2010-05-02
> **beastrace91 said:**
> Not true. What the newer poster simply meant is that usb_modeswitch is included in the repositories now. Meaning you do not have to install my custom .deb packages for just the A600 as my changes have been added to the main package.

I no longer have my A600 (upgraded to tethering my N900 instead thehehe) but anyways I am decently sure you need to manually "flip" the A600 from CLI the first time you hook it up. If it is not automatically appearing in network manager as you are saying.

Regards,
~Jeff
Thanks, Jeff.

I am working with the UM185c unit, and am not in a location where I have a signal. 

Here is what I have done so far:

> Clean installation of Ubuntu 10.04 from disk - check
> Downloaded/installed **[COLOR="Indigo"]usb_modeswitch[/COLOR]** from Synaptic - check
> Reboot into Windows w/Cricket modem plugged in - check
> Windows sees the modem and starts its network manager - check
> Reboot into Ubuntu w/Cricket modem plugged in - check
> Cricket icon shows up in 'Computer' as a CD-ROM icon - check
> Set up Cricket Communications in Network Manager - check
> Rebooted. Now Network Manager shows the following as a choice:

[B][COLOR="Indigo"]Mobile Broadband 
disconnected
Available
Cricket Communications connection 1[/COLOR][/B]:P

When I pass my cursor over the 'Cricket Communications' text, it gets highlighted. I click on it and the Network Manager begins to animate its icon (flowing radio waves upwards). :D 

This means it is attempting a connection, I hope?

After about a minute, it stops and a message appears:

**[COLOR="Indigo"]'Network disconnected'[/COLOR]**

So far, I have not used the command line.

Are there any more files I need to install, either via of Synaptic or via Terminal?

Please advise. Thanks in advance.

Dan

---

### Post by danrael on 2010-05-02
.

---

### Post by thedandalion on 2010-05-03
> **beastrace91 said:**
> When you got it to connect the first time did you do so by running the flipflop.sh? If so try running this file again next time you attach the modem - I know this was not necessary in 9.10 but maybe this has changed in 10.04. As I said, I no longer have the device so I cannot confirm this.

~Jeff
Yes, I ran the flipflop.sh file again and it still didnt activate it.

---

### Post by beastrace91 on 2010-05-03
@danrael Yes, it appears as though it is indeed trying to connect. Not sure why it would be failing out on you like that :-/ - I've never had a UM185c unit to play with.

@thedandalion What is the output in terminal when you run the flipflop.sh

Regards,
~Jeff

---

### Post by thedandalion on 2010-05-03
> **beastrace91 said:**
> 

@thedandalion What is the output in terminal when you run the flipflop.sh

Regards,
~Jeff

This is what I get... the first time it 'turned it on' but now it just blinks at me (mockingly) 
[ATTACH]155326[/ATTACH]

---

### Post by beastrace91 on 2010-05-03
@thedandalion When the modem is plugged in is it detected as a CD drive?

~Jeff

---

### Post by danrael on 2010-05-03
> **beastrace91 said:**
> @danrael Yes, it appears as though it is indeed trying to connect. Not sure why it would be failing out on you like that :-/ 

Regards,
~Jeff

As I explained, I am working on someone else's computer, and I do not have a Cricket signal here at my location.  He does where he lives 50 miles away.   So it appears that Network Manager sees the modem OK and tries to connect to a non-existing, but properly configured network.  After about a minute, it stops and renders a messages that the Network is disconnected.  

Besides the **usb_modeswitch file**, are there any other files that I might need to install?

Thanks

Dan

---

### Post by beastrace91 on 2010-05-03
> **danrael said:**
> Besides the **usb_modeswitch file**, are there any other files that I might need to install?

Thanks

Dan

Not that I'm aware of, are you using the um185c file I provide?

~Jeff

---

### Post by danrael on 2010-05-04
> **beastrace91 said:**
> Not that I'm aware of, are you using the um185c file I provide?

~Jeff


I downloaded and installed the one provided in Synaptics Package Manager in the new Ubuntu 10.04 distro

---

### Post by thedandalion on 2010-05-05
> **beastrace91 said:**
> @thedandalion When the modem is plugged in is it detected as a CD drive?

~Jeff

I am pretty sure because I get an icon on my desktop that says "A600CD" when I run the flipflop it disappears...

---

### Post by beastrace91 on 2010-05-05
> **thedandalion said:**
> I am pretty sure because I get an icon on my desktop that says "A600CD" when I run the flipflop it disappears...

And it still doesn't work afterwards? Please post the terminal output from running the flipflop.sh (copy and paste text - not screen shot please)

~Jeff

---

### Post by sophieand killer on 2010-05-06
> **beastrace91 said:**
> As your issue does not pertain to making Ubuntu see the device (which is the point of this guide) maybe posting a new topic describing your issue would be a better idea and would keep this one on topic.
 
~Jeff
 Had to go thru heck to post this. So I got the Cricket modem (the expensive one $40 a month) and after 2 days could no longer get online. Back to the full service store today. They uninstalled it and reinstalled it and now it works. Only info I can give you is I have 2 new computers both with Windows 7, I don't trust new windows stuff but that's my problem. So now it works. Their full service center is an hour away when you consider traffic so all I want to do is pass this info on. I could have done that if I had found the info online, I'm 62 or is it 63 anyhow I don't need to sit in a chair for an hour at a service center for my turn so I hope this helps someone. Where's the face of an old lady??? I want to add.

---

### Post by thedandalion on 2010-05-07
> **beastrace91 said:**
> And it still doesn't work afterwards? Please post the terminal output from running the flipflop.sh (copy and paste text - not screen shot please)

~Jeff


This is what I get

```
    
Looking for target devices ...
Found devices in target mode or class (1)
Looking for default devices ...
Found default devices (1)
Found a default device NOT in target class mode
Prepare switching, accessing device 003 on bus 004 ...
Looking for active driver ...
OK, driver found ("usb-storage")
```

---

### Post by foresthill on 2010-05-10
> **danrael said:**
> Thanks, Jeff.

I am working with the UM185c unit, and am not in a location where I have a signal. 

Here is what I have done so far:

> Clean installation of Ubuntu 10.04 from disk - check
> Downloaded/installed **[COLOR="Indigo"]usb_modeswitch[/COLOR]** from Synaptic - check
> Reboot into Windows w/Cricket modem plugged in - check
> Windows sees the modem and starts its network manager - check
> Reboot into Ubuntu w/Cricket modem plugged in - check
> Cricket icon shows up in 'Computer' as a CD-ROM icon - check
> Set up Cricket Communications in Network Manager - check
> Rebooted. Now Network Manager shows the following as a choice:

[B][COLOR="Indigo"]Mobile Broadband 
disconnected
Available
Cricket Communications connection 1[/COLOR][/B]:P

When I pass my cursor over the 'Cricket Communications' text, it gets highlighted. I click on it and the Network Manager begins to animate its icon (flowing radio waves upwards). :D 

This means it is attempting a connection, I hope?

After about a minute, it stops and a message appears:

**[COLOR="Indigo"]'Network disconnected'[/COLOR]**

So far, I have not used the command line.

Are there any more files I need to install, either via of Synaptic or via Terminal?

Please advise. Thanks in advance.

Dan

I run a Cricket A600. I just installed 10.4 on my laptop.

I was dismayed to see that 10.4 is not properly "flipping" the unit like 9.10 did. 

One temporary solution I found was to boot up in 9.10 (I run a dual boot system) let the modem flip there, and then reboot into 10.4, at which point the modem would be recognized and i could set it up under network connections. I suppose you could also flip the unit in Windows and reboot, that should work as well.

I got online eventually and ran the update manager, hoping a fix would be there, but no such luck. So I guess the next step is to try to flip the unit manually with USB_modeswitch. :(

Specific to the poster above, I was having a similar problem about a week ago (this was while running 9.10). The modem would take an eternity to connect, and eventually get hung up on by the Cricket server. About one out of ten attempts I could connect, but the speed was less than 1 kb per second, and would quickly stall and I would get hung up on. This lasted for about a week.

What I did to fix the problem was go into Windows and connect with the modem for 10-15 minutes. After connecting in Windows and then going back to Ubuntu, the connection problems disappeared. Now this is complete speculation on my part, or possibly a coincidence, but I suspect that there may have been some sort of firmware upgrade that installed itself when I was in Windows, one that required the Cricket software to install. I have had no problems since.

---

### Post by foresthill on 2010-05-10
The person who stated that USB_modeswitch is already installed in 10.4 is incorrect. You will need to find some way to get on the net and install it from the Synaptics package manager. The Cricket A600 modem should flip automatically once you do that.

Also, I just had the same problem of being unable to connect with my modem after it was detected. It would try to dial out and the connection would terminate.

So I booted into Windows and started the Cricket software. It turns out there was an update, which I installed, and now i can connect in Ubuntu once again. So my guess is that Cricket is keeping modems from connecting to its network until the update is installed.

---

### Post by drakect on 2010-05-19
ok guys i cant seem to find the similar problem in this thread but maybe you have a clue why when  did the flip and run the script it added the um device but when i try to configure it or connect it asks me for a pin number 

any ideas

---

### Post by beastrace91 on 2010-05-20
> **drakect said:**
> ok guys i cant seem to find the similar problem in this thread but maybe you have a clue why when  did the flip and run the script it added the um device but when i try to configure it or connect it asks me for a pin number 

any ideas

Does it allow you to leave it blank?

~Jeff

---

### Post by drakect on 2010-05-22
nope what aver i type in it says make sure your sim card is in :/

---

### Post by foresthill on 2010-05-25
Been having a problem in 10.4 Lucid, where if my modem times out, it will disconnect. Which is fine, but once I get disconnected, my modem is unable to reconnect without a reboot.

What happens when I try to reconnect is that the modem will attempt to dial out and the connection fails for some unknown reason. And since there is no feedback when using Network Manager as to why the connection failed, I have no idea what's going wrong. 9.10 does not do this.

What I did to get around this was install KPPP through Synaptics. I have no problem reconnecting when I use this program, plus I get feedback when I do connect.

Anyone else having this problem?

---

### Post by Callmesweettea on 2010-05-29
I have been reading the forums for hours now and I'm tired. I have just a few questions. 
I have a cricket Broadband Modem A600 etc, etc. Now I really want to Install Ubuntu 10.04 onto my laptop. I have burned it do disc already. Now I have been trying to get this thing to work with no luck. Does it make a difference that I am using Ubuntu from boot disc? I downloaded cricket_ mode_switch.tar.gz but not sure where to extract it  to. And do I extract it in Windows or Ubuntu? I only have Internet when using windows so I am switching back and forth by reboot because I am a super noob. I downloaded the file in windows and transfered it using the cricket uSb thingy. tried to extract it to desktop then open the terminal and type in whatever it was i was told to in the tutorial which didnt work, got some error Messages again. Nothing worked. and my windows cant even read the file. its jsut like blank. Anyways I post more in a few. Have to go back and try again. 

Any help would be appreciated as I want to get things sorted so I can use Ubuntu for good but first Internet is a MuSt :D

---

### Post by pdc on 2010-05-30
> Does it make a difference that I am using Ubuntu from boot disc?

....... yes because you need to save some changes; (you can't do that to a burnt CD ...)

> I downloaded cricket_ mode_switch.tar.gz but not sure where to extract it to.

that's where you need a permanent system .

Ubuntu has an ability to burn a copy to a USB stick; and it will save changes to that, so you can try the system; but not install to a hard drive till you need;

if you boot ubuntu; top line: System; Administration: half-way down: create a usb stick (or some such title); you need the .iso file on one stick as the input and a second USB stick to burn it to; then the second USB stick will boot ubuntu and remember changes you have made to it; if the boot system on your system is changed so a removable disk boots first

if you feel like it, you can "dual boot" where you shrink the size of your windows install, and install ubuntu on the remaining part 

have you read the very first entry?

[http://ubuntuforums.org/showthread.php?t=1146110](http://ubuntuforums.org/showthread.php?t=1146110)

it talks you through how to get this device working; it seems to give some troubles to folks

---

### Post by CBR_Rob on 2010-06-16
Ok I am not sure what I am doing wrong here. I installed the mode switcher and downloaded the cricketum185c.sh file. When I try to run the file in terminal I get a command not found error. I did notice that when I downloaded the .sh file it is saved as cricketum185c.download. I've tried renaming it and also tried the filename in terminal with the .download.

I am fairly new to Linux and am using Linux Mint 8 32bit with the Pantech modem. This modem does work in Windows and is activated. I have included a screenshot of the error.

---

### Post by beastrace91 on 2010-06-17
Rename your **cricketum185c.download** to **cricketum185c.sh**

For some reason when Chrome(ium) downloads .sh files it puts the file extension as .download instead of .sh

~Jeff

---

### Post by CBR_Rob on 2010-06-17
I have tried renaming the file and even opened it with gedit and copied out the contents and saved it with the .sh extension but still get the same error.

---

### Post by beastrace91 on 2010-06-17
That error means the file you are looking for is not in the directory you are trying to run it from. Use the **ls** command to display the contents of the directory you are in to ensure the .sh file is where you think it is.

~Jeff

---

### Post by CBR_Rob on 2010-06-17
The file is where I think it is. I am still getting the same error. I copied the command right from the 1st post and tried it a couple different ways since I am not sure what the ./ and / add to the command. I have attached a screen shot of the error again.

---

### Post by beastrace91 on 2010-06-18
> **beastrace91 said:**
> (Please note you need to first make this file executable by running ```
chmod +x cricketum185c.sh
```

Make sure you did that. Judging by the color of your .sh file in your screen shot it does not appear to be executable.

~Jeff

---

### Post by CBR_Rob on 2010-06-19
Thanks for the help. For some reason I was reading the commands backwards even though it clearly says to make it executable first. I am actually posting this using my cricket modem.

---

### Post by beastrace91 on 2010-06-19
Well glad you got it working at any rate :)

~Jeff

---

### Post by trifutec on 2010-07-14
I followed the directions for making a cricked device work with ubuntu, but I didn't see it popup in the network manager. I'm wondering if this method works on Ubuntu 8.04.

Does anyone know, I did see the cricket device light up and show as if it were receiving signal, but I'm stuck at that point. I don't use linux much so detailed explanations and answers would be greatly appreciated.

Thanks for the post, a great help!

---

### Post by beastrace91 on 2010-07-14
You know, I have never used the modem with anything older than 8.10 - so I am not sure if the network manager in 8.04 supports the modem.

~Jeff

---

### Post by trifutec on 2010-07-15
it probably doesn't. i will upgrade and try it again

thanks

---

### Post by azziam on 2010-07-30
I hope I can slide by here without reading all 22 pages of this thread.  [Yes, I read a lot of them.] I really thought I had it made when I got a few lines into the beginning post where it said: "Wait a few moments and poof! Your 3g modem should now be appearing in your network manager."  

I'm trying to get the A600 to work in Ubuntu Studio 10.04 and until it does I have to reboot into PCLinuxOS where it works fine and I have a connection.  I downloaded the cricket_flip_amd64.deb and also the flipflop.sh.  I installed the .deb and executed the .sh which seems to do the same as if I just run usb_modeswitch in a terminal.  All I can get is a message that no target device is found and asking if it's plugged in?!  The obvious answer to that is, yes, it's plugged in and I'm using it now.  I've been back and forth till my fingers and my brain are tired and my eyeballs need a timeout.  Is there a known reason why this might happen?  The device surely is seen because it is showing up as a Cricket T-Flash drive.  So why isn't it flipping?  Any help is greatly appreciated.

---

### Post by azziam on 2010-07-30
Update -- I went back and tried it again to see if it would make a difference if I unplugged and replugged the device.  This time I saw the Cricket device shown as a CD and when I ran flipflop.sh in a terminal I saw that it seemed to flip the thing properly.  Then there was just the Cricket T-flash drive showing again.  lsusb showed the correct ID 1f28:0020.  

Still, Ubuntu Studio seems to have no way to configure a PPP connection in its "Network Tools".  I looked in usr/sbin and found pppconfig but couldn't get it to run.  It just seems like something is left out of this OS distro.

I'm still hoping for some help to get the rest of the way there.

--
  azziam

---

### Post by beastrace91 on 2010-07-30
> **azziam said:**
> Still, Ubuntu Studio seems to have no way to configure a PPP connection in its "Network Tools".  I looked in usr/sbin and found pppconfig but couldn't get it to run.  It just seems like something is left out of this OS distro.

If you can get a wired connection on it just install Gnome network manager on it to dial up the modem.

~Jeff

---

### Post by azziam on 2010-07-31
> **beastrace91 said:**
> If you can get a wired connection on it just install Gnome network manager on it to dial up the modem.

~Jeff

This A600 is the only way out of here!  I used to keep a free Netzero account for emergencies but no longer keep a land line.

In PCLOS I use Gnome PPP and it works fine.  From what I've been reading here, network manager does everything automagically without entering numbers, password, or anything??  I did finally get pppconfig to run in a terminal and I filled in all the blanks but it doesn't make it show up anywhere because it has no front end.  Also, I wasn't sure if Cricket uses PAP, CHAT, or CHAP.  Anyway, all my settings I entered were saved in a couple files I'll probly have no use for.  

Just to be thorough, I've done all the manual typing of your modeswitch commands including the 2nd one ending in -R 1.  I can't copy and paste the output of my attempts but it has read the same as the successful ones, verified  by lsusb.  I really was expecting it to show up in Network Tools but all that shows is Loopback Interface (lo), Ethernet Interface 0 (eth0), and 1 (eth1).  There was also a (wlan0) but I unplugged it because it won't connect to anything from here.

Is there a separate Ubuntu Studio forum I should be asking in or is it all in this one?

[Almost forgot to say thanks for all the help you've given for the A600!  Maybe I should think about downloading and installing Network Manager by other means, if it can be got.]

--
  azziam

---

### Post by beastrace91 on 2010-07-31
Take a look at this guide for installing [URL="http://jeffhoogland.blogspot.com/2010/06/howto-installing-ubuntu-packages.html"]Ubuntu Packages Offline
[/URL]

:)

~Jeff

---

### Post by azziam on 2010-08-02
> **beastrace91 said:**
> Take a look at this guide for installing [URL="http://jeffhoogland.blogspot.com/2010/06/howto-installing-ubuntu-packages.html"]Ubuntu Packages Offline
[/URL]

:)

~Jeff

Thanks, I'm going to try this.  I'll need just a bit more direction, though.  So far, it looks to me like the lines starting with 'mv' are a separate command, correct?  Is there a destination that needs to be added to this?  It's not quite clear to me yet.  I ran the first line and got:

"Saving to: &#8220;Release&#8221;

100%[======================================>] 95          --.-K/s   in 0s      

2010-08-02 10:50:31 (5.90 MB/s) - &#8220;Release&#8221; saved [95/95]"

---

### Post by beastrace91 on 2010-08-02
The mv commands are simply to rename the files you are wgetting to the proper name they need to be. Just follow the guide step by step and you should be fine :)

~Jeff

---

### Post by azziam on 2010-08-02
Never mind.  I had to take a look at the syntax and add a destination for the mv commands.  When I get time to reboot I'll be giving the install a try.

[I sent this before refreshing to see your post above.  Again, I needed a destination directory for the 5 files.  Also I figured out to ignore the Packages text files that wanted to overwrite each other although I saved them anyway.]

--
  azziam

---

### Post by azziam on 2010-08-03
Something isn't working, so far.  Since I am not going back and forth between machines but am in a dual boot, I'm not using a flash drive.  I did all the wget commands and put the 5 files in a directory on a separate FAT32 partition I use for transferring data between OS'es.  I also copied the apt-get commands to a text file there.  

Then I booted into Ubuntu Studio, opened Nautilus as root and copied the 5 files into var/lib/apt/lists.  Then I tried: apt-get -qq --print-uris install networkmanager > apt_list.  I just get an error message that the package networkmanager can't be found.  I also tried with network_manager and also tried to get modemmanager which was also listed.  Any of these gave the same error of 'package not found'.  

What am I missing?

--
  azziam

---

### Post by beastrace91 on 2010-08-03
The package you are looking for is **network-manager-gnome**

~Jeff

---

### Post by desnaike on 2010-08-05
Hello everyone I took the easy way had the clerk at the cricket store activate the modem for me came home after stopping at starbucks/or any free wifi hotspot and installed usb-modeswitch,usb-modeswitch-data with synaptic and since I also have a desktop at home  I downloaded the usb-moadswitch deb file to install on it. worked like charm.

---

### Post by complearning123 on 2010-10-01
> **michael.patterson14 said:**
> Hey guys i found an interesting thing out today. when you insert the modem and it tells you it cant mount it, if you go to the places [COLOR=Black][COLOR=#CC0000] ***directory***[/COLOR][****]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=Wj9&ei=URsPS4T7D4u3ngfR1rTMAw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBsQBSgA&q=directory&spell=1")[/COLOR] and see ware it shows the cricket as a cd and then eject it the system will automatically recognize the modem and you should be able to connect to the net after that. But you have to do it every time you boot up. I'm using the UM185C on ubuntu 9.10, so far it has worked for both the desktop and netbook remix.
thanks michael i ejected it and then it recognized it as a modem and connected .  I tried Jeff's instructions but he kept putting the cart before the horse....saying that you have to enter this command but oh, wait you should have already made this an exec by this command....confusing!  especially for newbies to Linux like myself.  Thanks for the tip on the eject/cd thingy.

complearning123

---

### Post by beastrace91 on 2010-10-01
> **complearning123 said:**
>  he kept putting the cart before the horse

You know, thousands of others have used those instructions without issue. They are clearly laid out and as dumbed down as possible :confused:

If you are capable of reading and following instructions it really works pretty easily >.<

~Jeff

---

### Post by Sonic132 on 2010-10-29
Ok I'm running Kubuntu 10.04 and among other problems with video glitches and the like. I'm having trouble installing the Cal-comp A600 modem. I followed all the directions on the first post and it works somewhat. It lights up the signal bar lights and shows the signal strength. But it disappears from the connected devices list. Where it showed it as an optical drive.
I ran *lsusb* and it showed an entry that I narrowed down to having to be the modem. But it wasn't labelled as such.
Also...lastly, Mobile Broadband and Wireless is greyed out under *Configure - KDE Control Module*. So I'm not sure what to do after the somewhat successful *flipflop*. I've been on IRC almost all day and no one there can help me. I'd really love to see this issue resolved very soon.
Thanks in advance.

---

### Post by beastrace91 on 2010-10-29
Did you get it sorted after we talked on AIM last night Sonic? You need to install the gnome network manager and use it to connect to the modem.

Regards,
~Jeff

---

### Post by Sonic132 on 2010-10-29
> **beastrace91 said:**
> Did you get it sorted after we talked on AIM last night Sonic? You need to install the gnome network manager and use it to connect to the modem.

Regards,
~Jeff

No...apparently I need to download it since it doesn't appear to be on the Kubuntu CD. Any idea where I could get a deb for Gnome network manager and the keyring (I need that too right?) ?
At least that way I could put it on a thumbdrive or an external and move it over.

---

### Post by TGlo1488 on 2010-12-09
It took me a total of 5 min to using this method to post this reply using UBUNTU.

---

### Post by archie1941 on 2010-12-13
Congrats on the five min, been playing for two weeks, getting closer but no brass ring yet
See device in network manager
click on device and it tries to connect but msg comes up disconnected
I think I need to increase the sleep time from ten to twenty in the flip flop but so far haven't been able to find where it is with search.

I hope this gets it working.

archie@archie-desktop:~$ sudo /usr/sbin/usb_modeswitch
[sudo] password for archie: 
Usage: usb_modeswitch [-hvpVPmMrdHn] [-c filename]

 -h, --help                    this help
 -e, --version                 print version information and exit
 -v, --default-vendor NUM      vendor ID of original mode (mandatory)
 -p, --default-product NUM     product ID of original mode (mandatory)
 -V, --target-vendor NUM       target mode vendor ID (optional)
 -P, --target-product NUM      target mode product ID (optional)
 -C, --target-class NUM        target mode device class (optional)
 -m, --message-endpoint NUM    direct the message transfer there (optional)
 -M, --message-content <msg>   message to send (hex number as string)
 -2 <msg>, -3 <msg>            additional messages to send (-n recommended)
 -n, --need-response           read response to the message transfer (CSW)
 -r, --response-endpoint NUM   read response from there (optional)
 -d, --detach-only             detach the active driver, no further action
 -H, --huawei-mode             apply a special procedure
 -S, --sierra-mode             apply a special procedure
 -O, --sony-mode               apply a special procedure
 -G, --gct-mode                apply a special procedure
 -R, --reset-usb               reset the device after all other actions
 -Q, --quiet                   don't show progress or error messages
 -W, --verbose                 print all settings and debug output
 -D, --sysmode                 specific result and syslog message
 -s, --success NUM             check switching result after NUM secs
 -I, --no-inquire              do not get SCSI attributes (default on)

 -c, --config-file <filename>  load configuration from file

 -i, --interface NUM           select initial USB interface (default 0)
 -u, --configuration NUM       select USB configuration
 -a, --altsetting NUM          select alternative USB interface setting

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.4 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

archie@archie-desktop:~$ clear

archie@archie-desktop:~$ lsusb
Bus 008 Device 002: ID 04f3:0801 Elan Microelectronics Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 1f28:0020 Cal-Comp CDMA USB Modem A600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 007: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series
Bus 001 Device 006: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 03ee:6901 Mitsumi SmartDisk FDD
Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
archie@archie-desktop:~$ ls usb
ls: cannot access usb: No such file or directory
archie@archie-desktop:~$ lsusb
Bus 008 Device 002: ID 04f3:0801 Elan Microelectronics Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 007: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series
Bus 001 Device 006: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 03ee:6901 Mitsumi SmartDisk FDD
Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
archie@archie-desktop:~$ lsusb
Bus 008 Device 002: ID 04f3:0801 Elan Microelectronics Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 007: ID 1f28:0020 Cal-Comp CDMA USB Modem A600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 007: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series
Bus 001 Device 006: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 03ee:6901 Mitsumi SmartDisk FDD
Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
archie@archie-desktop:~$ sudo usb_modeswitch -v 0x1f28 -p 0x0020 r 1
[sudo] password for archie: 

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 007 on bus 006 ...
Error: message endpoint not given or found. Aborting.

archie@archie-desktop:~$ lsusb
Bus 008 Device 002: ID 04f3:0801 Elan Microelectronics Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 007: ID 1f28:0020 Cal-Comp CDMA USB Modem A600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 007: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series
Bus 001 Device 006: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 03ee:6901 Mitsumi SmartDisk FDD
Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
archie@archie-desktop:~$ 



this is the output with the devise pluged in

how and exactly what do I open, and how do I open it to change the time.

LOST IN LINUX! lol from an old fart

THOUGHTS

I believe the devise is switching
When it is plugged in I see it under connections
when I click on the connection I get a msg on screen (disconnected, with the sig symbol and a red x
My problem may be in the network settings

My other problem is that I haven't used cli since the VIV 20 days back in the 60s
I've forget the little I knew then

---

### Post by gdgtgrl on 2010-12-14
This worked perfectly for me with my UM185C and Ubuntu 10.04. Thanks!!!

---

### Post by archie1941 on 2010-12-16
**New Note**

Using the newest and updated
 unbuntu os  ubuntu 10-10
 plugged in A600     
comp says connected
 cannot surf web so computer isn't really connected 
See devise in manager
 rechecked everything a number of times
 archie@archie-desktop:
~$ sudo lsusb [sudo] password for archie
:  Bus 008 Device 002: ID 04f3:0801 Elan Microelectronics Corp
.  Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
**Bus 006 Device 011: ID 1f28:0020 Cal-Comp CDMA USB Modem A600**
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 008: ID 0781:5530 SanDisk Corp.
 Bus 001 Device 007: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series 
Bus 001 Device 006: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera 
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB 
Bus 001 Device 004: ID 03ee:6901 Mitsumi SmartDisk FDD
 Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
 Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 
Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub archie@archie-desktop:~$
 I am at my wits end on this 
[B]Yes! I've read all 24 pages of the post
 I know that your post has been dummied down 
I've tried the wvdial 
I've tried the gnome ppp 
I've reset the network connection 
I've rechecked the phone number--#777 
I've rechecked the user [EMAIL="name--6624206266@mycricket.com"]name--6624206266@mycricket.com[/EMAIL][/B] [B]
I've rechecked pasword--cricket [/B]

So if the thing is connected the question is to what?
 Is the connection internal to the computer only. 
If this is the case then am I missing a step 
Is my procedure missing some step
 
[U][B]Thank you for any help
 Art[/B][/U]

---

### Post by OnTrack on 2010-12-18
Art,
In addition to following the previous instructions about flipflop.sh exactly as given the following may help you: In the Cricket program "window" in Windows where you connect/disconnect you will see the following menu choices along the top:
Session  Tools  Options  Help
Click on help. One of the options from the drop down menu will be "About". Please click on it. Try using the number listed for MDN for your username. And use the number listed as MIN as your password when you set up in UBUNTU keeping #777 as your phone # as you previously stated.

---

### Post by azziam on 2010-12-31
I have followed ALL of the the above directions and I mean all 24 pages worth and was not successful.  You can see me struggling some pages back to no avail.  Now I am successful via a different route and my Cricket A600 connects in a few seconds every time.  First, I followed the instructions here - [http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html) - and that got my modem flipped and that's all it got me.  It didn't work if I didn't use the proper syntax of "sudo ./flipflop.sh" (the ./ were necessary).  [edit - IIRC, I didn't do the build commands but just extracted the file, made sure flipflop was made executable, and ran it.] My modem in no way showed up in the network manager and don't expect it to until you do the following (maybe it does for some people but not for me).  I wanted Gnome PPP as a front end so I searched it out making sure I had Ubuntu and amd64 in my search words.  I got the .deb for that and toted it to my Ubuntu Studio install and put it in a folder I named Cricket.  Just clicking on the deb would install it if it weren't for it saying it needed wvdial for a dependency (thought it would already be present).  Long story shortened, I kept being told I needed another dependency till I had the 5 packages I needed.  Then of course I was able to just click on those debs in reverse order and I found joy.

Here's the short list:
[http://packages.ubuntu.com/hardy/gnome-ppp](http://packages.ubuntu.com/hardy/gnome-ppp)  (pick i386 or amd64 and ignore that file list)
[http://packages.ubuntu.com/hardy/wvdial](http://packages.ubuntu.com/hardy/wvdial)
[http://packages.debian.org/sid/libuniconf4.6](http://packages.debian.org/sid/libuniconf4.6) (yep, pick out your architecture, bottom left)
[http://packages.debian.org/sid/libwvstreams4.6-base](http://packages.debian.org/sid/libwvstreams4.6-base)
[http://packages.debian.org/sid/libwvstreams4.6-extras](http://packages.debian.org/sid/libwvstreams4.6-extras)

That was a lot of legwork for me, whew!  Starting with the last first, click to install these debs and then open Gnome PPP (it'll be in Internet menu and I put it in the panel and switched to a cooler icon).  Put only your 10 digit phone # of your modem in the username space with no spaces or hyphens.  Put cricket or Cricket for your password and #777 for the number to dial.  Open Setup and make sure you have /dev/ttyACM0 (no slash after the tty and the 0 is a zero).  For some, you may need to use ttyUSB0 or tty USB1 but I know ACM0 works for some of us.  Speed=fastest available, USB Modem, Tone, heck you're done so Close the box and click on Connect.  You should be hooked up in 5 seconds and, oh yeah, now you'll see ppp0 in the Network Manger [meant Network Monitor] (ignore it just like it was ignoring your cheapass modem)! HTH, just send money to my Paypal account. :)

---

### Post by beastrace91 on 2011-01-01
@azziam

The instructions in the other link you posted... Well they are the same as what is here (only an older revision). Sounds like a carbon based issue to me - at any rate glad you got it working.

~Jeff

---

### Post by azziam on 2011-01-01
> **beastrace91 said:**
> @azziam

The instructions in the other link you posted... Well they are the same as what is here (only an older revision). Sounds like a carbon based issue to me - at any rate glad you got it working.

~Jeff

For some reason trying to run the command usb_modemswitch wasn't working for me, although if at some point(s) I had the modem switched, I couldn't tell.  lsusb could see the modem but for some reason it remained inaccessible. From what I've read elsewhere, Network Manager does not look for dial-up modems and that is what the A600 is seen as.  At any rate, Gnome PPP gives me the button to push when I need to connect Ubuntu Studio to the 'net which shouldn't be that often.  I now was able to get the 3 hundred and some updates for this Lucid install and I probably won't bother with Maverick for some time.  Thanks for your help! It's been some months since I'd tried to construct the local repositories and didn't get what I needed.

---

### Post by beastrace91 on 2011-01-01
Gnome network manager works just fine with most all modems. At least I have yet to find one it doesn't work with.

~Jeff

---

### Post by azziam on 2011-01-01
> **beastrace91 said:**
> Gnome network manager works just fine with most all modems. At least I have yet to find one it doesn't work with.

~Jeff

Glad to hear that and I can only hope others find it that easy.  From what I was reading that isn't always the case.  I've been dealing with modems, PCs, and software since '92 and I know if something is working for me or not.  If Ubuntu had had the needed tools in the OS to begin with, I would have had it connected months ago.  Anyway, if someone else has a problem with getting a machine connected with Cricket when they have no alternative connection to use temporarily, I hope the method I spelled out will do the trick - - whatever looks like the most direct route from A to B.  

A web search will find references to Ubuntu's dropping of support for ppp.  Here's one (towards bottom of page):
[https://bugs.launchpad.net/network-manager/+bug/74142](https://bugs.launchpad.net/network-manager/+bug/74142)
Again, if it works for you, then great.  Saying it's a "carbon based" error when it doesn't work for someone is of little or no help.

---

### Post by azziam on 2011-01-02
> **OnTrack said:**
> Art,
In addition to following the previous instructions about flipflop.sh exactly as given the following may help you: In the Cricket program "window" in Windows where you connect/disconnect you will see the following menu choices along the top:
Session  Tools  Options  Help
Click on help. One of the options from the drop down menu will be "About". Please click on it. Try using the number listed for MDN for your username. And use the number listed as MIN as your password when you set up in UBUNTU keeping #777 as your phone # as you previously stated.

Are the above suggestions from firsthand experience?  Username is your modem's 10 digit phone number and you don't need the @----------.--- but if that also works, fine.  Password is cricket.  #777 is #777.

---

### Post by azziam on 2011-01-02
Jeff,
Here's an update after going back and rereading the first 12 pages and the last few pages of this thread (my eyes are tired).  Even though I got things working fine with Gnome PPP I was not satisfied without finding out why your instructions didn't work for me.  I see that back in August I'd already said that Ubuntu Studio didn't come with Network Manager included in the install.  I'd forgot about that and was thinking it was one of either Network Monitor or Network Tools in the System>Admin menu.  I checked through Synaptic for network-manager-gnome and installed it.  Then I had to figure out that it had shown up as Network Connections in System>Preferences menu as it didn't show up in the panel right away.  The modem wasn't showing up in it either.  I disconnected Gnome PPP and checked again.  I rebooted and checked more than once.  So, I reconnected with PPP.  After reading for a while I checked again and it showed the A600.  There was no sign of it being auto-configured (maybe I needed to give it another 20 minutes to think some more <g>).  It asked for the 3 essentials and I entered the 10 digit phone number, cricket, and #777.  Then it was able to work.  Are you saying it usually even detects the phone number of the modem?  Anyhow, it was wanting a password every time till I blew away the login.keyring.  After a few reboots it's working fine.  Now I have a choice of two places where I can click twice after booting up and I'm connected.  The fact is, I wouldn't have got it working if not for getting Gnome PPP working first.  At least, if I had, I probably would have been booting back and forth repeatedly before I had 9 or so dependencies.  I have a cold and I'm a bit cranky but regardless, I hope the Ubuntu team got this stuff right in Maverick.  I'm tempted to blow off this Lucid distro and find out, partly because there should also be a major change in how hard drives are recognized (hd vs. sd) but that's another topic and another can of worms that deals with replacing a previous patched up can of worms in hard drive control.  I'm feeling physically miserable at the moment but I'll manage to say Cheers and Happy New Year!  Keep up the good work.

---

### Post by William Dojinn on 2011-03-18
Using 10.10 here. Good news and bad news. Good news is the A600 is seen just fine. Bad news? I have no idea how to connect.

I'd tried the 501(your modem number)@mycricket.com and I've tried it without the 501. Both times using 'cricket' as the password and absolutely Jack Nothing. It'll make the attempt according to the little signal bouncing icon but after that. Zilch.

Tried under xfce, but still have stock Gnome if switching back would make any difference.

Fairly sure the problem is user error, but I'm not sure where I fumbled the ball at.

---

### Post by DarkTide on 2011-03-25
This computer has the original ubuntu netbook remix. and has never been  online and unless I get this thing to work I cant download from ubuntu's  add or remove, but I have installed the "cricket_flip_i386.deb" file  from one of the sites, that I found, and the instruction after that was  to run "flipflop.sh" but at that point it never asks for a passcode like  the instuctions say should happen. I went to see if the wireless then  worked but it never shows. (This is my girlfriends work so im not to in  the loop, sorry-she was trying to help me but ended up doing more of it)  
The other thing we tried was just plugging in the modem and then put our  phone number with the cricket address. and then setting the passcode to  cricket and that was of no luck. Well thats about all we tried I guess.  
Dude I hope this helps you help us.

---

### Post by desnaike on 2011-03-25
Everyone the simplest way i've found is have the cricket store activate the device for you then through synaptic package manager install usb-modeswitch-data I did it at starbucks on the way from the cricket store (did'nt have a connection at home ) plugin the device and walla.

---

### Post by beastrace91 on 2011-03-25
> **desnaike said:**
> Everyone the simplest way i've found is have the cricket store activate the device for you then through synaptic package manager install usb-modeswitch-data I did it at starbucks on the way from the cricket store (did'nt have a connection at home ) plugin the device and walla.

Ahh it is truly wonderful that things have become this easy in just a yearishs time! Glad to see my flipping code made it upstream :)

~Jeff

---

### Post by shakma on 2011-10-25
GREAT NEWS!

I was about to be sad because usb-modeswitch-data is no longer available in the 11.10 repositories, but...

There is now a fully automated Mobile Broadband "wizard" that pops up when you first plug in an appropriate device.  My Cricket A605 was automatically detected, and after confirming my country and my provider, it began working immediately!!

Go Ubuntu!  Go 11.10!!!:guitar:

---

### Post by zacharysonicfast on 2012-10-18
I wish ANY Linux distro would even recognize my cricket dongle...

 ZTE AC3781 usb dongle   10/18/2012

Until Linux catches up I am STUCK with Windows 7
:mad:

Lets assume you had some flavor of linux and only had the usb dongle to connect with.

How then could someone D/L the necessary items to get it to work?
Reminds me of Win98 on a dialup with a corrupted inf file and no driver disk...

---

