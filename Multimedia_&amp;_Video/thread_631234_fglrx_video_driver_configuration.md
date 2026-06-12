---
title: "fglrx video driver configuration"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by rmemm on 2007-12-04
I just installed a new ATI Radeon X1600Pro video adaptor card.  This is a PCI-E card.  For obvious reason's I'd like to use the ati or preferably the fglrx driver with this card.  At the moment I'm using the vesa driver on Bus PCI 7:0:0 and that works fine.  Also I'm using Dapper.

The problem I have is that the fglrx driver fails to load because of a "no screens found" error.  It kind of seems like there are 2 ports or something.  PCI 7:0:0 seems to configure, then PCI 7:0:1 fails with "no screens found".  

This is a two port card - meaning I can connect 2 monitors at least.  In fact is has 3 ports - vga, dvi+vga, and svideo.

I only want one monitor -- and in fact I'm using the VGA plug only at the moment.

So how to I configure this in Xorg.conf?  I'm just not sure what to do about this.  Do I have to separately do something for PCI 7:0:1 even though I don't think I want a second monitor?  Is the X1600Pro even supported by this driver?

I have tried the ATI auto configuration tools -- but it too fails (I think with no screens found but I'm not certain).  Also I'd rather manually config Xorg.conf because the auto config seems to totally screw up my Xorg.conf file.

Thoughts -- I'm feeling pretty dense about this -- so any hints would be greatly appreciated.

Rob

---

