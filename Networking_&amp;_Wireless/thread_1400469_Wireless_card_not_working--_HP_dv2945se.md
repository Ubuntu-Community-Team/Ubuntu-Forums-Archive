---
title: "Wireless card not working-- HP dv2945se"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Bartelby on 2010-02-06
I just installed and Ubuntu doesn't recognize my wireless card.  I can get a wired connection.  I can't figure out what kind of card I have (did the terminal command line, have no idea how to read it) or how to install a driver for this OS (HP's site just lists drivers for Windows).

Can anyone help me get the wireless card recognized?

---

### Post by Bartelby on 2010-02-06
Nice!  I looked at another thread and got my card info at least:

08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

Where do I go from here?  Thanks!

---

### Post by spegru on 2010-02-07
I thing broadcom wifi cards are now ok in Ubuntu, since about 8.04.
However the drivers are proprietary so they are not installed by default.
Nevertheless Ubuntu makes this easy.
I suggest plug in you wired connection, wait a bit and look for the little greenish circuitboard icon in the system tray that indicates there are proprietary drivers available for your system. (I think you can also find info about proprietary drivers from within system settings)

If you select the proprietary drivers section you should be presented with a list of what is available - such as Broadcom wireless.

Select and install and you should be fine after a reboot.


by the way - on terminal use there are two very useful commands you can try.
lspci  -  this lists all the devices on the internal pci bus, probably including your wireless card
lsusb  -  does the same for usb devices
Both are v.useful for discovering your hardware

---

### Post by Bartelby on 2010-02-07
Thanks for the advice, but it doesn't seem to be working.  No green circuit comes up.  When I go "System -> Administration -> Hardware Drivers" it just tells me no proprietary drivers are in use on this system.  Looking on the web it seems like I would have to somehow hack the driver to get it to work--- that doesn't seem like something the average user would do, right?

Does anyone know how I can search and install the driver?

---

### Post by Bartelby on 2010-02-07
I found a page that says:
In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you: 

 [Toggle line numbers]("http://wireless.kernel.org/en/users/Drivers/b43#")    1 sudo apt-get install b43-fwcutter



You will be asked to automatically fetch and install the firmware into the right location. 

I tried entering that text into the terminal.  It gives back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter


I also tried downloading some kind of b43-fwcutter package and putting the folder in the firmware folder (as instructed by the readme file) but it says I don't have rights to do that.  Any help?

---

### Post by spegru on 2010-02-08
It is critical that the network is connected when the system is searching for proprietary drivers so make sure you have your ethernet cable plugged in.

The same applies for installing anything else. I just tried your b43-fwcutter command here and it works for me. I think the proprietary drivers system uses fwcutter anyway so it may be the same problem.
 
Check your network connection by browsing a few web pages.
If that works ok then I wonder if you messed the system - for example repo settings. 

It might be worth booting off the live cd and seeing if you can do it from there. It wont last after a reboot of course, but it will tell you if there is something wrong with your installation. 

By the way, to install anything you need to be root, so prefix all commands with   sudo

---

### Post by Bartelby on 2010-02-08
Hey spegru, good call on the sudo and thanks for the reply!
 
For the b43-fwcutter command how is it meant to be used?  Do you need to download some program and run that command in the appropriate folder?  I don't really understand the terminal and what the aforementioned command is doing.
 
As for the ethernet I have kept it plugged in whenever working with Ubuntu.
 
I may give booting off of the live CD a try to see if it makes any differnece.  I haven't made any changes to my install other than what has been suggested in various threads on this forum, though.  And it definitely did not detect the card or offer to install drivers from the start.

---

### Post by spegru on 2010-02-08
It seems you have a BCM4310 wifi chip (Type lspci in terminal to find out for sure)

It seems from this thread [https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/379052](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/379052) that karmic does not automatically pick up this wifi chip.
However the link also says you just need to install the b43-fwcutter and reboot. Good luck.

---

### Post by Bartelby on 2010-02-08
The chip type I got back from the terminal is:
 
08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
 
Total noob question here, but how do you install the b43cutter?  When I download it normally in Windows an install wizard would come up, but none does in Ubuntu.  The readme file mentioned dropping the folder into a system folder or something (not at the computer now, I forget what it specified) but when I dragged and dropped it an error message told me I didn't have rights to do that.  It is set up so that I am the sole user on Ubuntu, so if I don't have admin rights no one does!
 
Basically I just don't know how to download and install such a package without a wizard.

---

### Post by Crafty Kisses on 2010-02-08
A couple of ways you can get this card working is check the Restricted Drivers option, and see if the driver is in there and you can install it like that, or manually install the driver. If you want to manually install the the driver, you need to grab the driver right **[here.]("http://www.broadcom.com/support/802.11/linux_sta.php")** Once you have that, you need to install the driver, so first remove the old b43 module by running:
```
rmmod b43
```
Then you need to unzip the actual file, so run:
```
tar -xvzf hybrid*
```
Now you need to start compiling the driver so run the following:
```
make -C /lib/modules/`uname -r`/build
```
Then you need to start the install for the driver you just downloaded, so load the new modules:
```
modprobe lib80211_crypt_tkip
modprobe wl
```
Then you need to run:
```
depmod -a
```
Then reboot, and you should be up and running.

---

### Post by spegru on 2010-02-09
Crafty, that's probably great, but not very newbie-friendly.

Bartelby, sounds like you just started with the command line. You can do alot of things there but it's not always necessary.
I take it you downloaded the fwcutter from a website?

Most Linux software is contained in a Repository for that distro. (very much like an app-store except everything is free!). You can get stuff from websites but then you often miss out on automatic dependency installations, updates and detailed distro-specific setups. The Repo avoids all that.

Two ways to access software in the Repo: You can just open software management from System (I think - I am doing this from memory right now) search for the package by its name or description, tick for installation and tell it to proceed. The system will then ask for your password before it continues
Howvever (and this is probably easier in fact), if you know what it is called, you can do it very quickly from the command line.
In this case the command would be 
sudo apt-get install b43-fwcutter

The sudo (Super User Do) makes you root and you have to enter your password before it will do the command (in Ubuntu it's probably your standard password again).
The apt-get part is telling the system called aptitude to go get the software from the repo, and install installs it.

From what I read (I havn't actually got this card) here [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)  the system should then tell you what to do (that's the Wizard, if you like). I'm not 100% sure from this whether the system actually fetches the driver from Broadcom, or whether you have to get it yourself. Try it and see. If you need to download it from Broadcom a google search should reveal its location, or you might already have it on a windows disc.

If this doesn't work due to very detailed setup stuff in Ubuntu, then you might have to resort to Crafty's method.

BTW, what fw-cutter does is to take the windows exe file (which is basically a kind of zip), cuts out the actual driver from all the other windows rubbish, and wraps it up in a linux framework so that the windows driver can be used in Linux. Pretty neat I reckon!

---

### Post by Crafty Kisses on 2010-02-12
> Crafty, that's probably great, but not very newbie-friendly.

That method is about as newbie-friendly as you can get, unless you're talking about installing drivers from Synaptic, and all you really have to do is copy and paste the commands I gave him. Like I said in my original post that's one of the many methods you can get the card to work, personally I would use that method, just because I know that it works.

---

