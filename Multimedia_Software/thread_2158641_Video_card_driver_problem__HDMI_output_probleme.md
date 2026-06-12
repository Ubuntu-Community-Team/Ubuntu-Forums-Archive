---
title: "Video card driver problem | HDMI output probleme"
date: 2013-06-29
forum: Multimedia Software
---

### Post by malstorm86 on 2013-06-29
Hi guys, i have probleme with my linux! Im new at linux i started use this os on march because of my new job! i have to learn how to use it! But actualy all working well but not my graphic card and i usualy use the HDMI to plug into my TV 42 inch for doing some prog. So i tried a lots of things! 

Spec:
XPS L702x
VIDEO card : GeForce GT555m
Ubuntu: 12.04 LTS

#1 download the NVIDIADRIVER on nvidia with the .run file
chmod -x or 777 on the file
run it...

not work because lightdm started

so ctrl-alt f1 
sudo su -
service lightdm stop

run driver again and during installation the driver crash!..... so i unstall everything try something else after backup my xorg.conf.

#2 try to install the nvidia-common
everything install ok
im running the nvidia-settings! it told me i am not using my nvidia card.. 
so i run the nvidia x config file
after reboot
my resolution cannot be bigger than 640/480
so i have to change the horizsign and verticalrefresh to have back my resolution and my nvidia driver is never use and i cant use my hdmi

#3 try to install the nvidia-EXPERIMENTAL driver 310
doing everything on step 2 and not working...


i am not enable to active my nvidia card

When i plug my HDMI WIRE my tv say always incompatible resolution! i tried all my resolution and im not enable to active it!

is there a way to install the nvidia-driver on my computer :) I hope yes ! :) ty guys for help me


myusername@malstorm:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 124d (rev a1)

---

### Post by Yellow Pasque on 2013-06-29
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by malstorm86 on 2013-07-01
not working! same probleme!

---

### Post by malstorm86 on 2013-07-01
so anyway i wil fix that by formating , installing windows 7 , install vmware, run linux in full screen on my tv!

---

