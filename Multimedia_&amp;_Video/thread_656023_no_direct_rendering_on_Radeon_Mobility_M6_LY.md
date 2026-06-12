---
title: "no direct rendering on Radeon Mobility M6 LY"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by soviet911 on 2008-01-02
Hi i got an old HP omnibook with Gutsy on it and Radeon Mobility M6 LY, the problem is as stated above the direct rendining is not working 
soviet911@Soviet911:/$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I tried both Radeon and ATI drivers nether helped, sigh. can some one help me. Thanks!

---

### Post by tgilber1 on 2008-01-02
Are you using the Ubuntu xorg drivers or ATI's proprietary drivers?  The xorg drivers have limited features -  [http://www.x.org/wiki/radeonhd/](http://www.x.org/wiki/radeonhd/).

If you haven't yet, try out the proprietary version for 2/D3D effects and DRI.

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Realize, if you do use the proprietary drivers, you must edit the /etc/default/linux-restricted-modules-common file by adding fglrx to the DISABLED_MODULE to prevent any conflict with Ubuntu's fglrx driver and the proprietary version.  In any event, the installation instructions can be found in these forums.

---

### Post by soviet911 on 2008-01-03
Thanks but after googling some more i came onto a tut how to turn on the direct Rending on this exact card,so no it works like a charm thanks.

---

### Post by jogeer on 2008-01-04
I dealing with this same problem. Would you mind posting a link to the tutorial that helped you?

---

