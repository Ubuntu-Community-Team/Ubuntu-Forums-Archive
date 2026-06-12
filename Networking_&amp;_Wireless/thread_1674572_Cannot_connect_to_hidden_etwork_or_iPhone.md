---
title: "Cannot connect to hidden etwork or iPhone"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by dark fader on 2011-01-24
This is incredibly frustrating and I'm spending loads of time on it. If anyone can help I'd be over the moon.

I have a Lenovo Thinkpad T410 and I've tried installing Ubuntu 10.04 and 10.10. Although the on-board wireless was detected and connects nicely to my home network (WPA), it simply can't connect to my work networks - a number of hidden WPA networks. Ubuntu repeatedly asks for the passphrase, which is correct. Windows was able to connect fine before I removed the partition.

At one point I tried swapping Network Manager for Wicd, which told me it was failing at the 'obtaining IP address' stage.

It also only very rarely connects to my iPhone, which is running MyWi. It cannot seem to connect via USB, bluetooth occasionally works once but then requires a reset of both Ubuntu and the iPhone and a WiFi connection does the same thing as attempting to connect to a hidden WPA.

I'm currently running both 32 and 64 bit versions of 10.10 on different partitions. (The 64 bit version is actually a Mint distro but I understand the differences are pretty minor). I experienced the same problems on 10.04 64 as well.

So far I've tried:

 - ndiswrapper. It didn't seem to make a difference.
 - Updating the firmware drivers to the latest released for the card. Again, no difference.
 - Getting a USB wireless card. (Edimax nano). I've attempted to use ndiswrapper, but it's now broken on both partitions. On the 64 bit version, the GUI just gives a blank window which goes grey. The command line version hangs if I ask for a list of installed drivers. The 32 bit version gives blank error messages on the GUI. I've tried uninstalling and purging with aptitude to no avail.
 - Compiling the driver from source. Only the 32bit version is available. It works - for my home connection - but again fails on hidden networks. Slightly better on the iPhone - it very rarely connects to an unsecured ad-hoc network, completely fails on WEP.

I am beginning to tear my hair out now. I just want to be able to connect to wireless at work and tether my iPhone when I'm out and about. Of course, Windows did all this just fine.

I would even be happy enough if I could tether my phone with USB and share my phone's wireless connectivity. (It connects to the work network just fine.)

Any ideas anyone?

---

### Post by regala on 2011-01-24
> **dark fader said:**
> This is incredibly frustrating and I'm spending loads of time on it. If anyone can help I'd be over the moon.

> 
I have a Lenovo Thinkpad T410 and I've tried installing Ubuntu 10.04 and 10.10. Although the on-board wireless was detected and connects nicely to my home network (WPA), it simply can't connect to my work networks - a number of hidden WPA networks. Ubuntu repeatedly asks for the passphrase, which is correct. Windows was able to connect fine before I removed the partition.


what is the Wifi chipset ? (I could find by browsing I guess, but actually YOU can give us the best info on that, by running lspci)

> 
At one point I tried swapping Network Manager for Wicd, which told me it was failing at the 'obtaining IP address' stage.


hum, dhcp failure, maybe a driver problem, or a faulty dhcp (causing a NAK despite the dhcp offer to the client)

> 
It also only very rarely connects to my iPhone, which is running MyWi. It cannot seem to connect via USB, bluetooth occasionally works once but then requires a reset of both Ubuntu and the iPhone and a WiFi connection does the same thing as attempting to connect to a hidden WPA.


I'm currently running both 32 and 64 bit versions of 10.10 on different partitions. (The 64 bit version is actually a Mint distro but I understand the differences are pretty minor). I experienced the same problems on 10.04 64 as well.

So far I've tried:

 - ndiswrapper. It didn't seem to make a difference.


don't EVER use that crap again. Ubuntu docs citing this "tool" are just out of date about a century.

> 
 - Updating the firmware drivers to the latest released for the card. Again, no difference.

 - Getting a USB wireless card. (Edimax nano). I've attempted to use ndiswrapper, but it's now broken on both partitions. On the 64 bit version, the GUI just gives a blank window which goes grey. The command line version hangs if I ask for a list of installed drivers. The 32 bit version gives blank error messages on the GUI. I've tried uninstalling and purging with aptitude to no avail.


well you see, if you want to replace a faulty piece of hardware, or use something else to substitute its functions, try and choose something that is known to work on Ubuntu :)

> 
 - Compiling the driver from source. Only the 32bit version is available. It works - for my home connection - but again fails on hidden networks. Slightly better on the iPhone - it very rarely connects to an unsecured ad-hoc network, completely fails on WEP.


I don't understand the iphone part, you changed the IPhone driver ????

> 
I am beginning to tear my hair out now. I just want to be able to connect to wireless at work and tether my iPhone when I'm out and about. Of course, Windows did all this just fine.


well, go for it !!

br,

---

### Post by dark fader on 2011-01-24
> **regala said:**
> what is the Wifi chipset ? (I could find by browsing I guess, but actually YOU can give us the best info on that, by running lspci)



Thanks for the reply! :)

On-borad hardware is:

Intel Corporation Centrino Ultimate-N 6300 (rev 35)
driver=iwlagn driverversion=2.6.35-22-generic firmware=9.221.4.1 build 25532

USB adapter is:

Edimax EW-7811Un
rtl8192CU_linux_v2.0.939.20100726 compiled to 8192cu.ko

> 

hum, dhcp failure, maybe a driver problem, or a faulty dhcp (causing a NAK despite the dhcp offer to the client)


What can I do to fix it if it's any of those? How can I tell exactly what's failing? Network issues aren't my strong suit unfortunately.

> 
don't EVER use that crap again. Ubuntu docs citing this "tool" are just out of date about a century.


It does seem flaky at best. at one point it was causing the OS to crash on opening after suspend... A problem which cleared up when I removed it with Aptitude.

> 

well you see, if you want to replace a faulty piece of hardware, or use something else to substitute its functions, try and choose something that is known to work on Ubuntu :)



I didn't buy it in a vacuum, I found many posts and reviews stating that it worked 'perfectly' after compiling the drivers. Admittedly I wasn't aware of the lack of 64 bit drivers (I live and learn) and I couldn't find anyone connecting to ad-hoc networks or hidden networks... But is that specific information available for any other hardware?

> 

I don't understand the iphone part, you changed the IPhone driver ????



I'm using MyWi, an app from Cydia which can set the iPhone up to be tethered by Bluetooth, USB or Wifi (through an ad-hoc network.) Other OSes like Windows and OSX seem to be able to work with it in all modes I've tested so far. Ubuntu is failing on each:

USB is simply not picked up. Is there a network driver for USB that I can install?

Bluetooth seems to connect at first, but often doesn't see the internet - even though the phone can access web pages. If disconnected both Ubuntu and the iPhone need to be reset before it can work again - re-connection seems to cycle up and down (in Blueman manager) and eventually fail.
I can occasionally connect to the iPhone ad-hoc network with the new hardware, but connection is inconsistent and only works with no security enabled. Not ideal.
On the old inbuilt hardware, it seems to connect to the ad-hoc network if there isn't any security, but it can't see the internet.

I have another (home) lap-top which exhibits the same issues connecting to the iPhone under Ubuntu 10.10 32.

I'm beginning to think the problem may not be the drivers or the hardware, but the OS. If so, I'm hopeful of a resolution to the problem - but it's beyond me. If you can suggest any avenues for exploration I would be most grateful.

---

### Post by dark fader on 2011-01-25
Can anyone help me progress with this? How do I diagnose exactly what's wrong?

---

