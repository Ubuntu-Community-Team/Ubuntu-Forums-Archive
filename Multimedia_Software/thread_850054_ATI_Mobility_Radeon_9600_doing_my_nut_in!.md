---
title: "ATI Mobility Radeon 9600 doing my nut in!"
date: 2008-07-05
forum: Multimedia Software
---

### Post by surnameforename on 2008-07-05
Hi all,

I've been trying to get 3D acceleration working on my laptop for the last week having decided to give ubuntu a try out. It installed fine for everything except the 3D graphics.

The laptop is an Acer Travelmate 8000 and has a Mobility Radeon 9600 (part rv350) graphics chip. Ububtu is 8.04. The chip is listed as one which will work using either set of drivers (open-source or proprietary)

For installation I chose the 'bog-standard graphics' option and this works fine in 2D. If I let the installer install 3D drivers then ubuntu would lock up either during login or just after (neither ctrl-alt-f1 nor the capslock keys would work so it was a hard shutdown by holding down the power button).

INitially I tried the intructions for to open source drivers... 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy))

This lead to the same lock up.

I then tried these more comprehensive instructions...

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but again with no luck. I tried both a couple of few times. A friend said he was using the proprietary ATI binary drivers without problems so I tried the instructions here...

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers)

but it failed at the instuction to...

 You will then need to build the installation packages with the downloaded ATi drivers (ensure the ATi drivers have the execute flag set first): 

may be becuase I never ensured the execture flag was set because I have no idea how to do this or test for this.

SO I gave up on that and used the add/remove applications to add the drivers and then did a reboot. This didn't seem to make a difference. I tried to find out what the gl driver was by 

glxinfo | grep vendor

which returns...

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

WHich is what the standard graphics give. The xorg.conf file just seems to have the standard stuff in an not been modified by the ATI installer.

I'm a bit lost, I've searched the forum and the internet but without finding much whihc doesn't come down to a variation on the above.

I'm a bit lost on how to test the proprietary ATI drivers - the installer says they are installed, but is there a magic incantation to get them to be used?

Any help appreciated,

SF

---

### Post by Agroth on 2008-07-12
Big bump on this one! I have the exact same problem and I can't find any solution anywhere. The worst part is that it worked okay in Gutsy but after installing (clean install) Hardy, I can not get this to work in any way.
Please help.

---

### Post by bodhi.zazen on 2008-11-22
Looks like a bug. I do not know if there is a fix.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

---

