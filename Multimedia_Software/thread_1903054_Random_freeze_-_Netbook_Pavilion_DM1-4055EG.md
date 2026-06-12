---
title: "Random freeze - Netbook Pavilion DM1-4055EG"
date: 2012-01-01
forum: Multimedia Software
---

### Post by marcuslauer on 2012-01-01
Hello,
I have (had) several problems with my new HP Netbook DM1-4055EG with Ubuntu 11.10 oneiric ocelot (32 and 64 bit versions)
Hardware: AMD Dual-Core E-450 (Vison E2) with 2x 1,65 GHz / 4 GB RAM / 500 GB HDD / 11,6" 29,6 cm Brightview LED-Display 1366x768 / AMD Radeon HD6310M onboard graphic.

I think the hardware in the Pavilion DM1-4000 series is almost the same?

The first problem was the bad wifi-connection (WLAN Chipset BCM 4313). I solved this by using the propietary STA-driver by Broadcom and blacklisting the following kernel modules (in /etc/modprobe.de/blacklist.conf):

blacklist brcm80211
blacklist brcmsmac
blacklist brcmfmac
blacklist bcma

Second problem was the fact that the display started flickering sometimes. It looked like an old cathode ray tube on 60 Hz. Ugly... It came on nearly every session I used the netbook.
I watched it for some days - it was always was after the time the display gets automatically darker or after reactivating (only screensaver - never after suspend). Now I deactivated screensaver and the "automatically getting darker function" (sorry - german ubuntu - I don't know the english expression for it). Now the screen doesn't flicker anymore - but I have to swith the display off by using a skript with the command "xset dpms force off"). For the moment ok - but not perfect.

Ok, if someboby has the same problems I can help by giving futher information. I fight against the problems on this netbook for some weeks and tried a lot.

But one problem I can not solve by myselve. :confused: The netbooks freezes randomly - especially by high workload (extracting rar archives) and very often by watching Flash-Videos (for example youtube).

At the moment I use the fbdev (framebuffer) driver for the graphiccard. It seemed to be a little bit better than the radeon which is included in oneiric. But this day the Netbook was frozen several times. No mouse, no keyboard, no buttons - only the screen (frozen) was shown. The sound in the buffer (last 3-5 seconds) plays in loop. So no real advantage to the radeon.

I didn't use the proprietary AMD driver because the driver included in the ubuntu-repositorys doesnn't fuction properly. There is a watermark with "not compatible" after activating. 

Ok, what about the other Ubuntu-users with this Netbook or netbooks with the same chipset ... Do you have the same problems? Is the chipset not supported by ubuntu? I didn't find any other problems in the forum with this device.

Thanks, Marcus

---

### Post by marcuslauer on 2012-01-03
Ok, now I installed fglrx (catalyst) - via dwonload and build from amd.com. Newest realease. My netbook freezes also with this graphics driver. half a day it was ok - but then it was frozen. mysterious.

Can anybody confirm that there are normally no problems with this chipset? Now I try one week win7. what an annoyance... 

ML

---

### Post by sathiyamoorthy on 2012-01-04
I am also facing the same issue in ubuntu 11.10 and HP DM1 4004sa Pavillion laptop.

I installed ATI drivers, but it still freezes !!

Can anybody resolve this issue ?

Thanks for your time.

---

### Post by marcuslauer on 2012-01-04
Ok, tried one more clean installation of oneiric. With no significant changes on the system (64 bit) it freezes so I give up.

Now I try natty on a second partition. Perhaps this computer is more stable with the old ubuntu release. Waiting for Ubuntu 12.04. ? ...

I will tell you my experience with natty.

Cheers, ML

---

### Post by marcuslauer on 2012-01-04
> **sathiyamoorthy said:**
> I am also facing the same issue in ubuntu 11.10 and HP DM1 4004sa Pavillion laptop.

I installed ATI drivers, but it still freezes !!

Can anybody resolve this issue ?

Thanks for your time.

Hi, you have the same hardware than my machine (the videochip is nearly the same). Do you have also the Broadcom BCM4313 WIFI-Chip? I have an vague suspicion that the WIFI is the cause of our problem. This WIFI-Chip made the most problems after installation.

I testes all available drivers for the graphic - with no difference (radeon, fbdev, fglrx).

Cheers, ML

---

### Post by sathiyamoorthy on 2012-01-05
Yeah here is the solution that worked for me. Installed the fglrx-updates which installed two other packages.. Rebooted and played videos to check and worked around an hour - no issues !

I believe it is fixed !

---

### Post by marcuslauer on 2012-01-07
Ok, what about you system. No more freezes with this the last days?

For me it didn't function. With Natty no problems for 2 days.

ML

---

### Post by marcuslauer on 2012-01-18
Ok, I'm a little bit resignated.

I tried the following Ubuntu Versions:

