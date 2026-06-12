---
title: "Blackgold BGT3600 Tuner with Mythbuntu"
date: 2013-01-25
forum: Mythbuntu
---

### Post by mattcony on 2013-01-25
Hello,
 
VERY new to Mythtv and Ubuntu / Linux. i have never even touched it !. I'm really trying to ditch my Microsoft MCE setup and move to Mythtv/XBMC/Respberry Pi setup.
 
I found Mythbuntu which I thought was the answer to everything for me as a Windows only user. So far I have managed to download the ISO and install on my PC with backend/frontend setup.
 
I have now hit a wall in that i can't setup my tuner card to work, I have a blackgold BGT3600 twin tuner. From what i can see from there install guide its very hard to make work.
 
I have never done anything with Linux and don't know where to start the instructions on there website I can't understand. I'm even struggling to move the .tar file to the correct folder I can't even find a program to let me copy files into diffrent folders. I have tried the "Thunar Filemanager" program that was included in the build but this won't let me move anything. If I drag a file to another folder it moves back ??
 
Is there a self-install driver/file I can use ?
 
Thanks
Matt

---

### Post by BicyclerBoy on 2013-01-25
Blackgold (fool's gold more like for linux users) provide a binary blob that only works with 2 specified kernel versions..
Their website & products all *look* very impressive.

Unfortunately they did not make an (obvious) open source layer that could be re-compiled/linked to any kernel version (within reason); this is what nVidia does.

Unless you know how to get that specified kernel or stop/pin the kernel package & thereby stop kernel updates, you're fighting a losing battle.

The BGT driver build instructions look reasonable. 
AFAIK MythTV backend does not work on windows.

---

