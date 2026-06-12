---
title: "Wireless Trouble :("
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by kcaz on 2009-06-27
OK so I'm running Ubuntu on a mac, I have 2 partitions, the mac and ubuntu. The ubuntu is actually just windows from boot camp, and then I installed Ubuntu over Windows.

Anyways the wireless internet isen't working. I think I've heard of some of these problems before, but I was just wondering what the general consenses is.

I have a modem, and on other computers and the mac partition of my computer the internet works fine, but ubuntu wont reconize it. When I stick an eithernet cable from the modem to the computer however the internet works fine.

Any suggestions?
~Kcaz

---

### Post by tlois on 2009-06-27
Have you done all the updates?  Maybe also look on Apple section of this forum too and give them your exact Mac info.

---

### Post by Ayuthia on 2009-06-27
If I recall correctly, Apple uses a Broadcom wireless card.  However, I am not quite sure if I am sure if I follow how you installed Ubuntu.  Are you saying that you are using Wubi to install Ubuntu in Windows that is running through Boot Camp?  

Regardless, it would probably be helpful to see what Ubuntu shows when you go into the Terminal and type:
```
lspci -nn
```If it shows a Broadcom 4318 card, you should be able to enable it either through System->Administration->Hardware Drivers or you can install it through Synaptic by installing b43-fwcutter.  If you want to do it the Terminal way:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```Just make sure that the cable from the modem is hooked up to the computer for this because the system will need to download a firmware file to make your wireless card work in Linux.

---

### Post by kcaz on 2009-06-27
What I did is this. I had been dual booting Windows XP and Mac and decided install Ubuntu over the Windows XP Partition. It wasn't wubi. It was like if you had an XP computer and replaced XP with Ubuntu.

The wireless card is Broadcom bcm4328. It says that the card is activated but not in use. I can't seem to get any type of wireless signal. I posted in the Apple User's thread here @:[http://ubuntuforums.org/showthread.php?p=7529122#post7529122](http://ubuntuforums.org/showthread.php?p=7529122#post7529122)

Thanks in advance,
-kcaz

---

### Post by tlois on 2009-06-27
Try enabling the driver.  Go to System, Admin, Hardware drive and make sure it is enabled.

---

### Post by kcaz on 2009-06-27
I believe it is. It says "Activated but not in use"

---

### Post by Ayuthia on 2009-06-27
Please try the following from the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```It could be that the b43 or ssb module is currently loaded and is preventing the wl (Broadcom STA) module to work.  These commands will remove the possible conflicting modules and then load the wl module.  Then it will check for wireless sites.

---

