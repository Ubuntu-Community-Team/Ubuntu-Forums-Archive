---
title: "*FINALLY* Getting the Nvidia 8200 Working in Ubuntu 8.10"
date: 2009-03-23
forum: Multimedia Software
---

### Post by nbaes on 2009-03-23
I've been going around in circles for a week trying to get decent performance from my PC's integrated Nvidia 8200 GPU. I wanted to post this for anyone else who is struggling with this. Using the hardware drivers provided by Ubuntu 8.10, I had trouble -- 173 worked OK, but everything felt slow. 177 caused a lot of instability, especially with Desktop Effects enabled. I got the 180.29 driver using the instructions below, and now finally I get good performance with Desktop Effects, Flash videos, and no more issues with scroll artifacts in FireFox. I'm posting this for anyone else who's been struggling with these problems. Enjoy!

Add these 2 lines to /etc/apt/sources.list:
 deb [http://ppa.launchpad.net/anders-kaseorg](http://ppa.launchpad.net/anders-kaseorg) /ppa/ubuntu intrepid main  
 deb-src [http://ppa.launchpad.net/anders-kaseorg](http://ppa.launchpad.net/anders-kaseorg) /ppa/ubuntu intrepid main  

[I did this by typing  gksudo gedit /etc/apt/sources.list into terminal and adding these sources at the very end of the file]

Now run the following commands:
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 026491A5
 sudo apt-get update  
 sudo apt-get install nvidia-glx-180  

Restart your computer.

Check to make sure the install was successful by running dmesg | grep -i nv; on the last line, you should see 

NVRM: loading NVIDIA UNIX x86 Kernel Module  180.29  Wed Feb  4 23:44:25 PST 2009

Credit for these instructions goes to BikeTheTam, and his original post can be found at [http://ubuntuworking.blogspot.com/2009/02/nvidia-and-image-corruption-in-intrepid.html](http://ubuntuworking.blogspot.com/2009/02/nvidia-and-image-corruption-in-intrepid.html)

---

