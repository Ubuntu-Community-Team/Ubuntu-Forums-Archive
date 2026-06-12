---
title: "X won't display on DVI using fglrx driver"
date: 2008-06-23
forum: Multimedia Software
---

### Post by charwhee on 2008-06-23
I have a weird problem (happens under both ubuntu and xubuntu). I can't get X to work when I plug my monitor into my computer using the DVI cable. Is there something that I need to add to xorg.conf so that it will work?

If I switch to the first console, I can see that the signal is actually getting to the monitor, and can log in without a GUI. 

When I plug the VGA cable in, everything works, but X misidentifies the screen mode/resolution, which should be 1280 x 1024, even though it is specified.

I can post my xorg.conf and the log, although there are no errors in the log. I was just hoping that there was something I needed to specify in order to use a DVI connector.

Video Chipset: ATI xpress200 integrated

I originally thought the VESA driver was being used but when I open a console and do fglrxinfo or look at the proprietary drivers in the system menu, it looks like fglrx has been loaded and is functioning.

---

