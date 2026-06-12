---
title: "Belkin F6D4050 USB wireless WiFi"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by huh? on 2009-12-12
just bought a Belkin USB wireless, Model F6D4050 V2...it works on the Vista machine okay...
 just on a chance it work on 9.04,  I plugged it into a USB port...nothing...searched thru the USB portion of the trouble shooting guide and didn't see the model number listed...
 I suppose I might have to wait till some one comes up with a new driver...
 any suggestions ? 
 thanks

dutch, North Carolina

---

### Post by The Toxic Mite on 2009-12-13
Hey!

Can you go to Applications > Accessories > Terminal, and enter the following command?

```

lsusb

```

Post the outputs when done :)

---

### Post by slughappy1 on 2009-12-24
I have been trying to find drivers or help for this product for a little while now. My lsub is ```
jason@Barnaby:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 050d:935a Belkin Components 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 005: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@Barnaby:~$ 

```

---

### Post by SeaJayEmm on 2009-12-27
You will need internet access on the computer. Either wire it to your router, or share an internet connection from another computer via crossover cable. Also you must have the rt2870.inf and the rt2870.sys from the xp x64 driver. If you need them email me at [email]justin6382@gmail.com[/email]. 
Use ndisgtk to install the driver.Open a terminal and type....
sudo apt-get update
after that is finished
sudo apt-get install ndisgtk
after that is finished 
sudo ndisgtk
a GUI will pop up go to the location of your rt2870.inf and the rt2870.sys is located and select the .inf file, click install
Reboot and you should be online. You may have to enter your ESSID and password.
You must have the rt2870.inf and the rt2870.sys from the xp x64 driver. If you need them email me at [email]justin6382@gmail.com[/email]. 
Use ndisgtk to install the driver.
I have a Belkin F6D4050 and have it installed and working under ubuntu 9.10. 
If that doesn't work post back and I will help you further.

---

### Post by slughappy1 on 2009-12-27
Do I need the 1000 or 2000 driver? I found the [website]("http://en-us-support.belkin.com/app/answers/detail/a_id/2752"), but I don't know which to use.

---

### Post by SeaJayEmm on 2009-12-27
These are the files you need in order to install the Belkin F6D4050....
rt2870.sys & rt2870.inf. If you have the Windows driver disc that came with the usb wireless adapter these files can be found on that disc. And again I can email them to you.

---

### Post by slughappy1 on 2009-12-28
Thanks for all that, it works! One more question. So why does linux have to use the xp drivers and not the vista drivers?

---

### Post by SeaJayEmm on 2009-12-28
You know I am not really sure. Honestly I have never booted up a Vista machine before. From the screen shots and a few videos I have seen online about Vista, it reminds me of WinME, it sucks.

---

### Post by wah fun on 2010-01-07
SeeJayEmm,

I have the Belkin F6D4050 v2 USB network adapter and a Belkin Enhanced wirelss router. I have ubuntu 9.10 and have tried just about everything to get it to work but no joy. Ndiswrapper just doesn't do the trick for me. What did you do to get yours to work?

thx,
wah fun

---

### Post by dominic27b on 2010-01-10
I have the Belkin F6D4050 v1 and I contacted Belkin tech support and asked them if I could have the file and they said, "sorry, we don't support Ubuntu." I knew all I needed was the .inf file for my card, and I would be good.

I found my CD, I installed the .inf file, and then I clicked "Configure Network", and it said "Unable to determine if hardware is present" (it was present). It said on the main menu under r2870.inf, Hardware Present: yes, but it wouldn't work. What do I do now?

---

### Post by slughappy1 on 2010-01-10
For the v1 this is what you do, I would think that the v2 would be close to the same.

```
1- You must have the rt2870.inf and the rt2870.sys from the xp x64 driver, which you can get from the Driver CD that came with. Copy the two files to a folder somewhere on your computer.
2- Open a terminal and type....
3- "sudo apt-get update && sudo apt-get install ndisgtk && sudo ndisgtk" but take the quotes out
4- A GUI will pop up. Click on Install New Driver and go to the location of your rt2870.inf and the rt2870.sys and select the .inf file, click install
Reboot and you should be online. You may have to enter your ESSID and password.

```

