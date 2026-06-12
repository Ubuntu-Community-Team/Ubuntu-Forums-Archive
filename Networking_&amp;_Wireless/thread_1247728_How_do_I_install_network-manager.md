---
title: "How do I install network-manager?"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by Jordii on 2009-08-23
I deleted the network-manager, but now i can't install it.. I can't install anythin, i allways get the message: couldn't find the package ... (Or something like that, I'm Dutch)
I also can't connect to the internet, and I can't install .deb files. I always get an error like:
- depency is not satisfiable: ....
- Wrong architecture (.....)
 
I installed Ubuntu on my windows media center edition, with wubi. I thought it wasn't only a wubi problem so I post this here.
If you need more information, please tell me how I can get that information ](*,) I'm REALLY new to it :P

---

### Post by lswb on 2009-08-23
> **Jordii said:**
> I deleted the network-manager, but now i can't install it.. I can't install anythin, i allways get the message: couldn't find the package ... (Or something like that, I'm Dutch)
I also can't connect to the internet, and I can't install .deb files. I always get an error like:
- depency is not satisfiable: ....
- Wrong architecture (.....)
 
I installed Ubuntu on my windows media center edition, with wubi. I thought it wasn't only a wubi problem so I post this here.
If you need more information, please tell me how I can get that information ](*,) I'm REALLY new to it :P

Probably the quickest way is to start synaptic, and from the synaptic menu click on settings and check off the live CD as a software source. Close that dialog and click on reload, now you should be able to reinstall NM from the CD. After you have reestablished an internet connection you can unselect the CD, click reload again, and update to the current version of NM if it has changed.

As another method, if your connection is through an ethernet cable connected to a router, running these commands in a terminal will in most cases get you a connection:

sudo ifconfig eth0 up
sudo dhclient eth0

---

### Post by razorboy5 on 2009-08-23
wrong architecture means it's not ur OS i think...?

probably using the wrong 32bit or 64bit or something like that

+1 for lswb's method

---

### Post by Jordii on 2009-08-23
I can't find the option to check off the CD

---

### Post by lswb on 2009-08-23
OK, try again:

Main Menu/System/Administration/Synaptic, enter password if prompted.
After Synaptic has started, from the Synaptic menu, select Settings/Repositories/Ubuntu Software. The check box should be at the bottom of the dialog box.

---

### Post by Jordii on 2009-08-23
Thank you! I can check off that option, but I have to eat now, so I'll try the rest later.

---

### Post by Onesimus on 2009-08-23
When you say that you deleted the network manager - how did you do it ?
Did you uninstall it, or did you delete the icon in the top panel.  

If it is the latter, then this can be simply added by right clicking on the top panel and selecting 'Add to Panel...',

Scroll down and select 'Notification Area'.  Click Add and you're done !

---

### Post by Jordii on 2009-08-23
I used the terminal to remove it.

---

### Post by Jordii on 2009-08-23
Now I get:
Please insert the disk labeled:
XUbuntu 9.04_Jaunty Jackalope_-Release i386 )20090420.1) in drive /cdrom/
(also seems that I used the Xubuntu installer to install Ubuntu)
 
The installer CD is inside, and I was able to open it, it showed on my destktop named Xubuntu 9.04 i386
 
Then when I click cancel I get the message:
W: Failed to fetch cdrom:[Xubuntu 9.04_Jaunty Jackalope_-Release i386 (20090420.1)]/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb
 
Edit 1: Could it be something with my drivers? Because I recently reinstalled my computer, then I also couldn't connect to internet, but when I updated the drivers everything worked just fine.
 
Edit 2: I forgot to mention that when I load the packages I get a message: The following details are provided:
I can't really translate that to English but it's something like he can't load many stuff from [http://archive.ubuntu.com/ubuntu/dists/jaunty/](http://archive.ubuntu.com/ubuntu/dists/jaunty/).....
These are links, but i can't load them because I don't have my internet connection working yet? And do I need those links to make it work?
An example (May not be translated correctly)
- Loading from [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg). Could not find archive.ubuntu.com
 
Edit 3: Now I get the message:
E: Unaple to lock the download directory.
And another message half dutch..
E: Kon vergrendeling /var/vache/apt/archives/lock niet verkrijgen - open (11 resources temporarily unavailable)
It's nearly the same message.. I know what it means, but not how to change it.

---

