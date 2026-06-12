---
title: "new linux user, need help getting wireless setup"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by T.Rebel on 2010-05-11
hello, 

So ive decided to start playing around with linux recently, but i need some help getting my wireless setup going. i have a wn311b wireless card and am running ubuntu 10.04. 

now, i have searched around to figure out how to go about this, finding that people have successfully gotten this card to work for them using ndiswrapper. seeing this i learned how to install ndiswrapper from my live cd, which ended up being somewhat bothersome because the software manager could not detect my cd. i managed to add the cd in the terminal and install ndiswrapper this way, and the manager shows it was a success. however, i kinda forgot the commands i used to do this... whatever, i got it going..

After i installed ndiswrapper i found my .inf and .sys files from my windows folder and installed them using ndiswrapper, both in the terminal as well as using ndisgtk. both times the driver and hardware were both installed and present when i ran "ndiswrapper -l"

from here is where i got stuck, when i type in "iwconfig" and "ifconfig" wlan0 is no where to be seen. also, there is no option for a wireless network configuration, just an ethernet connection. 

"lspci" shows my device as well, and i have also blacklisted the suggested native drivers...

any ideas or help??

---

### Post by T.Rebel on 2010-05-12
anyone?? 

please this is getting very annoying..

another note, when i run the live disk my hardware is detected, both my nvidia card and my wireless. if i try to install the native drivers i get an error message for both, telling me to view the jockey.log. how can i view this log, and why cant i install??

---

### Post by Fist_Rothbone on 2010-06-22
**This worked for me: [COLOR=Blue]_[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)_[/COLOR]**[B]
I've  changed those instructions as needed for the [COLOR=Red]*WN311B-100NAS / BCM43XG*[/COLOR] *[COLOR=Red](rev 01)[/COLOR]. *
I worked and cussed for hours, but as soon as i did this and rebooted, i was up and runnin.

This is my first post: Figured i should try and be helpful, considering how much this forum has helped me.



Step 1 (run in terminal)[/B]

[COLOR=Blue]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/wn311; cd ~/wn311
sudo apt-get install cabextract
sudo apt-get install unshield
wget [ftp://downloads.netgear.com/files/WN311B_setup_6.1.exe](ftp://downloads.netgear.com/files/WN311B_setup_6.1.exe)
cabextract -L WN311B_setup_6.1.exe
unshield -d ~/wn311_xp/ -L -g "Driver_xp File Group" x disk1/data1.cab
sudo ndiswrapper -i driver_xp_file_group/wn311b.inf[/COLOR][COLOR=Blue]
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee  /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant[/COLOR]
[COLOR=Blue]sudo aptitude remove b43-fwcutter[/COLOR]

**Step 2  (run in terminal)**

[COLOR=Blue]sudo gedit /etc/init.d/wirelessfix.sh[/COLOR]

**Step 3**

Paste the followings in the opened file(wirelessfix.sh)and **make sure  you save it before continuing Step 4**

[COLOR=Blue]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
[/COLOR]
**Step 4  (run in terminal)**


[COLOR=Blue]cd /etc/init.d/ && sudo chmod 755  wirelessfix.sh[/COLOR]
[COLOR=Blue]sudo update-rc.d wirelessfix.sh defaults [/COLOR]

**Step 5**

[COLOR=Blue]Reboot and you are done[/COLOR]

---

### Post by elibenyosef on 2010-06-22
hi
thought i might ask you , i am trying to run the wubi.exe file from my desktop but for some reason nothing happens after i press on "run".
do you know mybe what is the problem?
thanks
eli

---

