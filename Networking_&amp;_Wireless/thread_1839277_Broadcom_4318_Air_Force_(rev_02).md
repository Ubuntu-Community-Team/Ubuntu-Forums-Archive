---
title: "Broadcom 4318 Air Force (rev 02)"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by Thornberry2000 on 2011-09-05
Dear Sirs/Madams

Please could someone help me, i have spent the last few nights reading and trying to fix a problem Im sure could be fixed within a matter of minutes, however being an absolute beginner i don't know what to do:

I have currently installed ubuntu 11.04 natty (working under classic due to hardware on an acer aspire 3000 laptop (formerly xp). It has a broadcom 4318 airforce (rev .02).

I have tried installing all the packages in relation to it from synaptic package manager, however doing this does not show the option of enable wireless under the network manager.

I tried the ndiswrapper and downloaded the broadcom driver from the acer website and then installed the package.  This shows the option of 'enable wireless' under the network manager however does not show me any wireless connections in the area.

I really need someones help as this has been driving me insane.  I am able to access a connection via a wired connection but this laptop is for my dad and the connection point isn't really in a viable place for this.

I would greatly appreciate someone taking me a newbie through the whole process of trying to fix this.

Thanking you for your time.

Tom :(

---

### Post by praseodym on 2011-09-05
Hi,

for this device the firmware has to be installed. Remove ndiswrapper completely for that before (copy/paste the commands, wired connection needed):

```
sudo modprobe -rf ndiswrapper b43
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo modprobe -v b43
sudo depmod -a
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo service network-manager restart
```

---

### Post by Thornberry2000 on 2011-09-05
I will try it tonight. Thank you, lets hope it works, because my brain has nothing left in trying to work it out.

I will let you know the results.

Thank you praseodym.

Tom

---

