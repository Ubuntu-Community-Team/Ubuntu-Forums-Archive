---
title: "Zonet zew2502 help"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by tonalvoltage on 2010-03-05
Hello all,

I'm brand new to Linux and Ubuntu so please bear with me!

I just installed Ubuntu 9.10 and am trying to get my Zonet zew2502 wireless usb to work right.  So far I have

-installed ndiswrapper from the Synaptic Package manager
-copied the netMw225.inf and MRVW225.sys to my download directory

At first, when I ran ndiswrapper -l I got NOTHING back.  When I plugged in the zonet to usb and ran lsusb I got 

```

Bus 001 Device 009: ID 1286:1fab Marvell Semiconductor, Inc.

```This doesn't appear on the list when the zonet is not plugged in so I can only assume that this is it.  Anyhow, I did a sudo ndiswrapper -i netMw225.inf and everything seemed to install, so now when I do ndiswrapper -l I get:
```

netmw225 : driver installed
     device (1286:1FAB) present

```But I'm not quite sure where to go from here.  I don't think a GUI front end for ndiswrapper got installed to help me search for and connect to wireless networks.  Any help as to what I should do next would be greatly appreciated!

EDIT: The computer also has a PCI ethernet card (wired) that does work correctly, but I have the cable unplugged while debugging the wireless card.  Could this be causing a conflict?

Thanks,
Evan

---

### Post by chili555 on 2010-03-05
Please run:```
sudo modprobe ndiswrapper
iwconfig
```Do you have a wireless interface, wlan0, perhaps? If so, please click the Network Manager icon at the top right of your desktop and see if you see your network. Click it and see if you connect. Please be sure the ethernet cable is detached while try to get the wireless connected.

The icon looks like two computer monitors with an **[COLOR="Red"]X[/COLOR]** over them.

---

### Post by tonalvoltage on 2010-03-05
Thank you, that actually did it!

Before, I did have a graphic (though it wasn't as you described... more like several dots) but all it showed before was "Wired Network- disconnected" with no other options.

After running the commands you suggested and clicking on it, I had the options for wireless networks.  So I guess my problem was that ndiswrapper wasn't added to the kernel?  Shouldn't it have automatically gotten added when I installed it via the Synaptic manager?

---

### Post by chili555 on 2010-03-05
I think you meant that the module should be loading automagically on boot, rather than modprobbed every day while we make the coffee. Did you do?```
sudo ndiswrapper -m
```From *man ndiswrapper*:> -m     writes  an alias for wlan0 (default wireless device) into module
              configuration file so that ndiswrapper kernel module  is  loaded
              automatically when this interface is used.If you don't remember, it does no harm to repeat it now. If that doesn't do it, please post back.

---

### Post by tonalvoltage on 2010-03-08
I just rebooted my machine today and had to re-run:

```

sudo modprobe ndiswrapper
iwconfig

```

I did run
```

sudo ndiswrapper -m

```

 before the reboot, but the network card wasn't available at start up.  Any idea why?

---

### Post by chili555 on 2010-03-08
Please try:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```Reboot and let us know if it's fixed.

---

### Post by tonalvoltage on 2010-03-09
Thank you, that did it.

---

### Post by 96Beatz! on 2011-10-19
Hello!  I too have the same problem. Did all that was done on this thread, and still cannot see my wireless USB zonenet 2502.  I have the exact setup but i'm running back track 5r1. 

i'll try and post a screen shot of what I got. Please help. Thanks!  and yes i know this thread is old! LOL!

edit: i'm also running it on VMware player 4.0 32bit. so i'm using the 32 bit vista driver.. will try the XP drivers also.

---

### Post by 96Beatz! on 2011-10-19
Also another screen shot showing Me installing the other driver also.  Still Nothing..

---

### Post by 96Beatz! on 2011-10-19
Fix it!  Changed USB ports.  diabled wired ethernet. reinstalled drivers with xp drivers.  works flawless now. thanks!?!  LOL!

---

### Post by rmcellig on 2012-08-07
I am having problems getting my Zonet device to connect. I can see it in my Network menu but when I try to connect, the network icon keeps spinning. When I use the Broadcom internal wireless device on my laptop, it connects right away. What should I do and what should I post back to this thread so that I can get my wireless device to work?

---

