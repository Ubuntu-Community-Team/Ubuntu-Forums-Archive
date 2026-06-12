---
title: "Module loading help"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by svtcontour on 2008-04-07
I have a Genpix USB module that is loading at different times.  So when I try to use Mythtv, it will be module 2 sometimes, and module 0 other times.

This is what I was told to do.
> Are you sure that your genpix is 2 when i was scanning it was at 0. it seems that is moving around. I would go to modprobes.d and blacklist your genpix module and then I would go to modules and add it there this will let it load last and it will always be 2 use mythtv-setup to edit changes. make sure you select devices virtual for mythtv once you are done scanning so let say you are using 0 to scan once you are done make sure you change it to 3 and etc. 

This is my* LSMOD*

> dvb_usb_gp8psk         16132  9
dvb_usb                25164  1 dvb_usb_gp8psk

I was told to remove it from > modprobes.d and add it to > modules.

How do I do that.   I am not sure what part to put in > modules.

---

### Post by warp99 on 2008-04-08
The modules file is located in /etc. You can do the following to add the line:

```
echo "dvb-usb-gp8psk" | sudo tee -a /etc/modules
```

Then do the following to add the module to your blacklist:

```
echo "dvb-usb-gp8psk" | sudo tee -a /etc/modprobe.d/blacklist
```

Per the instructions that were given.

---

### Post by svtcontour on 2008-04-08
That seems to have worked.  Thanks a bunch.

---