11.04
11.10
12.04 alpha (by the way - the new release at it's self is very stable and I liked it very much)

Alwas the same behaviour. It freezes. Sometimes only one or two times a day. But this device is not stable with ubuntu. I can't explain. I tried several drives for the graphiccard.

Other AMD Vision Netbooks don't have this issue with ubuntu. mysterious...

So, if you decide to buy this device - don't use it with ubuntu.

Now I have to go back to windows 7?

---

### Post by renataogarcia on 2012-02-06
Hi [marcuslauer]("http://ubuntuforums.org/member.php?u=768924"),

I have a different setup but I'm facing some crashes also, only with the  open source driver. Those are some of the items I've checked that might want to try too:

- Since you mentioned that you get on high load and video it would be worth checking memory with memtest.
- Disable Hardware acceleration -> [http://askubuntu.com/questions/2301/randomly-freezes-how-can-i-diagnose-the-problem](http://askubuntu.com/questions/2301/randomly-freezes-how-can-i-diagnose-the-problem) . Although this is not a solution, might help to identify if it's GPU related.
- Check temperature of the devices, specially the GPU. Try using sensors.
- Debug with netconsole. Same link as above.

---

### Post by marcuslauer on 2012-02-07
> **renataogarcia said:**
> Hi [marcuslauer]("http://ubuntuforums.org/member.php?u=768924"),

I have a different setup but I'm facing some crashes also, only with the  open source driver. Those are some of the items I've checked that might want to try too:

- Since you mentioned that you get on high load and video it would be worth checking memory with memtest.
- Disable Hardware acceleration -> [http://askubuntu.com/questions/2301/randomly-freezes-how-can-i-diagnose-the-problem](http://askubuntu.com/questions/2301/randomly-freezes-how-can-i-diagnose-the-problem) . Although this is not a solution, might help to identify if it's GPU related.
- Check temperature of the devices, specially the GPU. Try using sensors.
- Debug with netconsole. Same link as above.


Hello,
thank you for you reply. I will try it. Nice point to dive in again ;-)
At the moment I only use it at work with win7. It was most stable with the combination natty 32bit and latest catalyst - but also not "freeze-free" ;-)
You write that your device freezes only with the open source driver. Did you also try the AMD catalyst driver?

Bye, ML

---

### Post by renataogarcia on 2012-02-07
Yeah, I tried Catalyst. It worked for me,  or at least much less freezes than I have with open source. However since I've changed to Gnome Shell I had to move to open source driver because Catalyst wasn't working well with Gnome Shell, specially with 3 monitors, which is my case.

---

### Post by michaelk1 on 2012-03-25
I had similar problems with Mint 12 64-bit.
I turned off power management for wireless card. Hasn't frozen since.

As root, create file etc/pm/power.d/wireless containing

#!/bin/sh
/sbin/iwconfig eth1 power off

then 
chmod 755 /etc/pm/power.d/wireless
reboot
(assuming wireless device is eth1, might be wlan0).

Michael

---

### Post by marcuslauer on 2012-03-25
Hello Michael,
thank you for the hint. I try it out.

ML

> **michaelk1 said:**
> I had similar problems with Mint 12 64-bit.
I turned off power management for wireless card. Hasn't frozen since.

As root, create file etc/pm/power.d/wireless containing

#!/bin/sh
/sbin/iwconfig eth1 power off

then 
chmod 755 /etc/pm/power.d/wireless
reboot
(assuming wireless device is eth1, might be wlan0).

Michael

---

### Post by marcuslauer on 2012-04-22
Hi,
yes wireless device is eth1. i thied it out. but i think i have no fortune with this netbook. under ubuntu 12.04 beta freezes are extremely rarely. but they happen. in the last 2 weeks 2 times.
1) when i thied to install google chrome browser
2) during watching a youtube video

So, under ubuntu 12.04 it is much better but not perfect. youtube freeze is a well known friend from the previous ubuntu releases.

> **marcuslauer said:**
> Hello Michael,
thank you for the hint. I try it out.

ML

---

### Post by MrArch on 2012-05-25
Same problem but I'm using Arch Linux so I guess it's linux specific and not really Ubuntu specific. The freezes happen mostly during high load and youtube videos but it also happens when I'm typing some documents in LibreOffice. I also noticed the brcmsmac driver is very dodgy so I use the broadcom wl driver.

Using the open source or proprietary drivers does not make any difference. Tonight I will try installing Debian stable to see if an older kernel fixes the lockups.

Anyone found a fix for the hard lockups?

---

### Post by marcuslauer on 2012-05-27
Hi,
I didn't find any solutions and yes I think it is a Linux kernel issue - not related to any ubuntu version. And I don't know if the freezes are caused of the wireless modulr or graphicdriver or something else.

I use the Netbook at work with win7 - no problems. It's a shame...

ML

---

### Post by pjbroad on 2012-07-03
Sounds very like this issue, same hardware, same random hard freezes.
[http://ubuntuforums.org/showthread.php?t=1989051](http://ubuntuforums.org/showthread.php?t=1989051)

---

### Post by MrArch on 2012-07-16
Finally found the solution:
[http://ubuntuforums.org/showthread.php?p=12108086#post12108086](http://ubuntuforums.org/showthread.php?p=12108086#post12108086)

---

### Post by marcuslauer on 2012-07-21
Hello,
here is a possible solution for the lockup/freeze problem with this netbook. Found it at the HP support forum and it seems to work:

Quote:

For anyone else with this problem, for info, I'm using grub, and the simplest way I found to disable the thermal module was to edit /etc/default/grub.
This had a line something like:
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 
To disable the thermal module, I changed this to:
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.off=1"
 
Having edited this file, you then need to run
 
update-grub
 
to activate the change.

[http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/HP-Pavilion-DM1-4033ef-linux-freezes-randomly/td-p/1339919/page/2]("http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/HP-Pavilion-DM1-4033ef-linux-freezes-randomly/td-p/1339919/page/2")

---

### Post by pjbroad on 2012-07-22
I've been running with the grub option "thermal.off=1" set on my dm1-4125sa for a few days and, so far, no freezes. The best its been since the day I bought it.:)

---

