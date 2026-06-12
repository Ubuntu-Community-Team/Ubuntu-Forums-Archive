---
title: "Disabled Nvidia restricted driver,  can't get to login screen!"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by jonathanmotes on 2007-09-25
I disabled my restricted nvidia driver and now I can't get to the GDM login screen -- I get a screen full of white lines that fade in and out! Is there a way to boot to a terminal and fix things? 

I'm not sure what the problem is...is it that my xorg file needs reconfiguring? (I don't really know how to do that) or is it that my hardware isn't supported by any open source drivers? I had to install ubuntu using the alternate disc because my hardware wasn't well supported by the open source drivers but I was able to boot with them after installing. I had to enable the restricted driver in order to get the correct screen resolution (1440x900) however.

EDIT: I finally got recovery mode to work, so I have a comand line...is there a command I can enter to change my driver back to the restricted one?

Thanks in advance!

---

### Post by 5-HT on 2007-09-26
Replace the video driver (nv, vesa, etc..) listed in your xorg.conf for 'nvidia'.
You may need to reinstall the appropriate nvidia package as well if the module was uninstalled.
cheers,

---

