---
title: "fglrx issues"
date: 2011-01-11
forum: Multimedia Software
---

### Post by Beardednerd on 2011-01-11
Last night I was playing around with my system trying to install newer ATI drivers for my ATI HD 5770 on Ubuntu 10.10 x64. In my ignorance I downloaded the latest package from the ATI website and installed them directly over the drivers already running (...which were installed through the restricted software application). This caused a noticeable graphical slow down.

To correct my bad driver install I removed the downloaded package using the uninstall .sh found within ATI's wiki. However, the video performance did not improve. I then also removed the fglrx install through the repository, thinking this would revert me back to open source drivers upon reboot; Similar to how Windows reverts back to the OS driver when all 3rd party drivers have been removed.

However, this did not work as planned. On reboot I was presented with a 'no signal found' error with my monitor after viewing the Ubuntu splash screen (which does still display, oddly). After which I rebooted and attempted attempted a low graphical boot through the recovery menu, with the same result. Returning to the recovery console, I attempted to simply reinstall the fglrx driver ```
sudo apt-get install fglrx
```. The console stated the driver installed, but I still did not receive a monitor signal when I booted normally. Nor did fglrxinfo work when I once again returned to the recovery console.

Finally I attempted to manually install the fglrx driver, using this guide ( [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide) ). Everything was going well until I reached the step in which I had to run ```
aticonfig --intitial
```, and the console informed me there was no such command. Upon reading through the forums found two postings regarding this response; One suggested you could install aticonfig through the respiratory, which did not work. The other stated aticonfig is housed in /usr/lib/fglrx/bin, and that there could be a path issue in running it. When I navigated to /usr/lib/ I could see the fglrx folder, but I was informed the directory did not exist each time I attempted to move in to it.

I am at wits end. Is there anyway for a newbie such as myself to recover from this double driver install/purge/etc? If not, is there a way to re-install the Ubuntu O/S files, but leave my installed programs/config files in place? While I know I can boot to a live CD to backup my content and reformat, it does take a very long time to move 500Gb of data between two drives.

---

### Post by Yellow Pasque on 2011-01-12
The full removal procedure in the wiki should reset your graphics configuration to how it was after a fresh install: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
Additionally, you should delete or move /etc/X11/xorg.conf if you have one.

---

