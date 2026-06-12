---
title: "Wireless Problems"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by dsjas297 on 2006-01-19
I have a wireless card on my comp with the ralink rt61 chipset. Using ndiswrapper, I loaded drivers for the card. I also used "ndiswrapper -m" to have the drivers load at boot time. Still, Ubuntu does not recognize my adapter and I did not find it in the menu for configuring network devices. I then edited /etc/modules to include ndiswrapper. Still no luck.

Any help on how to fix this is appreciated.

---

### Post by healychan on 2006-01-19
Have you try "sudo modprobe ndiswrapper" ??

---

### Post by dsjas297 on 2006-01-19
Tried what you said and it still did not appear in the network configuration menu. I then used "lsmod" to list all kernel modules and found that ndiswrapper was loaded.

(Note: There is a driver available for my chipset here: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

However, I was not able to get it working. Part of the problem might be that it was made for RedHat based systems but I am not sure.)

---

### Post by h0me5k1n on 2006-02-07
I've got an 'rt61' card and have got it recognised by the drivers from ralink.

Here's what I have so far:
 
I installed the kernel headers:
apt-get install linux-headers-2.6.12-10-386 build-essential gcc-3.4

got the drivers:
wget [http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz)

extract them:
tar -xvzf 2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz

Change to the (extracted) Module directory:
cd RT61_Linux_STA_Drv1.0.3.0_200512230/Module

Use the 2.6 kernel makefile:
cp Makefile.6  ./Makefile

sudo make all

sudo insmod rt61.ko
(rt61 now shows up in lsmod)

sudo ifconfig ra0 YOUR_IP up

At this point ra0 shows up in ifconfig and I can see my access point when I do 'iwlist ra0 scan'.  

1) The problem I have is that the module doesn't start automatically if the system is rebooted - how do I do this?
2) how do I set up WPA/WEP with this?  The readme file with the driver mentions a rt61sta.dat file but I'm not sure where to put it? It doesn't seem to recognise me trying to set it up using iwconfig and, although it mentions a /etc/Wireless/ directory, I can't seem to get it to work.  It doesn't automatically create the /etc/Wireless directory either (although on one attempt at installing the drivers it did create the directory and put the rt2561.bin, rt2561s.bin, rt2661.bin and rt61sta.dat in it for me)

---

### Post by h0me5k1n on 2006-02-15
UPDATE:

I have the RT61 drivers from ralink installed and working fine using WEP now but I still haven't worked out how to load the module at startup.

---

### Post by judgekaster on 2006-02-19
[QUOTE=h0me5k1n]UPDATE:

I have the RT61 drivers from ralink installed and working fine using WEP now but I still haven't worked out how to load the module at startup.[/QUOTE]

Glad to hear you got the RT61 driver running. I have some positive and negative experiences with it as well.

Positive: I got the rt61 driver loading at startup. I copied the rt61.ko file to /lib/modules/{kernel-version}/kernel/drivers/net/ and issued a depmod command.

Positive: I edited the rt61sta.dat file in /etc/Wireless/RT61/ with the necessary information to access my Open/WEP access point and issued a "sudo ifconfig ra0 {IP address} up"

Negative: I cannot use the network-admin graphical interface to configure ra0 without causing instability to the network. "iwconfig" and "ifconfig" would hang afterwards. Relatedly, the startup script to start the network, i.e. /etc/init.d/networking" will hang at boot time. :cry: 

I hope you can share more of your experiences in getting to use the rt61 driver.

Cheers! :-D

---

### Post by melquiades on 2006-03-15
I have an RT61 adapter and though I have successfully installed it and used it to access the net, it has some serious problems too. Like, ubuntu would get stuck at th e "Configuring network interfaces..." portion of the bootup. If I press 'ctrl+c', the boot 
would proceed but would hang during the start of the GUI session. All of these problems would disappear if I remove rt61.ko from the /lib/..../driver/net directory. So now, if I want to use wifi, I have to copy the driver to the /lib..../driver/net directory, load it, then run dhclient to configure the interface. Then I have to remove rt61.ko before I powerdowm my laptop.

---

