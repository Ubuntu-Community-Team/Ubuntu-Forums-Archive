---
title: "K9Copy making backups that are larger that 4.7gb discs"
date: 2010-10-16
forum: Multimedia Software
---

### Post by Nightstrike2009 on 2010-10-16
Hiya everyone

I have a problem with K9Copy's back up system it cannot seem to shrink a DVD9 down to 4.7gb to fit on a standard 4.7gb DVD Disk, has anyone any suggestions on how to correct this? As it renders K9copy totally pointless for me.

PS: This issue didn't exist on Ubuntu 10.04LTS

---

### Post by mc4man on 2010-10-16
Well k9's default target size is 4400 MB which should fit on any dvd r, if you've changed that then reset.
(typical capacity is about 4,706,074,624 bytes
If it's set to 4400 then lower the amount you're over plus a little, no sense writing right to the edge, won't make any difference in apparent quality

---

### Post by Nightstrike2009 on 2010-10-16
Thanks mc4man,

k9copys default was indeed set to 4400Mb which I hadn't altered but your right lowering it should work, wish id thought of that, thanks friend :-)

UPDATE: This doesn't work you have to burn disc to .iso image first, then select that image as source and burn to disc from there, that way it fits on DVD5 disc.  I think K9copy was wrongly assuming that a DVD9 Blank was in the drive when actually it was a DVD5 (Using same drive as source)

That still didn't work K9copy would not burn due to source being bigger than disc :-(

---

