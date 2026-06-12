---
title: "Which Nvidia driver to install? (Open source driver is unstable)"
date: 2013-02-20
forum: Multimedia Software
---

### Post by WWLK on 2013-02-20
Hi,

I'm on Ubuntu 12.10, fresh install, dual booting with Windows on a separate physical drive.

I installed Ubuntu and installed ~250MB of updates; however from install to present I have had problems with the graphics on Ubuntu (none on Windows). 

Problems include:
 - Windows flashing between 'what the window should look like' and a black area representing the size of the window.
 - Windows staying as black rectangles. (Sometimes clicking in the black area will fix it temporarily)
 - The entire desktop flashing black for several seconds.
 - Dialogs (e.g. right click dialog) just a black rectangle.
Note: A screenshot of black areas on my screen included.

I also have dual monitors with resolutions of 1920 x 1200 and 1280 x 1024. Not sure if this is anything to do with the problem.

I'm guessing this is something to do with the Nvidia drivers (I have had similar problems on previous installs of Ubuntu including the LTS version) so I checked out the graphics drivers available.

I have included a screenshot of the drivers I have available however I'd like some advice on which one to install since in past installations, installing a driver has worsened the problem. Also I have attached a screenshot of my system specs (where interesting the graphics are 'Unknown').

Thank you for your time :)

---

### Post by pme 72 on 2013-02-22
If you want to use Unity you should probably install one of the proprietary drivers. If you want to try to continue using Nouveau try installing the xubuntu-desktop package from the software center. You will need to reboot and choose xubuntu from the login screen. You can always choose Unity at the next reboot if xubuntu-desktop does not work out. 

I had similar issues when I installed an Nvidia GT220 on my machine running 12.10. With the xubuntu-desktop package the issues with the screen corruptions disappeared.

---

### Post by Yellow Pasque on 2013-02-22
> where interesting the graphics are 'Unknown'
It's a cosmetic bug. Install mesa-utils.
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

### Post by ersatzsplatt on 2013-02-22
Go ahead and use the proprietary driver nvidia provides.  it is difficult to have open source drivers that make the best use of the hardware when the vendor considers fundamental working portions of the hardware proprietary.  please follow up with how that worked for solving your problem.

---

