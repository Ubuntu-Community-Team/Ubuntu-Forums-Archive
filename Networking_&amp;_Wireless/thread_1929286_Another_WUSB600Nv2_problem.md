---
title: "Another WUSB600Nv2 problem"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by fubofo on 2012-02-21
Hi guys,

I have a problem with my **WUSB600Nv2** usb adapter.
I am running **Ubuntu 11.10 64bit**, current kernel **3.1.4-030104-generic**, GNOME 3.

I have downloaded and compiled the **RaLink 2.5.0.0** drivers successfully. The **rt3572sta module is installed** fine and I can actually scan networks using network-manager.

I have 2 issues:
- First issue comes when trying to connect to my WPA2PSK network. It just keeps _asking for the password but will not accept_.
- Second when I _cancel the password prompt my entire desktop freezes_....I can move the mouse but nothing else works, not even CTRL+ALT+F1 so I have to switch off the power to my machine :!: .

Strange thing is, this adapter works absolutely flawlessly in Fedora 16 - scans and connects to all networks regardless of security and LED works.

**network-info.sh** attached (seems to be too much info to post in code tags)

---

### Post by UltimateCat on 2012-02-21
I have the WUSB54GC and the rt8168 driver and long story short...until I 
```
blacklisted the rt8169
```
And shut down and then rebooted I could not get online.

Been online since and doing ok.

Not sure how to fix your desktop from freezin I'm sorry-

---

### Post by fubofo on 2012-02-21
Cheers for that UltimateCat, though no other modules seem to be loading - only the rt3572sta.

There is some advice about blacklisting rt2800 but they never seem to get loaded on my system. I think everything looks like it could work, if only I an get over the authentication issue...?

---

### Post by fubofo on 2012-02-22
Managed to get it working again in Ubuntu 11.10 !! :D

I think it seemed to be a combination of details here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85")

...along with bits from here: [http://ubuntuforums.org/showthread.php?t=1690402]("http://ubuntuforums.org/showthread.php?t=1690402")

I say a combination because emory's (post 85) instruction didn't seem to work before. I have a feeling the missing piece was:

```
Create file /etc/udev/rules.d/10-wusb600nv2.rules
Add the following lines:
Code:
# UDEV-Rule for wusb-600Nv2 ID 1737:0079
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0079", RUN+="/sbin/modprobe rt3572sta"
Create the file /etc/modprobe.d/rt3572sta.conf
Add the following line:
Code:
install rt3572sta modprobe --ignore-install rt3572sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id
Blacklist other drivers
Open /etc/modprobe.d/blacklist.conf
Code:
sudo gedit /etc/modprobe.d/blacklist.conf
Put the following lines at the end of the file:

Code:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870
Reboot
```

Gonna go ahead and -
**2.4.0.1**
make uninstall
reboot

**2.5.0.0**
sudo su
make clean
make
make install
reboot

...just to see if the new driver will work because it will build an install properly..  (let's hope nothing breaks and I can get 2.4.0.1 working again if 2.5.0.0 doesn't work lol)

---

### Post by fubofo on 2012-02-22
UPDATE

OK so there is definitely an issue with 2.5.0.0 driver, it didn't want to connect like before. Reinstalled 2.4.0.1 and everything works fine again. :)

**2.5.0.0**
_works_
-makes / builds
-installs without errors
-scans networks (ALL)
-connects to unsecured networks

_doesn't work_
-connect to WEP / WPA2PSK secured networks (constantly asks for authentication and on my machine causes complete PC freeze when cancelling authentication prompt)

[B]Ubuntu 11.10 64bit
3.1.4-030104-generic[/B]
*full system info attached from network-info.sh*

---

### Post by fubofo on 2012-02-23
OK so just to provide a fool-proof step by step guide for future reference here is what I did to have this WUSB600Nv2 working.
That is:
- configure/build the module for your current kernel
- install the module
- have the machine auto recognise the adapter and connect to wireless networks

_Please note_: You can follow joho500 post ([here]("http://ubuntuforums.org/showpost.php?p=10470616&postcount=1")) and simply substitute downloading the RaLink driver for emory's driver ([here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/+attachment/1649708/+files/RT3572-WUSB600Nv2-2.4.0.1-kernel-2.6.35.tgz")) . joho500 post contains a bit more information than I do, relating to configuring the module for specific settings for this device which I intentionally left out here because emory has already changed the config files in his pre-made package - 

_Second note_: if you already know about making modules just go to the bottom of this post


--------------------------------------------------------------------------------------------------
UNPLUG THE ADAPTER

[SIZE="1"]*[COLOR="DimGray"]taken from [http://ubuntuforums.org/showpost.php?p=10470616&postcount=1](http://ubuntuforums.org/showpost.php?p=10470616&postcount=1)[/COLOR]*[/SIZE]

[SIZE="2"]**1**) Check your device to verify it's the WUSB600N version 2[/SIZE]

```
lsusb |grep 1737
```

This should return:

```
...: ID 1737:0079 Linksys
```

[SIZE="2"]**2**) Download the 2.4.0.1 driver from emory's post in Launchpad.[/SIZE]
([direct link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/+attachment/1649708/+files/RT3572-WUSB600Nv2-2.4.0.1-kernel-2.6.35.tgz"))
[COLOR="DimGray"]For some reason the 2.5.0.0 (latest) driver from RaLink will not work with secured networks, even though I have managed to successfully build and install and recognise and scan without any problems *(might look into this later, though not sure if 2.5.0.0 provides any improvements)*[/COLOR]

[SIZE="1"]*[COLOR="DimGray"]taken from ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85))[/COLOR]*[/SIZE]

