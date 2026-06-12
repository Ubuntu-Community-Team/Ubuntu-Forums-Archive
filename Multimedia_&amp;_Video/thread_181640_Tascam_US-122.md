---
title: "Tascam US-122"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by Infatuated_iPod on 2006-05-24
I have a quick question, I know its kind of dumb but oh well. 

I have a Tascam US-122 USB Recording machine, it works fine in windows, and i used to take my laptop around with it to create sort of a mini-recording studio. The program i used was Cubase, and everything worked fine. 

Well now, on the laptop that used to have windows, I have Ubuntu, Is there any way to get this hardware to work , and what software could I use to record? 

When i plug it in , the hardware configuration thing says (US-122) but nothing else. I have no idea how to go about installing this.

---

### Post by SFN on 2006-06-12
I've written a HOWTO that may help you. It's [here]("http://ubuntuforums.org/showthread.php?t=194490").

---

### Post by Copland Audio on 2007-04-03
I'm having a tough time installing my us-122 interface as well.  I've looked at the instructions at [http://ubuntuforums.org/showthread.php?t=194490](http://ubuntuforums.org/showthread.php?t=194490)  
Step 1:
sudo apt-get install fxload alsa-base alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-utils alsamixergui alien
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fxload is already the newest version.
alsa-base is already the newest version.
alsa-firmware-loaders is already the newest version.
alsa-tools is already the newest version.
alsa-tools-gui is already the newest version.
alsa-utils is already the newest version.
alsamixergui is already the newest version.
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

My results in the second step were:
 => `alsa-firmware-1.0.9-4.noarch.rpm'
Resolving chuck.ucs.indiana.edu... 156.56.247.193
Connecting to chuck.ucs.indiana.edu|156.56.247.193|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch ... 
No such directory `pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch'.

now, I'll admit, I'm brand spanking new to the terminal window, and I imagine I'm not going to the correct location to complete step 3 (I'm getting:  sudo alien --to-deb alsa-firmware-1.0.9-4.noarch.rpm
File "alsa-firmware-1.0.9-4.noarch.rpm" not found.)  
and I'm not quite sure how to get to the right directory to...what am I doing, converting to debian?  I apologize, but I think I'll need some more direction.  
I'm trying, though!  Thanks in advance for any help and your time!
I should also say that I have the CD with the windows and mac drivers... would that help?  I'm just trying to get a basic recording setup with Audacity... I'm running Xubuntu Edgy...

---

