---
title: "NVIDIA GeForce 6150 and Maverick Meerkat"
date: 2010-11-27
forum: Multimedia Software
---

### Post by the dsc on 2010-11-27
Hi ubuntuers.

I'm trying to install GeForce 6150. The first attempt was by going to *system > administration > additional drivers*. Didn't work. It act a bit as if it did, but when I restarted, X wouldn't start. I tried Xorg -config or something, but it wouldn't fix it, some complaints about things like vmwgfx module and incomplete information on xorg.conf. I've unfortunately not made extensive notes on the actual messages. I just wanted to restore X with nv or nouveau, whatever it is called these days, so I could try again, perhaps with nvidia's installer.

I'm a bit suspicious that nvidias requires a xorg.conf to work, with a somewhat defined monitor section. I'm not sure it does, I just have this suspicion becouse of some error messages. Unfortunately the xorg(s) that was/were generated in this process didn't have this section, at least not the ones I saw. 

Do I really need this section, and how can I generate it correctly? On *system > preferences > monitors* it says the monitor is unknown, and before the monitor configuration GUI shows up, there's a dialog asking whether I want to activate the proprietary driver for nvidia: 

> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?



Other doubt that's in my mind. On nvdia's ftp, there are two installers. One that ends on 0.run, and other that ends on 1.run. I couldn't find yet which one I really should run. The README frustratingly mentions "#.run".

Another question more for the sake of curiosity, is the ubuntu's native install, when it works, akin to installing the driver "the debian way", or is it just a shortcut to install it the nvidia's own way?


Thanks for any help.

---

