---
title: "Belkin Play Wireless N+N300 Dual Band USB Adapter (F7D4101 v1)"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by sherwindm on 2010-05-25
Hi! I recently got a usb wireless adapter its the one posted above. I havent seen any threads posted here or anywhere for that matter so I'm starting one. I googled it without any success since I think that this adapter is relatively new at this time.

Tried getting it to work in **Ubuntu 10.04** with ndiswrapper. Blacklisted all the broadcom drivers and installed the XP driver from the CD(**bcmwlhigh5**). It says diver is installed and device is present however the network manager applet does not show that its there, only gives me the wired connection. 

Anybody else having the same issue? Just wondering if anybody could shed some light on it all for me. If any more information is needed to help please prompt me.

Thanks in advance.

---

### Post by sherwindm on 2010-05-29
bump!

---

### Post by sherwindm on 2010-05-31
Seems that no one has the same adapter:(..using Belkin Basic with rtl8192su chip atm working fine with windows driver using ndiswrapper GUI (ndgtk).:)

---

### Post by erwi on 2010-06-14
Same problem here. This is the reward for investing in the most advanced wifi dongle in the shop. :(


The chip on the device is Broadcom bmc4323 (I opened the flimsy plastic case on the dongle). I tried the b43-fwcutter, but couldn't get any drivers to work.

when trying to extract the winXP firmware from the driver on the CD, bcmwlhigh5.sys, I get the error: "Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum b770039886598aab7cf5eaeec2409e31."

---

### Post by Another Sawyer on 2010-07-13
I've got the same issue, same adapter, and Ubuntu 10.04.  I am totally new to Ubuntu (2 days experience now!) and would love to see a resolution to this problem.  I'll keep my eyes pealed.

---

### Post by binglissa on 2010-10-08
Nailed it using the Belkin N300 and a netgear wndr3700 router. 

From the installation CD for the N300 nab the 3 XP files and put them in a folder on the home folder.

net8192su.cat
net8192su.inf
rtl8192su.sys

install and open the ndiswrapper tool
find the net8192su.inf file and install
plug in the usb wireless n300 and setup your wireless settings.

Had some issues initially with slow and intermittent service but turned to be that usb port was too close to other wires. moved it away to another usb port and it works rapido!!

---

### Post by sherwindm on 2010-11-29
> **binglissa said:**
> Nailed it using the Belkin N300 and a netgear wndr3700 router. 
 
From the installation CD for the N300 nab the 3 XP files and put them in a folder on the home folder.
 
net8192su.cat
net8192su.inf
rtl8192su.sys
 
install and open the ndiswrapper tool
find the net8192su.inf file and install
plug in the usb wireless n300 and setup your wireless settings.
 
Had some issues initially with slow and intermittent service but turned to be that usb port was too close to other wires. moved it away to another usb port and it works rapido!!
 
Nice! :D
Although I havent tried this yet. I have been on and off with Linux, its a love hate relationship. :p Thanks for your solution.

---

### Post by sherwindm on 2010-12-01
I have done the same thing and It did not work before, probably they did some updates with ndis or something. Problem now is that the network keeps kicking me off, it does not let me connect. I am using WPA**+**WPA2 but when I use WEP, or no encryption, I don't have this problem..  Could it be my router or the USB adapter that's giving me the problem?

---

### Post by sherwindm on 2010-12-01
Just got it working apparently it only works with WPA1, WEP, No encryption and not with WPA2 or WPA+WPA2. 

Just found a post discussing about the issue but this was a couple of years ago not sure If they already made changes since then.

 [http://ubuntuforums.org/showthread.php?t=660961](http://ubuntuforums.org/showthread.php?t=660961)

If anybody has a solution on connecting with WPA2 please let me know.

---

### Post by Q-ro on 2011-02-06
> **binglissa said:**
> Nailed it using the Belkin N300 and a netgear wndr3700 router. 

From the installation CD for the N300 nab the 3 XP files and put them in a folder on the home folder.

net8192su.cat
net8192su.inf
rtl8192su.sys

install and open the ndiswrapper tool
find the net8192su.inf file and install
plug in the usb wireless n300 and setup your wireless settings.

Had some issues initially with slow and intermittent service but turned to be that usb port was too close to other wires. moved it away to another usb port and it works rapido!!

i had the same adapter (Belinkin F7D4101v1) but my cd have different files for the XP Folder
 
```
bcmh43xx.cat
bcmh43xx64.cat
bcmwlhigh5.inf
bcmwlhigh5.sys
bcmwlhigh564.sys
```

used the ndiswrapper on them but it didn't work, my wifi is useless, i was wondering if anyone had the same cd y do, or if there is any way to fin the drivers you mention, 'cause i searched on belkin and F7D4101v1 trows no result 

Thanks in advance.

---

### Post by t6633 on 2011-05-15
Worked just as described. Belkin N300 micro was up and running in 3 minutes.
Thanks.

---

### Post by geek.de.nz on 2012-05-30
Does this work without ndiswrapper? I'm looking at buying this adapter because it seems promising but a requirement for me is that it works in Ubuntu out of the box, otherwise it's a waste of time.

Thanks for any input!

---

### Post by Davidgo on 2012-08-11
> **geek.de.nz said:**
> Does this work without ndiswrapper? I'm looking at buying this adapter because it seems promising but a requirement for me is that it works in Ubuntu out of the box, otherwise it's a waste of time.

Thanks for any input!

Definately did not work "out of the box" (or at all) on Ubuntu 12.04 - 64bit for me.  In fact, its going back to the supplier.

---

