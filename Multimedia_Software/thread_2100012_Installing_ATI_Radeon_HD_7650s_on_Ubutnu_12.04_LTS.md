---
title: "Installing ATI Radeon HD 7650s on Ubutnu 12.04 LTS on HP ProBook 4540s"
date: 2012-12-31
forum: Multimedia Software
---

### Post by thish on 2012-12-31
Hello everyone,

I'm desperately in need of help with figuring out how get my AMD ATI Radeon HD 7650s graphics to work on my HP ProBook 4540s laptop. I have tried a few distributions ( ubuntu 12.04 LTS, ubuntu 12.10, Mint Maya, Mint Nadia and none of them works.

It says "Uknown" when i check the system information and some programs that needs it activated rejecting to load due to the graphic card not installed properly.

this is what i did.

unzip /home/username/Downloads/amd-driver-installer-12.6-legacy-x86.x86_64.zip
sudo chmod +x /home/username/Downloads/amd-driver-installer-12.6-legacy-x86.x86_64.run
sudo sh /home/username/Downloads/amd-driver-installer-12.6-legacy-x86.x86_64.run

sudo reboot
sudo aticonfig --initial

sudo reboot

---

### Post by Luigi2012SM64DS on 2012-12-31
did you try:
```
sudo apt-get install fglrx
```
?

---

### Post by thish on 2012-12-31
no i didn't.. but i'll give ut a try now. i also did a fresh install. thanks for the reply :) hope this works

---

### Post by thish on 2012-12-31
it didn't work... i tried to do this then

sudo sh '/home/username/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.run' 

and when the  setup start running it said i need to remove fglrx.

i read somewhere about problems in 2xxxx-4xxxx series. I wonder if this affects on 7xxxM series also.

---

### Post by thish on 2012-12-31
ok i played around with terminal and somehow got it to work.. not sure what exactly happen but it did the trick.. 

so if anyone wanna try... here's my specs...,

ATI Radeon HD 7650s 2GB
Linux Mint 13 (maya) cinnamon 32bit


this is what i did....

    1  sudo apt-get install fglrx
    2  sudo reboot
    3  sudo
    4  sudo '/home/thish/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.run' 
    5  ll
    6  sudo sh '/home/thish/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.run' 
    7  sudo sh '/home/thish/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.run' 
    8  sudo sh '/media/Portable500/MasterStorage/Softwares Collection ( Linux ) 22-10-2012/amd-driver-installer-12.6-legacy-x86.x86_64.zip' 
    9  sudo sh '/home/thish/amd-driver-installer-12.6-legacy-x86.x86_64.run' 
   10  sudo apt-get install ia32-libs
   11  sudo apt-get remove --purge xserver-xorg-video-radeon
   12  sudo apt-get remove fglrx fglrx-amdcccle
   13  sudo apt-get install fglrx-updates fglrx-amdcccle-updates
   14  reboot
   15  sudo reboot
   16  sudo dpkg -l fgl*
   17  sudo aticonfig --initial -f
   18  sudo aticonfig --initial
   19  sudo aticonfig
   20  history

---

