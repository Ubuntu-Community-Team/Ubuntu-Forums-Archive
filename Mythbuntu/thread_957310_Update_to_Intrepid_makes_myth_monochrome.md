---
title: "Update to Intrepid makes myth monochrome"
date: 2008-10-24
forum: Mythbuntu
---

### Post by beablis on 2008-10-24
Hi, I just updated my mythfrontend (using a VIA CLE266) from mythbuntu hardy to mythbuntu intrepid. After that XFCE and the Myth-GUI look quite bad (about 8 colors). 
The strange thing is that LiveTV and all recordings look fine. 

Do you guys have an idea what happened?

---

### Post by ian dobson on 2008-10-24
Hi,

Sounds like the update broke the graphic driver. 
Maybe try unstalling the graphic driver,reboot then re-install the driver or reconfigure the xserver using.

sudo dpkg-reconfigure xserver-xorg

Regards
Ian Dobson

ps. What driver are you using?

---

### Post by beablis on 2008-10-25
It looks like intrepid doesn't include the via driver, which was used on my machine on hardy. I'm just trying to activate the openchrome driver manually on this via based frontend (Digitainer) but the picture still looks as bad as with the automatically generated xorg.conf. 
There are several complaints about openchrome in launchpad, some recommend to add the 
Option		"XaaNoImageWriteRect" 
to the device section in xorg.conf but this doesn't solve the issue here.

So my recommendation for all VIA users is not to update to 8.10 (yet)!

---

