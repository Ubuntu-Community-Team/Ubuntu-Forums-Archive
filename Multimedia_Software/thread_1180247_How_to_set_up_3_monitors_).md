---
title: "How to set up 3 monitors :)"
date: 2009-06-06
forum: Multimedia Software
---

### Post by Curtis12 on 2009-06-06
Hi everybody,
I just installed Ubuntu 9.04 Juanty from Vista. I am new to Linux and Ubuntu and I have 3 monitors that I would like to have working with Ubuntu. Is this possible and how do i set it up? My cards are both NVIDIA, one is 7600 GT and the other is 8400 GS. I am currently running driver version 180.44. Now there is a new version, 185.18.14, and I am not able to install it... Please, what am i doing wrong?

Thanks a lot!
Curtis12

---

### Post by Curtis12 on 2009-06-11
Ok, i have a new problem. I thought i found a way to install NVIDIA-Linux-x86-185.18.14-pkg1.run. i ran the following code

sudo /etc/init.d/gdm stop
cd Desktop
sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
sudo /etc/init/d/gdm start

It ran and it said something about no predefined kernel (or something to that effect) and it asked if i wanted to make one. I hit OK. Now i get an error when i start up wtih NVIDIA. I have reconfigured to the default configuration and now no NVIDIA drivers are installed. I wetn to System--> Administration--> Hardware Drivers and install the 180.44 drivers again. It says i need to restart and I do. During the loading, it gives me the NVIDIA error and i have to go back to the default configuration. I found once, and i dont remember where, that i had the 185.18.14 something and that it was not possible to have 180.44 drivers (or somethign to that effect). 

Im sure many of you are lauging at me now lol, for being such a noob at this :) 

Thanks in advance,
Curtis12

---

