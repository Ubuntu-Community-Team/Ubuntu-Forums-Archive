---
title: "How to Dedicate Bandwidth in Ubuntu"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by cdusseau on 2010-08-19
I have a setup to image computers 16 at a time. Basically what happens is that I PXE boot (tftp) to a menu, navigate submenus to choose the correct system image, then clonezilla is loaded and the image process begins.

The problem I am running into, is that once I have several of the machines going, the network load seems to be too great and navigating the menus to choose the correct image takes 5-30 seconds longer than it did under no load.

Basically what I would like to do is see if I can dedicate a certain amount of my network bandwidth solely for the PXE (tftp) server to speed up menu navigation.

I have gigabit connections all the way through, the only physical limitation I could see might be the use of CAT5E cable instead of CAT6. Not sure if that would be the culprit though.

---

