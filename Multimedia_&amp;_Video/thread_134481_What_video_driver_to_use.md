---
title: "What video driver to use?"
date: 2006-02-22
forum: Multimedia &amp; Video
---

### Post by xmastree on 2006-02-22
Hi.
I've just aquired a new motherboard, in the shape of an [**Asus K8V-MX**](http://www.asus.com/products4.aspx?modelmenu=2&model=754&l1=3&l2=14&l3=225) which has built-in video. I'm currently using the vesa driver, but I suspect there's a better one available if only I could find out what chip it is. The manual, and the website aren't much help, just stating **Integrated Graphics** :rolleyes: 

I know I ought to install a proper one sometime (nVidia being top of the list) but for now I have to make do with the built in one.

So, how can I identify it? dpkg-reconfigure xserver-xorg can't detect it, and offers me the list to choose from.

---

### Post by sharke on 2006-02-22
I think your graphics may be Graphics Controller, VIA UniChrome Pro K8M800 
Regards
Sharke

---

### Post by xmastree on 2006-02-22
Hmm... I tried the via driver, but that didn't work. I guess I'll just live with it until I get a proper card.

Thanks anyway.

---

### Post by abel on 2006-02-22
Hey XmasTree,

Without you knowing you helped me fix my Serial mouse issue . As a Ubuntu noob I'll try to help when I can.

Did you try the driver at:

[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=K8V-MX](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=K8V-MX)

Just wondering. There seems to be a few Linux related drivers in the list for the motherboard.

:) 

abel

---

### Post by xmastree on 2006-02-23
> Without you knowing you helped me fix my Serial mouse issue. \\:D/ 

Thanks, I hadn't seen that. However, the vga driver is aimed towards redhat 9, and xf86 rather than xorg. I gave it a go anyway, but couldn't install it.

Instead I 'borrowed' the GeForce 4 from my old computer... :rolleyes:

Strange things are happening though, since I replaced the motherboard. My desklets keep dying, and my panels tend to fall over too... :-k 

Time to reinstall/upgrade to breezy I guess.

---

