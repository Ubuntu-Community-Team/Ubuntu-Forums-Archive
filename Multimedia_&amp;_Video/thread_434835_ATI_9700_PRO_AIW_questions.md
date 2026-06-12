---
title: "ATI 9700 PRO AIW questions"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by Neil_Bell on 2007-05-06
OK guys tired of MS stuff and going to make the swap. Tried a few distros and like what ubuntu has to offer so got it installed. Computer is a P4 3.06gig with an ATI 9700 Pro All in Wonder AGP card. What I want to do is run a 3d desktop, beryl preferable and use the tv tuner portion of the card for watching tv. Don't need video capture which isn't supported anyway. Question is which driver are you using / software to accomplish this. Anyone with this card can you give me some guidance on it. Running 7.04 version as well. Lots of info out there but not specific and as there are a few variants of this card need to pic the brains of the experts.


thx Neil

---

### Post by Neil_Bell on 2007-05-07
ok little more info ...running the mesa open source driver....followed the beryl install on wiki but still isn't a fan of the r300 card.locks up solid so no error codes...come on boys help a brother say good bye to Bill Gate..for just seconds out of your day you too can save a poor windows user.

---

### Post by Monosabio on 2007-05-28
Any idea if Beryl will support old Ati cards ? I also have an ATI 97000 Pro AIW and can't use 3D desktop :-(

---

### Post by super.goop on 2007-05-29
Beryl worked for me and I'm using an ATI 9800 Pro AIW.  I had to use the radeon driver ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)).  I also had to right-click on the Beryl icon in my system tray and select Beryl under the Window Manager (b/c it was still using Gnome after installing Beryl).

---

### Post by freefromXP on 2007-05-29
I use a 9800 pro on a XP2700+ 1.5g machine and Beryl runs great.  I use this guide to install drivers and beryl. [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

  The only problem with this install is it sucks for games.  I can't get anything to play and I am fixing to go with the ATI drivers and XGL to use beryl.


  IF you don't care about gaming use the link above it will work great for you.

---

### Post by Neil_Bell on 2007-06-02
will give them a try...right now i'm running the lastest ati drivers from ATI site, XGL and Beryl. This was the guide i used. Tonnes of other tweaks there too. beryl runs and start right away there is the code you need to make that happen on the page listed.
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)
Thing of it is I work fine but it isn't a very stable setup. I get random lockups where only the mouse works and that is it. Only solution is a hard reset, sys req keys do nothing unless i get to the problem fast. A of course a hard reset does give you the all important log file i need to see what the issue is. Tried pretty much every driver but not sure if the radeon was in the mix or not but need to kill the lock up issues as it is a pain in the ***. all in all my linux experience is good so far so anotherwindows convert is here to stay.

---

