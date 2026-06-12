---
title: "Not able to enable wireless"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by nooffswitch on 2010-07-07
I have recently installed ubuntu on my laptop. However I cannot enable the wireless on it. The card is registered and drivers are installed. From reading previous forums i can guess that its because its "Hard Blocked"" (assumptions). However the switch for it is in the on postion. Any help is appricated.

---

### Post by nooffswitch on 2010-07-07
Would able be able to tell me how to enable wireless as so far all i get is wireless is disabled. Not to familiar with Ubuntu at the moment, so any help even guesses would help.

---

### Post by nooffswitch on 2010-07-07
[COLOR=Black]i fixed it by doing
[/COLOR][COLOR=Black]sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4126-20100324.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4126-20100324.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
cd madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
make
sudo make install
sudo modprobe ath_pci
sudo reboot
[/COLOR][COLOR=Black]

I'm not sure if someone with my knowledge could use this info to help anyone else or knows how to delete this thread. Its a fix i found on a previous forum and  i changed the  web address and file name to the current most recent at the time i posted. As i'm not entirely sure what i did. :P.
[/COLOR]

---