---

### Post by Markur on 2010-01-13
Hey

I tried to get my belkin usb-adapter f6d4050 v1 to work by following your steps. I got the driver from the CD and installed succesfully the ndisgtk. When I load the driver by clicking "Install" ob the driver after choosing where the rt2870.inf is from the xp x64 version (as obviously the rt2870.sys) is, the guy puts a line like "rt2870 - Driver with some error" (its german). Then I can not find wireless networks in the networkmanager. - I suppose its the error of the driver.
If I load the XP_2K rt2780.inf it tells that it's not able to test whether there's hardware or not.  Typing then lsmod in the terminal says that ndiswrapper is activ, but also no connectivity - there's no rt2870sta. The same for the Vista_x86. Ant the case like above I get with the Vista_x64.

lsusb gives a line 
Bus 001 Device 003: ID 050d:935a Belkin Components 
that you know there is the stick. It shows its everytime LED. Uder Windows the stick didn't make any troubles.

Yesterday I updated to Ubuntu 9.10 because I read in the internet two other posts where the poeple using 9.04 failed with the installation.

Eventually you can helb me. Thx

---

### Post by Jorenu on 2010-02-01
Can someone upload those two files, due I forgot my CD at home..
Please?

---

### Post by slughappy1 on 2010-02-01
If you give me your email address, I'll send them to you now.

---

### Post by pjhercules on 2010-02-09
I have followed the directions in this post and when I point to the .inf file a window opens stating:Unable to see if hardware is present.  And in terminal it states: Warning: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.  Any ideas?  Thanks for your help.

---

### Post by slughappy1 on 2010-02-10
I'm not sure about the config files part, but my computer some times needs to boot with things in. So I would try turning off your computer, insert usb, and then turn it on and try again.

---

### Post by David Batty on 2010-02-10
Thanks I have just bought a Belkin wireless usb adaptor and used your solution to to install it. Everything worked first time, many thanks!:p

---

### Post by askoa on 2010-02-13
Hey! I got this adapter too, but cant get the driver files anywhere (my usb-dongle came without a cd..?) Could you please send me them via email? Thank you very much!

---

### Post by SeaJayEmm on 2010-02-14
Email me at [email]Justin6382@gmail.com[/email] for the Belkin F6D4050 drivers. You will need to let me know if you are running a 32 bit or 64 bit Ubuntu. For those of you having problems getting this adapter to work make sure you are using the correct driver. If you are running a 64 bit Ubuntu you need to use the XP_x64 drivers, if you are running a 32 bit Ubuntu you need to use the XP_2K drivers. Also make sure you use ndisgtk to install the drivers rather than cli ndiswrapper. You also need to make sure you hardwire your computer to your wireless router via an ethernet cable and update your system before installing.

---

### Post by Lord Finga on 2010-03-20
I also have Belkin F6D4050 v1 and got it to work by using the ndisgtk tool. But after some time being online (around half an hour or so) I get disconnected. I tried to run lsusb to determine if the stick is still recognized but the terminal doesn't respond and it also doesn't do for other terminal commands. After a reboot everything is back to normal for a while again. Any ideas? Using Ubuntu 9.10 64 bit.

---

### Post by minerbog on 2010-11-08
Hi Guys,

I have a belkin F6D2050 v2 wireless usb stick. Had no end of problems trying to get it to work. I read somewhere on this forum (can't remember where and my history is gone after the install) that Ubuntu 10.10 gets this wifi working out of the box??

Its true, install 10.10 reboot plug in and away you go.

---

### Post by AndrewS on 2011-12-19
Hello

I just came across this thread on getting a Belkin router to work in Linux, and wondered if a similar approach might help me out?  I have a Belkin network USB hub (F5L009ea) which should allow me to share usb devices (hard drives, printers etc) between networked PCs without any particular PC needing to be switched on.  It seems to work OK under Windows XP, but under Ubuntu 10.04 (my preferred OS) I can see a hard drive by entering the IP address in Chromium or Firefox, but cannot connect to the drive.  I was wondering if I needed a driver for the hub?

I would appreciate any help you might be able to offer on this.

Thanks

Andrew

---

