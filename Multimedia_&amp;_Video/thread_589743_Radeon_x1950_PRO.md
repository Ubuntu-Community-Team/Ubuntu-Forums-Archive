---
title: "Radeon x1950 PRO"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by MySweetTedy on 2007-10-24
Hello everyone, i have been trying for 2 weeks to get my video card running, but have encountered many problems using almost every installation guide i found around.

so firstly about my pc:

pentium 4 3.0 Ghz
1.5gb ram
enough disk space
Video:
AGP Ati Radeon x1950 PRO 512 MB Ram
**2 Monitors**

All i tried till now was on Ubuntu 7.04 and 7.10, right now i am installing Kubuntu 7.10, but everytime i try to fix my drivers and both monitors to work, i have to reinstall Ubuntu cause no Graphic starts. So i was hopping for someone to tell what exactly to do so that i get everything working. I am not completely new to ubuntu but I dont really have advanced knowledge so if your guide is more noob friendly it will be great :) If you give me the links to the right HOWTOs to use it will be great 2.

Thanks

---

### Post by DarkMachine on 2007-10-28
I also have a Radeon X1950 Pro AGP, I read somewhere that there was a problem with this card (AGP version).  Apparently it is recognized and a PCI card instead of AGP.   I get 3d to work if i go to ATI's page, download the 8.37 drivers.   Then extract them:

 sudo sh ati-driver-installer-8.37.6-x86.x86_64.run --buildpkg Ubuntu/gutsy

Then use the package tool of your choice to install the *.deb packages, and reboot.  This works for me.  I wish they would fix this problem, because i hear the NEW drivers are really much better.

Right now i am runnign the 8.42 drivers (no 3d), and the GDM login screen doens't come up just black screen.  Since i know it's running, i just type my user name and password to login and then X starts up  and everything runs smoothly.  but if i want to game I go back to the 8.37 drivers.  If there is a way to make the new drivers work i would love to know it.

Darkmachine

---

