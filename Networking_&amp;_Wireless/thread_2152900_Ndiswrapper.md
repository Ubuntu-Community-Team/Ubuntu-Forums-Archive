---
title: "Ndiswrapper"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by DmytriE on 2013-06-09
I am brand new to linux and don't know the very first thing about it.  I've looked at some of the basic commands such as cp, mv, mkdir, rmdir, etc.  But, I don't know the first thing about setting up so it can see my USB wireless card.  From my research I've come to the conclusion that their isn't a driver for the "Netgear WNDA4100 N900 Wireless Dual Band USB Adapter".  I have a feeling that I will need to use NDiswrapper but I don't know where it is in linux (or if its even there).  Furthermore, once I get NDiswrapper I don't know how to install it...

I have a dual boot system with Windows 7 and Ubuntu 13.**.  Any help is welcomed and greatly appreciated.  Please respond like I don't know anything cause I really don't. :(

---

### Post by ajgreeny on 2013-06-09
ndiswrapper is in the repositories but I think is not installed by default.  Be warned also that there was a time when the utility had to be built before use as the repo version did not work.  I have not had to use it for over two years, so am not sure if there is still a problem, but even if there is it is not difficult to compile and install it, just follow the instructions:-
> [I]**Compiling the latest version of ndiswrapper**

 [/I]
[LIST]
[*]This section is based on an ndiswrapper [wiki page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/InstallDebian"), and [here]("http://ubuntuforums.org/showthread.php?p=601226"). Please discuss any problems or errors you experience there.* It  is recommended that you first remove any sign of ndiswrapper from your  computer. There is a module which installs by default with Ubuntu. To  remove this, from a Terminal run the following commands: *

*sudo modprobe -r ndiswrapper sudo apt-get --purge remove ndiswrapper-utils sudo rm -r /etc/ndiswrapper/ sudo rm -r /etc/modprobe.d/ndiswrapper sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko*[I]  Before you begin to compile your own ndiswrapper, please note that  whenever you update your kernel you will need to recompile. However, it  shouldn't be necessary to remove the previous traces of ndiswrapper, as  detailed above when you reinstall. 
[/I] 
[/LIST]
***4.1. Install kernel headers***

[I] 
[LIST]
[*]From a Terminal, run: 

sudo apt-get install linux-headers-$(uname -r) and run the following for the dependencies: 

sudo apt-get install dh-make fakeroot gcc-3.4 build-essential 
[/LIST]
 
**4.2. Download and unpack the current version**

 
[LIST]
[*]You can find the current version of ndiswrapper [here]("http://sourceforge.net/project/showfiles.php?group_id=93482"). Then, in a terminal change to the directory where you saved the downloaded file and run the following commands: 

tar xvfz ndiswrapper-[current version].tar.gz cd ndiswrapper-[current version] Replace [current version] with the actual version of the file you downloaded. 
[/LIST]
 
**4.3. Install Ndiswrapper**

 
[LIST]
[*]The  most current version of ndiswrapper (since at least version 1.19) can  no longer be compiled into a .deb package. To work around this, do the  following while in your ndiswrapper directory (see above): 

sudo make uninstall sudo make It is advised that your run in fakeroot for the following: 

fakeroot sudo make install  If any errors occur during these steps, please try installing again. It  may be required for you to run in fakeroot during the entire process.  When everything has installed without error, return to the [install]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#install") section of this document to finish setting up ndiswrapper. 
[/LIST]
[/I] 

---

