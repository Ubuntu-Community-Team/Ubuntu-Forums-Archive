---
title: "Using system ram for video ram"
date: 2009-12-01
forum: Multimedia Software
---

### Post by maghajan on 2009-12-01
Hi, 

I am running Xubuntu 9.10 on a Dell server.  I have a monitor attached to it, however, because the computer only has 16MB video memory, the resolution is pretty small.  The system does have 8GB of system memory though.  Is there anyway I can make the computer use some of this system memory as video memory instead?  I don't care if it is a bit slow, I just want more resolution so I can use a larger monitor.  Thanks!

---

### Post by efflandt on 2009-12-02
If video is on the motherboard, there may be a BIOS setting for the max amount of regular RAM to use.  If it is a separate video card with its own video RAM, that RAM is your limitation.

---

### Post by maghajan on 2009-12-17
> **efflandt said:**
> If video is on the motherboard, there may be a BIOS setting for the max amount of regular RAM to use.  If it is a separate video card with its own video RAM, that RAM is your limitation.

Thank you!  Well is it a Dell Poweredge 1950 server.  I am trying to use it as a desktop (please don't ask why, it's just the situation I am in, I know it's not the "right" way to use it).  It has 8gb of system ram, so I'd love to use some of that ram towards the video ram.  The video card is built onto the motherboard, but when I go into the BIOS I don't see such a setting :-(

---

### Post by jerrrys on 2009-12-17
i use a IBM server for a desktop and the on board video supports a whole 16meg of shared ram.  bottom line is that to get good video you got to go with a video card, can't just add ram if its not supported by your on board video.  if yours is like mine, you have PCI-X slots.  which means standard PCI cards will work.  these are old and slow compared to PCI-E, but will give you a big performance boost for say 30 to 50$.  the PNY company still carries them

[http://www3.pny.com/Categories/GeforceGraphics.aspx?Category_ID=13](http://www3.pny.com/Categories/GeforceGraphics.aspx?Category_ID=13)

---