[SIZE="2"]**3**) Extract the archive[/SIZE] (it will unpack as ./2010_0709_RT3572_Linux_STA_v2.4.0.1 so extract this where you really want it)
[COLOR="DimGray"][I]I have a folder in my home directory called **build** , this is where I keep all my custom builds [kernels, drivers/modules, packages, etc.
_I renamed the directory 'WUSB600Nv2-2401' and put it in ~/build/_ ][/I][/COLOR]

[SIZE="2"]**4**) cd to the directory you just extracted[/SIZE]
[COLOR="DimGray"]*I ran, in terminal, _cd ~/build/WUSB600Nv2-2401/_ *[/COLOR]

[SIZE="2"]**5**) Clean up any precompiled files, build the module specific for you current kernel, install the module[/SIZE]

[SIZE="1"]**run as superuser for the next few parts**[/SIZE]
```
sudo su
```

[SIZE="1"]**clean up**[/SIZE]
```
make clean
```

[SIZE="1"]**compensate for idiocy as a work-around Ralink's broken clean target**[/SIZE]
```
find . -name "*.*o" | xargs rm
```

[SIZE="1"]**build the module for your current kernel**[/SIZE]
```
make
```
[COLOR="DimGray"]this should compile without any errors[/COLOR]

[SIZE="1"]**install the module**[/SIZE]
```
make install
```
[COLOR="DimGray"]this should install without any errors[/COLOR]

[SIZE="1"]*[COLOR="DimGray"]taken from [http://ubuntuforums.org/showpost.php?p=10470616&postcount=1](http://ubuntuforums.org/showpost.php?p=10470616&postcount=1)[/COLOR]*[/SIZE]

[SIZE="2"]**6**) Have the module auto loaded:[/SIZE]

[SIZE="1"]**Create file /etc/udev/rules.d/10-wusb600nv2.rules**[/SIZE]
```
gedit /etc/udev/rules.d/10-wusb600nv2.rules
```
Add the following lines:
```
# UDEV-Rule for wusb-600Nv2 ID 1737:0079
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0079", RUN+="/sbin/modprobe rt3572sta"
```
Save and exit

[SIZE="1"]**Create the file /etc/modprobe.d/rt3572sta.conf**[/SIZE]
```
gedit /etc/modprobe.d/rt3572sta.conf
```
Add the following line:
```
install rt3572sta modprobe --ignore-install rt3572sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id
```
Save and exit

[SIZE="2"]**7**) Blacklist the rt2x00 modules:[/SIZE]
```
gedit /etc/modprobe.d/blacklist.conf
```
Add the following lines at the end of the file:
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870
```
Save and exit

[SIZE="1"]**exit from superuser to keep your machine safe ;)**[/SIZE]
```
exit
```


[SIZE="2"]**8**) Reboot and plug in your WUSB600Nv2 adapter - hope to god it works[/SIZE] :D


--------------------------------------------------------------------------------------------------
For those who know what they are doing and just want a shortcut just copy & paste the following which will:
-create 'build' folder in your home directory
-download + unpack emory's driver package
-rename it to WUSB600Nv2-2401 and cd into the new directory
-clean, build and install the module for your kernel

```
mkdir ~/build
cd ~/build
wget https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/+attachment/1649708/+files/RT3572-WUSB600Nv2-2.4.0.1-kernel-2.6.35.tgz
gunzip RT3572-WUSB600Nv2-2.4.0.1-kernel-2.6.35.tgz
tar xvf RT3572-WUSB600Nv2-2.4.0.1-kernel-2.6.35.tar
mv -i 2010_0709_RT3572_Linux_STA_v2.4.0.1/ WUSB600Nv2-2401
cd WUSB600Nv2-2401/
sudo su
make clean
find . -name "*.*o" | xargs rm
make
make install
```

Now you just need to create the .rules and .conf files to auto load the module when you insert your adapter (see **step 6** above) and blacklist the rt2x00 modules (see **step 7** above)

*All credits go to emory for providing the pre-configured 2.4.0.1 driver and to joho500 for detailing the .rules and .conf files, and providing a full step by step guide.*

---

### Post by n9ntje on 2012-05-01
thankyouthankyouthankyou ):P 

An ubuntu N00b

---

### Post by fubofo on 2012-05-01
Just glad I could help from one noob to another :)

---

### Post by larsstanley on 2012-05-01
A big thank you from me as well.
I'm completely new to Linux/Ubuntu and am having fun learning the basics - and am impressed with the capabilities.
I had the same problem with WUSB600N - and have searched the net for a couple of days to find a solution - and your very clear instructions made my day!
(I believe, that many of us download the latest RALINK drivers - which then causes the problem)

Thank you !

---

### Post by fubofo on 2012-05-01
No problem guys. I'm just as much of a noob lol

You would probably be surprised to see that I have had issues with WUSB600Nv2 working for about 2 years over different Ubuntu releases and multiple kernels.

Thought it best to keep a record for future use and for others (in the spirit of Linux)

---

### Post by gbaptista on 2012-06-07
Thank you for saving my life!

---

