---
title: "Recognizes ethernet connection, but cannot go online to download drivers"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by tcdevotie on 2011-03-25
Hi,

I recently downloaded and installed Ubuntu 10.10 (I believe? - the  current version) alongside my Windows XP that came with the HP Mini  laptop I have.  I installed it at home where I have dial up connection,  so needless to say I did not install Ubuntu while connected to internet.   Probably should have in hindsight. The system works flawlessly with  the exception I cannot click the mouse pad and use another finger to  scroll the page or something...that isn't the main issues I'm having.

1.) Wireless does not connect.  I've read around and one suggestion was  to find an ethernet connection and the Ubuntu would begin the necessary  downloads it needed to work properly.  I did this and all I got was that  is was connected, but not internet usage and downloads to help.  Here  is the output of the command...

**sudo lshw -C network**

> 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: c8:0a:a9:6c:40:d9
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10MB/s
       resources: irq:42 ioport:5000(size=256) memory:50010000-50010fff memory:50000000-5000ffff memory:50020000-5002ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:56000000-56003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: f0:7b:cb:2d:0b:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43  driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes  wireless=IEEE 802.11bg
2.) I also tried to see about **ndiswrapper -1** as well as **lspci | grap Wireless**

Both of the above commands were recognized and I was told they were not  installed.  I was then given the command from the terminal to download  them.  After typing it in it was said they could not be found.

I apologize if the code is hard to read.  I wasn't sure how to make it indented correctly from posting.


That's what I'm working with.  I hope that's all the info you need.  Let me know what else you might need.  

Thanks for the support.

_____________

One thing to note is that I know it says network DISABLED, however, it  is enabled because when I right click the option it clearly saying it is  enabled.

---

### Post by josephmills on 2011-03-25
> **tcdevotie said:**
> Hi,

I recently downloaded and installed Ubuntu 10.10 (I believe? - the  current version) alongside my Windows XP that came with the HP Mini  laptop I have.  I installed it at home where I have dial up connection,  so needless to say I did not install Ubuntu while connected to internet.   Probably should have in hindsight. The system works flawlessly with  the exception I cannot click the mouse pad and use another finger to  scroll the page or something...that isn't the main issues I'm having.

1.) Wireless does not connect.  I've read around and one suggestion was  to find an ethernet connection and the Ubuntu would begin the necessary  downloads it needed to work properly.  I did this and all I got was that  is was connected, but not internet usage and downloads to help.  Here  is the output of the command...

**sudo lshw -C network**

2.) I also tried to see about **ndiswrapper -1** as well as **lspci | grap Wireless**

Both of the above commands were recognized and I was told they were not  installed.  I was then given the command from the terminal to download  them.  After typing it in it was said they could not be found.

I apologize if the code is hard to read.  I wasn't sure how to make it indented correctly from posting.


That's what I'm working with.  I hope that's all the info you need.  Let me know what else you might need.  

Thanks for the support.

_____________

One thing to note is that I know it says network DISABLED, however, it  is enabled because when I right click the option it clearly saying it is  enabled.

hi there there is a couple of ways of fixing this but could you 
post this for us to see 
```
 lspci -vnn | grep 14e4 
```
 reinstalling  ubuntu with the internet hooked up (this is the easy way out )
there are other ways to but first lets that card thanks

---

### Post by tcdevotie on 2011-03-25
> 

Broadcom Corporation BCM4312 802.11b/g LP-PHY



Hope it helps.

---

### Post by josephmills on 2011-03-25
> **tcdevotie said:**
> Hope it helps.

ok plug in your ethernet/phone cable and then unplug it then plug it in again then post 
```
ifconfig 
``` thanks

---

### Post by tcdevotie on 2011-03-25
Ok I will as soon as I can. I'm at school at the moment, in about an hour or so I'll post back. While you're waiting can you give me suggestions about reinstalling with Internet connected? Am I supposed to uninstall? I'm sure there's a post for it so if you know the general area I'll check it out just in case.

---

### Post by josephmills on 2011-03-25
if you are online via eth0 then try this 
```
sudo apt-get upgrade
```
then 
```
sudo apt-get update
```
then
```
sudo reboot 
```
then go to System-->Addmin-->Additional Drivers 
it will search for a min or two then b43 driver should come up activate the driver close the box then 
```
sudo apt-get update 
```
then 
```
sudo reboot
```
then try your wireless hope this helps

---

### Post by josephmills on 2011-03-25
> **tcdevotie said:**
> Ok I will as soon as I can. I'm at school at the moment, in about an hour or so I'll post back. While you're waiting can you give me suggestions about reinstalling with Internet connected? Am I supposed to uninstall? I'm sure there's a post for it so if you know the general area I'll check it out just in case.

try step 6 after you get home and eth0 is connected and let us know what happened hope that this helps

---

### Post by tcdevotie on 2011-03-25
Ok, tried tha codes given and no new upgrades were downloaded and updates failed apparently.  Also, when I click for wireless it says firmware is missing.  When I get to the software center to get it no download happens. So....looks like another option? Or should I reinstall connected to the Ethernet?

---

### Post by josephmills on 2011-03-25
> **tcdevotie said:**
> Ok, tried tha codes given and no new upgrades were downloaded and updates failed apparently.  Also, when I click for wireless it says firmware is missing.  When I get to the software center to get it no download happens. So....looks like another option? Or should I reinstall connected to the Ethernet?

yes I would re-install if I were you. When installing ubuntu 10.10 a box comes up that has some green tick marks next to it is will say connected to the internet and plunged into a power source etc. make sure that the green tick is there for the internet. After installing repeat step 6

---

### Post by tcdevotie on 2011-03-25
Ok, the only issue is that I'm unsure how to safely reinstall without taking up more drive space.  Can you suggest a link to help or anything?

---

### Post by josephmills on 2011-03-25
> **tcdevotie said:**
> Ok, the only issue is that I'm unsure how to safely reinstall without taking up more drive space.  Can you suggest a link to help or anything?

use gparted to erase the partion for ubuntu that you have all ready and reinstall  

[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.youtube.com/watch?v=uMW_p_9cAH4](http://www.youtube.com/watch?v=uMW_p_9cAH4)

---

### Post by tcdevotie on 2011-03-25
Quick question, the GParted, from the link you gave me it has to be booted from a live CD, is it ok that I use a USB like I did for the ubuntu itself?  And can I run it in windows?  This is a HP mini I'm using that doesn't have a CD tray.

---

