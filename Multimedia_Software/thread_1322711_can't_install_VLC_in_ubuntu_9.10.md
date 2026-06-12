---
title: "can't install VLC in ubuntu 9.10"
date: 2009-11-11
forum: Multimedia Software
---

### Post by licketty_split on 2009-11-11
hi i can't seem to install VLC in karmic. When i use apt-get i get the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libvlc2
E: Package vlc has no installation candidate

ive tried installing thru the software center but it says "Not available in current data". any help is greatly appreciated

---

### Post by Menthu_Rae on 2009-11-11
Change your repository in software sources then try again.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download](https://help.ubuntu.com/community/Repositories/Ubuntu#Download) Server

---

### Post by Arup on 2009-11-11
Have you enabled medibuntu repos, open up terminal and type 

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

Enter your root password when it asks for it, after that do a sudo apt-get upgrade and sudo apt-get dist-upgrade and then do a sudo apt-get install vlc

---

### Post by licketty_split on 2009-11-11
thanks arup, i did that but still no change

---

### Post by howefield on 2009-11-11
Ensure the universe repository is enabled.

Then do a sudo apt-get update and try again.

---

### Post by Arup on 2009-11-11
Do you see vlc listed in synaptic?

---

### Post by omniuni on 2009-12-23
Hi,

I'm having the same exact issue. I don't know why. It did not happen on my other computer. Both got a fresh install of Karmic, and for some reason, I still can not install VLC on this machine! I even downloaded the package directly, and it failed because of dependency problems!

Has anyone figured out a solution, or at least what's going wrong?

---

### Post by Kilius on 2010-01-01
I had the exact same problem, and I solved it by changing the 'Download From' location in the 'Ubuntu Software' tab in the 'Software Sources' admin window.  I chanaged it to 'Main Server' from the region server ('Server from Canada') that it defaulted to.  After the packages were updated, I could install VLC through the the Ubuntu Software Center with no problem at all.

---

