---
title: "ATI help, no drivers found!"
date: 2011-05-31
forum: Multimedia Software
---

### Post by highonpop on 2011-05-31
Im getting frustrated with this...

I have ubuntu 11.04

few things first:

-I'm a total Linux noob.
-I cant figure out how to get to the x.org configuration, i've searched high and low for it. I looked in the software center and it says i have OpenGL installed, but when i search for OPENGL or x.org in my applications menu, it only gives me available downloads, and nothing to actually open in a window and use.
-When I open the additional drivers menu its 100% blank. not 1 driver is listed.
-I searched for and downloaded the proprietary ATI driver from the software center, additional drivers menu is still blank, and I can't run Unity now.
-I tried to open the ATI Catalyst control panel, and it says the driver is not properly configured, and to run the aticonfig, where is this? i cant find it...

None of this is making any sense to me. I've been reading forum posts and numerous 3rd party sites for days, and nothing works.

I'm just trying to get my laptop to run EVE. It ran fine when I had windows on here. All of my problems with it seem to be stemming from my Graphics, and I cant seem to figure out how to fix it. It seems that every fix I can find, doesnt work on my laptop, and many of the control panels people point to as a resource to fix a problem, I either can't find them, or they are not populated the way they should be.

I hate to say it, but if I can't get this issue resolved, I may have to turn back to Windows, The main reason I even have this laptop is to play games when I'm not at home...and I cant do that....all i can use it for ATM is music and internet...

---

### Post by Yellow Pasque on 2011-05-31
What card do you have? If it's on this list, then proprietary drivers are not going to work and you should head back to Windows for gaming with an ATI card. [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

---

### Post by highonpop on 2011-05-31
unfortunately mine is on that list, the x600  :(

I can't change it, as this laptop is relatively old, 6 years or so, and it has no expansion slots for extra cards

and I've also realized that I lost my windows disk, so looks like im keeping linux on this laptop, and leave the gaming for my home PC... at least for EVE anyway.

---

### Post by Yellow Pasque on 2011-05-31
Then do these 6 commands to get back to default driver install: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

After that, you may wish to try: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

