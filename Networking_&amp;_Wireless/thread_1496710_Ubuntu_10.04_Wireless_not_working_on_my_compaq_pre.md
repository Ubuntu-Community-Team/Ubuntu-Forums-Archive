---
title: "Ubuntu 10.04 Wireless not working on my compaq presario CQ60 211DX"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by tacotime on 2010-05-29
Hey guys,
On friday (5-28-10) I installed ubuntu 10.04 Lucid, and everything was just peachy, wireless worked and everything. 
Today (saturday 5-29-10) booted up to find that my wireless wouldn't work. I plugged up to Ethernet and that worked fine, i updated and everything, still no wireless. I google the problem, and have tried everything under the sun to get this darn wireless card to work. I'm pretty sure it's atheros but i am not sure. 
when i go to system -> admin -> hardware and drivers nothing shows up. 
i have no clue what to do. 
Can someone help me?!?!
Thanks in adcance! :) 
-Tacotime

---

### Post by awregan on 2010-06-09
> **tacotime said:**
> Hey guys,
On friday (5-28-10) I installed ubuntu 10.04 Lucid, and everything was just peachy, wireless worked and everything. 
Today (saturday 5-29-10) booted up to find that my wireless wouldn't work. I plugged up to Ethernet and that worked fine, i updated and everything, still no wireless. I google the problem, and have tried everything under the sun to get this darn wireless card to work. I'm pretty sure it's atheros but i am not sure. 
when i go to system -> admin -> hardware and drivers nothing shows up. 
i have no clue what to do. 
Can someone help me?!?!
Thanks in adcance! :) 
-Tacotime

Same problem here. Using internet from windows

---

### Post by Oscar07202 on 2010-06-14
i had a problem like this in ubuntu 8.04, this was a while ago but here is a link that should probably help you. what i basically had to do  was disable the propiertary drivers of the wifi card and install new drivers.


check this link:
[http://ubuntuforums.org/archive/index.php/t-766169.html](http://ubuntuforums.org/archive/index.php/t-766169.html)


these are probably the steps found from the lnk above:

"apche93
August 6th, 2008, 11:17 PM

Here is another method of installing ur driver:

First download the driver from here:


[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

Then complete these steps:
1. Remove any ath_pci driver from the RESTRICTED DRIVERS MANAGER
2. Make sure that you have build-essential package installed, if not, fire up a terminal and type in sudo apt-get install build-essential
3. Navigate your way in Terminal to the directory where you downloaded the archive for the driver
4. Type these to decompress the archive tar xfz madwifi-ng-r2756+ar5007.tar.gz and cd madwifi-ng-r2756+ar5007
5. Type make to compile
6. Type sudo make install to install the driver
7. Type sudo modprobe ath_pci to insert the driver as a kernel module
8. Restart by typing sudo reboot
9. If all goes well, after you restarted, you will find wireless networks in your Network Manager


OR,

u can just visit this topic where i kinda stole the information from:
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)


Hope that helps!(apache93)"



#########################################you should check the link above before you start following the steps made by apache93 as they use admin(root) rights and could possibly negatively effect your pc###################################################################3

---

