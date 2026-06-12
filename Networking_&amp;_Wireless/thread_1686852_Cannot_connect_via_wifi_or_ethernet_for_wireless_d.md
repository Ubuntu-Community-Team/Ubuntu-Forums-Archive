---
title: "Cannot connect via wifi or ethernet for wireless driver activation."
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Alexalad on 2011-02-13
I recently installed ubuntu 10.10. Everything worked fine except the fact that it seems impossible to acquire an internet connection.

When I select the wifi icon on the panel, it just shows "No network devices available". I know my network can be found when I search with my iPhone, so I know there are networks to connect to.  So, I checked the drivers, and it informs me that the B43 and STA drivers are not activated. So thats not a big deal, I guess, but when I use my ethernet cord, my laptop doesn't recognize/acknowledge (I'm not sure what the right term would be)it. I'm fairly sure I can't activate these drivers without an internet connection because when I do try, a message pops up saying "failed to fetch" with some long link.

My only guess is that it could be a hardware problem, but I really have no idea. I guess the ethernet problem is my only real problem. Because after I establish and internet connection the the rest is easy to fix.

I'm sure its obvious, but I'll go ahead say that I'm a novice ubuntu user. I've only been working with it for about a week, but I'm learning alot.

---

### Post by mips on 2011-02-13
What have you done so far to try and get your wired connection going?

---

### Post by gerowen on 2011-02-13
Many modems (the one from your ISP, not your router) have a USB connector in the back of them.  This has many functions, one of them being providing internet access via USB, :-)  Just run a USB cable from your modem to your computer and Ubuntu should pick it up and use it for internet access so you can install the proprietary drivers for your other network devices.  You "might" have to reset your modem after doing this though, some of them get picky about which device is authorized to access the net through them until you power cycle them.  I've used this method before for computers that had similar problems to gain access to the internet.

---

### Post by Alexalad on 2011-02-13
I've tried connecting my laptop and my router with an Ethernet cord, but nothing seems to change. Would restarting my router really help?

---

### Post by gerowen on 2011-02-13
Use a "USB" cable, and your "modem", not your router.  This is assuming you, like me, have a little black modem that you got from your ISP, and your router runs through the modem.  I've done this and gotten internet access via USB so I could get other things done.

---

### Post by Alexalad on 2011-02-13
My modem does not have a USB port to use. My router doesn't either. There's only Ethernet ports. Which aren't working with my laptop at the moment.

---

### Post by jermanbdogg on 2011-02-14
in terminal what is the output for the command:

lspci -vnn | grep 14e4

---

### Post by Alexalad on 2011-02-19
My output was:
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY
[[COLOR="Red"]14e4[COLOR="Black"]:4315] (rev 01)[/COLOR][/COLOR]

---

### Post by jermanbdogg on 2011-02-19
I have the exact same one as you. Took me forever to find an answer. I have mine fixed. I have the step-by-steps laid out below. The LP-PHY part means that it is low-powered and needs a specific older driver in order to activate it.

[B]Install B43 Broadcom Wireless Driver on HP Mini 1119nr 
Ubuntu 10.10 Desktop edition – from clean install (no wired or wireless connection at start up)
PCI-ID: 14e4:4315
Driver needed: BCM4312 LP-PHY[/B]

**My install guide was made from 2 sources:**
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[http://fedoraforum.org/showthread.php?t=218303](http://fedoraforum.org/showthread.php?t=218303)

**Before starting make sure that the power and ethernet cable is plugged in**

From a working internet computer download b43-fwcutter (version 13 at time of posting) from:
[http://packages.ubuntu.com/maverick/b43-fwcutter](http://packages.ubuntu.com/maverick/b43-fwcutter)

and

Download broadcom-wl-4.178.10.4.tar.bz2 (incorrectly labeled) should be 4.174.64.19 (label not important though) from:

[http://downloads.openwrt.org/sources...8.10.4.tar.bz2](http://downloads.openwrt.org/sources...8.10.4.tar.bz2)

Put them in a folder called drivers and put it on a thumb drive and move it to the problem computer on the desktop.

Go into the drivers folder on the desktop and double click on b43-fwcutter.deb to install it. (it will open software center &#8594; click on install. Once it is installed close software center.

Back in Nautilus, right click on broadcom-wl-4.178.10.4.tar.bz2. Left click on extract here.

In the Ubuntu menu click on Applications &#8594; Accessories &#8594; Terminal

Type: 
cd Desktop/drivers/broadcom-wl-4.178.10.4.tar.bz2/linux

Then type: 
sudo b43-fwcutter -w /lib/firmware wl_apsta.o
(this is going to build the driver in the firmware folder)

Reboot the computer

After logging in you should have a wired connection. (check Firefox for internet connection) Also check to see if the blue light is on the front of the laptop. (if not flip the switch to see if it comes on)
-if light is on, check the network connection icon to see if a list of wireless networks come up.

---

### Post by Alexalad on 2011-02-19
I followed your guide, and everything worked perfectly. I've activated my B43 driver, and the wifi seems to be working fine right now. Thanks.

---

### Post by jermanbdogg on 2011-02-19
Congrats. Glad I could help. Happy Ubuntuing! :)

---

