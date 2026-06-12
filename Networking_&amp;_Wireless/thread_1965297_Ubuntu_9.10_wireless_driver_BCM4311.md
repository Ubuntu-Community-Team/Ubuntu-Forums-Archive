---
title: "Ubuntu 9.10 wireless driver BCM4311"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by protocoder on 2012-04-25
Hi Experts,

I am out of ethernet and wireless connection after re-installing Ubuntu 9.10

From other computer with access, I have installed NDISwrapper.

I have downloaded the BCM4311 14e4:4319 (rev 02) driver exe 
and I do not have wine, carbextract and I could get all the needed files by unzip to a single folder.
I kept all these files in single folder and let Wireless Network Drivers see the INF file to install the driver. 
I see this error " Unable to see if hardware is present"

Please can some one help me from here. 
Thanks in Advance
Anand

---

### Post by nothingspecial on 2012-04-26
*Thread moved to **Networking & Wireless**.*

---

### Post by protocoder on 2012-04-26
Thank you nothingspecial 
for moving to the right folder and apologies for posting at wrong place. 


In the post above, I could able to find the Broadcom drivers 
SYS and INF file though the name of the INF file is different oem28.inf ! (??), on opening this I am sure it is same as BCMWL5.

However when I point this INF file to in the "Wireless Drivers", It does not see the hardware "Unable to see if hardware is present"

I have done some debug on why the driver is wrong and here is analysis which I need your help.
The latest driver from Dell and the existing windows SYS and INF file were pointed by putting all relevant files in a same directory as instructed in the [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I am not able to see hardware, even when I pointed to the existing windows drivers and also unzip the latest Dell ones with same issue. Here is the analyis.

lspci command
03:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

lspci -n command
03:03.0 0280: 14e4:4319 (rev 02)

So the driver I should be looking for BCM4311 14e4:4319 (rev 02).
1. Is there any such driver ? Not according to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) chip ID bearing 14e4:4319 are shown belonging to BCM4318 and not BCM4311. 

So why is my broadcom chipset and chipids are different?

For BCM4311 chipset, the relevant Chip IDs are 14e4:4311 and 14e4:4312. 
So please can someone help me understand if there is issue some where. 

2. Why the SYS, INF taken from the windows directories do not work either. 

Note: Last time some one was nice to give me the relevant INF files ..which I think I lost when I had to re-install. 
I have Dell Latitude D610 laptop. Any help, pointing any mistakes would really be appreciated.

---

### Post by wildmanne39 on 2012-04-26
Hi, 9.10 is very out dated so you may not be able to install the driver from restricted drivers, you should upgrade to at least 10.04 then run this command:
```
sudo apt-get install b43-fwcutter
```
unplug wired connection and reboot.
or:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
if you install 11.04 or later.
Thanks

---

### Post by protocoder on 2012-04-27
Hi wildmanne39,

Thank you again for the message. Yes I am going for upgrade and I having the right INF, right driver with me ready will enable me to upgrade easily. My effort is to get the drivers which worked earlier and to understand what mistake I am doing as same issue can come when I move to latest ubuntu or linux mint.

Is any one who had same issues or seeing any mistake of mine .. can some one share me the INF for Dell Latitude D610 laptop.

Please advice.
Thanks a lot

---

### Post by wildmanne39 on 2012-04-27
Hi, you do not need the INF file if you upgrade your card is supported in later versions of ubuntu.

It may take some tweaking to get it to work but in my last post I gave you the commands to run to install the driver you need if the pci id is 4311. Please post the output of the following command so we can see what it says.
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by protocoder on 2012-04-28
Thank you wildmanne39

I was trying to figure to get to internet and finding the right INF only to make sure I give these right input when I install new ubuntu or linux mint, Thanks for letting me know that new versions does that automatically with a command. Now this issue probably it is only case of curiosity on why drivers are not accepted.

I think tomorrow I will download new version, mostly mint as it comes with all the packages and bit friendly as long as it supports c,c++ and python programming environment. 

Meanwhile here is the output 
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit 
Ethernet PCI Express [14e4:1677] (rev 01)
	Kernel driver in use: tg3
	Kernel modules: tg3
--


03:03.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 
802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

In the blacklist, I had ssb as mentioned in the ndswrapper guide, I tried in vain if it makes any difference, if I remove ssb from that list. Nope still no joy.

---

### Post by wildmanne39 on 2012-04-28
Hi, if you need help after you get the new version installed then post back.
Thanks

---

### Post by protocoder on 2012-04-30
Thank you very much wildmanne39. You have been awesome. I will probably seek help. With my old laptop configuration, I probably look for less resource hungry os. I will let you know what I tried and how it went. Cheers.

---

