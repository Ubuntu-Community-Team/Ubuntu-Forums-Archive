---
title: "Can't install RawPlusJpeg addin for F-Spot"
date: 2008-07-04
forum: Multimedia Software
---

### Post by ReelExterminator on 2008-07-04
Hi, I am having trouble installing what seems like quite a useful addin for F-Spot (I'm using F-Spot 0.4.3.1 under Hardy). After choosing 'FSpot.RawPlusJpeg,0.4.3.0' in the Add-in Installation box (Edit &#8594; Manage Extensions &#8594; Install Add-ins) and pressing Forward, I get the message 'The installation failed!' with little helpful info. There are messages printed in the console either.

---

### Post by ReelExterminator on 2008-07-18
Has anyone used this plugin successfully?

---

### Post by RolfH on 2009-01-27
> **ReelExterminator said:**
> Has anyone used this plugin successfully?

Yes. I ran it in 0.4.3.1 before I upgraded to 0.5.0.3
It found a lot of duplicate path+name without file extension and merged them into one file, with the raw picture as original and the jpg as a version called jpeg.
 
Run f-spot from a terminal window to see output the plugin produces..

Try this (might work?): 
 * Backup your ~/.gnome2/f-spot/
 * delete ~/.gnome2/f-spot/addin*
 * start f-spot and reimport the extension

---

