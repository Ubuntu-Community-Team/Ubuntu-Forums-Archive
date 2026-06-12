---
title: "Installed Ubuntu 12.10, and my graphics card isn't detected?"
date: 2013-02-10
forum: Multimedia Software
---

### Post by zking on 2013-02-10
I switched to Ubuntu 12.10 from Windows 7. When I used Win7, "aero" worked perfectly and everything was fine in terms of graphics drivers. 

On ubuntu, when I go to About This Computer >> Graphics, it says "Graphics: Unknown", and "Experience: Standard".  I don't think Ubuntu is detecting my graphics driver for some reason, or perhaps it can't find drivers for it.

My graphics/video card is ATI Radeon X600. Worked fine with Windows 7 and everything was fast.

I think, for this very reason, Ubuntu is not running as fast as it should. It's not as snappy as Windows 7 and I feel like I'm not getting the full graphical experience.

Is there anything I can do? When I go to settings >> additional drivers, it says "no proprietary drivers are in use." There's no driver to choose from. 

Thanks!

---

### Post by Yellow Pasque on 2013-02-10
That's a common bug with the unity info program. Installing mesa-utils package will probably make it say something more specific than 'Unknown' (but that won't change the way the system functions).

> it says "no proprietary drivers are in use." There's no driver to choose from. 
That is correct. The open-source radeon driver is used by default and no proprietary drivers support the card.

---

