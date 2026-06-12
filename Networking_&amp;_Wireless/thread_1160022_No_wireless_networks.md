---
title: "No wireless networks"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by jonnyl888 on 2009-05-15
Everytime i install ubuntu 9.04 no wireless networks ever show up. Iv reinstalled it quite a few times bevause of partition errors, and some of the times iv used ubuntu, it firstly doesnt show any networks and after a few reboots a largee number of networks suddenly appears when i click the network icon. Now iv finally gotten ubuntu to install properly there are no networks. I have a broadcom card, which seems to automatically install thw driver when i installed linux. Is there a way to reset the card through the terminal or something?

Sorry about the spelling mistakes, im typing from my ipod touch

---

### Post by Kevbert on 2009-05-15
Please go to Applications-Accessories-Terminal and type
```
lspci
```
to list all pci connected devices. If you look for the line(s) with 'Network Controller', this should include your Broadcom card. Please post back model and revision.
It may also be worth trying the command
```
iwlist scanning
```
to see if there are any wireless networks available.

---

### Post by bluestreek on 2009-05-15
Please do:

sudo apt-get install linux-backports-modules-jaunty

and then as long as you are not relying on 3G broadband modem.

sudo apt-get install wicd

Reboot and see if you can see any networks. Network manager is a little bit messed up at the moment.

---

### Post by jonnyl888 on 2009-05-15
> **Kevbert said:**
> Please go to Applications-Accessories-Terminal and type
```
lspci
```
to list all pci connected devices. If you look for the line(s) with 'Network Controller', this should include your Broadcom card. Please post back model and revision.
It may also be worth trying the command
```
iwlist scanning
```
to see if there are any wireless networks available.

It says broadcom corp BCM4328 802.11a/b/g/n

I tried the iwlist scanning and it sasys "interface does not support scanning"
 for lo, eth0 and pan0

Also i tried installing backports and wicd but it said that it couldnt find the packages.

---

### Post by superprash2003 on 2009-05-15
add a sudo , type sudo iwlist scanning and post the full output

---

### Post by Kevbert on 2009-05-15
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1134631") (especially post #5).

---

### Post by jonnyl888 on 2009-05-15
> **Kevbert said:**
> Please take a look at [[COLOR=Red]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1134631") (especially post #5).

IT WORKED! finally, the first method on the page was the one that worked for me.

Thanks

---

