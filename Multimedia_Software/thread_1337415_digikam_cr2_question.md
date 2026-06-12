---
title: "digikam cr2 question"
date: 2009-11-25
forum: Multimedia Software
---

### Post by bdaly on 2009-11-25
Hi All, 
Pretty much a complete newbie here. Trying to get away from Windows. I am trying to set up a photo workflow in ubuntu 9.10. I use a Canon 500D T1i camera , shooting RAW. Since it is a new model, I've had to do some hacking because it is not supported in the stable releases of most of the photo editing software. I have gotten gimp,ufraw,dcraw all importing the raw files 'correctly' (what I mean by 'correctly' is that the colors are not all pink/purple - they look correct) and where applicable they will convert to jpeg,tiff or whatever correctly.
For digital asset management,sorting and taging though I like the look of digiKam. Here is where I run into trouble. When I add an album in digiKam all looks well, I can 'correctly' view the raw files in the image browser. However, when I click the edit button (lets say I want to do a simple crop - not worth opening gimp for) the image looks all pink/purple in the image editor.

I am pretty sure that this has to do with the version of either libkdcraw or libraw digiKam is using. It seems that it may have an embedded local version of these libraries that it uses. I have tried to install from tarballs updated versions of these libraries but to no avail, when I click list of supported cameras, I cannot seem to affect the versions of KDcraw or LibRaw that digikam reports.

I've attached a screen shot showing the editor on the left and the viewer on the right. center is the version info for digikam.

I may be in over my head here but I feel like I'm very close. Any help would be greatly appreciated.

Regards,

Barry

---

### Post by bdaly on 2009-11-26
Anybody? Did I post this on the wrong forum?

---

### Post by bdaly on 2009-11-30
Monday morning bump! Anybody?

---

### Post by GameManK on 2010-01-18
Same problem here with Digikam 1.0.0.

---

### Post by GameManK on 2010-01-19
A newer version of libkdcraw is in kdegraphics in KDE SC 4.4, so I solved this problem by upgrading to 4.4: [http://www.kubuntu.org/news/kde-sc-4.4-rc-1](http://www.kubuntu.org/news/kde-sc-4.4-rc-1)

The upgrade was a bit problematic, but it works now.  Maybe you can grab just the newer dcraw libraries.

---

