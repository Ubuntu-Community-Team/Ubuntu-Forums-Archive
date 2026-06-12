---
title: "NVIDIA-Linux-x86-185. just work dam you"
date: 2009-06-12
forum: Multimedia Software
---

### Post by memnoch7 on 2009-06-12
So I'm just learning the whole Ubuntu thing, and I'm playing around with getting some of my games installed with wine the only problem is I can't get my video card driver working correctly... (ubuntu 8.04 nvidia geforce 9800gt)

originally I tried  doing the whole ctrl+ alt + f2 and then 
sudo /etc/init.d/gdm stop
cd Desktop
sudo sh ./NVIDIA-Linux-x86-185.yadda yadda
sudo /etc/init.d/gdm restart

and eventually after many tries and having to get some sort of header library thing it worked!!!
until i rebooted... and then it went back to low resolution mode. so I went forum hunting and I found a thread said i should remove restricted modules, and any other related nvidia products before installing the driver... 

did that reinstalled driver.. and now it just stays in low resolution... nvidia-xconfig doesn't seem to do anything and I'm stuck in this mode any help would be nice

---

### Post by majamba on 2009-06-12
install the driver using aptitude

then run as root for some reason i need to do this then my videocard worked

---

### Post by Arup on 2009-06-12
Do a --purge remove linux restricted modules and linux restricted modules common, remove nvidia modaliases, install xorg-dev, do a sudo apt-get install build-essentials and then hit ctrl+alt+F2 and after logging in do a sudo /etc/init.d/gdm stop 


do a sh NVIDIA.xxxxxxx --unistall and then rerun the installer.

---

### Post by memnoch7 on 2009-06-12
K just got home from work I'll try it see what happens thx guys

---

### Post by memnoch7 on 2009-06-12
so I went ahead and purged what i could find and went reinstalled it nogo... tried the beta drivers nogo made sure my  gdm file was configured properly... nogo.. tried a billion things... at the end of the day I got it working using the beta drivers... just reinstalling em the same way i have been. 

ctrl alt f2
sudo /etc/init.d/gdm stop
cd Dekstop
sudo sh ./NXXXBETA FACE
sudo /etc/init.d/gdm restart

yay nvidia LOGO... I have no idea I'm sure you guys got me on the right track some how... but weird thing is when I installed the driver it gave me an error saying unable to open /usr/lib/nvidia/libglx.so xserver-xorg-coc for reading no such file or directory.. and i hit enter for ok  well w/e thank god it works for now thanks again guys

---

