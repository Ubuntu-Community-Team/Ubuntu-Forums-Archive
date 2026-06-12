---
title: "Wireless Issues (complete newbie here)..trying Wireless Network Drivers etc..."
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by UbuNoob001 on 2010-01-22
HEY !   So im a complete newbie (one week...and this is my first post)to the Linux world( and a novice windows user). I feel so close to getting wireless working just cant get to the last step! 

So, im trying to get my wireless to work. So i should give some info....

I have a Dell Inspiron 1545 (dual boot with Vista Home Premium)
Hardware: BCM 4312 802.11b/g    
                  Broadcom and I have pci_14e4:4315      (i was told this should help) 

I have WICD on Ubuntu 9.10 cause i was told that might fix my problem (it didnt).

And via "Ubuntu Software Center" I downloaded : Device Manager and Wireless Network Drivers.

Wireless Network Drivers ( i guess this is GUI Ndiswr. ?) says that my first step needs to be to Install driver by "select INF file". I looked on sourceforge for a driver for my chipset and i couldn't find it. 

Anyway, does anyone know 1. Where i can find the right driver? and 2. how to get to the INF file (whatever that is :-) so that I can get wireless working?

 MANY MANY MANY thanks:D. ( i just learned words like chipset etc today so assume i know nothing lol) 

 Brad

---

### Post by bkratz on 2010-01-22
You might want to go through this thread

[http://ubuntuforums.org/showthread.php?t=1378830&highlight=14e4:4315](http://ubuntuforums.org/showthread.php?t=1378830&highlight=14e4:4315)

---

### Post by UbuNoob001 on 2010-01-22
Had a look through that post, however can't make too much of it as im new to all the Linux jargon. However, it seems like the main issue is 1. finding the driver, and 2. finding the INF (?) file so that Wireless Network Drivers can install it(?). 

Not sure if this helps but my wired connection works fine. Under WICD > Preferences>General Settings>Newtwork Interfaces, the "wireless interface" has nothing written next to it. The wired (working connection) says "eth0".

***Also, earlier i found a driver put out by Broadcom supposed to work with linux: " 802.11 Linux STA Driver", however it cam in the form : hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz 
and i wasnt sure if this was something that i could get an INF file from to use with Wireless Network Drivers.

---

### Post by UbuNoob001 on 2010-05-03
Sorry guys had forgotten to mark this as solved. Simply had to download restricted STA driver.

---

