---
title: "ATI graphics card drivers installation"
date: 2013-08-16
forum: Multimedia Software
---

### Post by rock2 on 2013-08-16
Hi,

I recently installed Ubuntu 13.04 and it has been treating me fairly well. 

Last week I was trying to install VirtualBox and noticed my PC was heating up. I had cool it off by putting a fan next to it. Upon a quick search i stumbled on this page

[http://askubuntu.com/questions/143808/why-does-ubuntu-trigger-thermal-protection-shutdowns-on-my-dell-laptop](http://askubuntu.com/questions/143808/why-does-ubuntu-trigger-thermal-protection-shutdowns-on-my-dell-laptop)

So i tried installing ATI Graphics Card drivers and it finished the installation with errors. I tried searching methods to install graphics card drivers and found these:

[http://askubuntu.com/questions/290583/how-to-use-ubuntu-13-04-with-ati-rv635-mobility-radeon-hd-3650-graphics-card](http://askubuntu.com/questions/290583/how-to-use-ubuntu-13-04-with-ati-rv635-mobility-radeon-hd-3650-graphics-card)

[http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-driver-in-12-04-lts](http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-driver-in-12-04-lts)

[http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)

I tried all of these, but none of them succeeded in installing the drivers.

Could you please guide me to identify what is going wrong?

I am relatively new to linux. So, if this question is too generic, kindly advise what kind of logs / procedures should be updated with this data.

Thanking you in advance

Chris

---

### Post by Yellow Pasque on 2013-08-16
Catalyst dropped support for your card in recent versions, so Catalyst won't work on anything newer than Ubuntu 12.04.1.

First off, make sure you have completely purged any of the failed installs: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)

Next, look at: [https://help.ubuntu.com/community/RadeonDriver#Power_Management](https://help.ubuntu.com/community/RadeonDriver#Power_Management)
Try the two "sudo bash" commands and see if it helps.
If not, then your Ubuntu options are:
1. Install Ubuntu 12.04.1 and Catalyst
2. Install a 3.11 kernel on your current install and use the dpm option: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc5-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc5-saucy/)
3. Install or upgrade to Ubuntu 13.10 (since it has 3.11 kernel already) and use dpm

---

### Post by rock2 on 2013-08-16
Thanx for the reply. I have a question, what is the dpm option? In the link you provided i see couple of files, of which I guess I will use the i386 version for installation. 

Just as a sidenote: I had installed Ubuntu 12.04 (not sure if 12.04.1) some time back, but the wifi was not working. Since I had only wifi available, i did not continue to use it.

---

### Post by Yellow Pasque on 2013-08-16
> Thanx for the reply. I have a question, what is the dpm option? 
[https://help.ubuntu.com/community/RadeonDriver#Power_Management](https://help.ubuntu.com/community/RadeonDriver#Power_Management)
[http://www.phoronix.com/scan.php?page=article&item=amd_radeon_dpm&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_radeon_dpm&num=1)

---

### Post by rock2 on 2013-08-28
I tried Option 2 since that seemed like the one with the least resistance. However doing so, leaves a blue bar on the left side of the screen. I tried to undo the changes. But the blue bar did not budge. Finally i resolved to installing Ubuntu 12.04.1.

---

