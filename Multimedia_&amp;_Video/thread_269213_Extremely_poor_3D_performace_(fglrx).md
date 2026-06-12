---
title: "Extremely poor 3D performace (fglrx)"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by squimmy on 2006-10-01
Hello,

I have a X800 GTO2 and *was* using the fglrx drivers that are in the repository( 8.25.18 ). I follwed[ this guide.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29") Back then I was getting around 7000 fps in glxgears.

I then decided I should install the later ( 8.29.6 )drivers so I followed method 2 of that same page. *I didn´t uninstall anything inbetween the driver installations,but I did install XGL/Beryl*

Anyway,I was, with the old drivers, getting almost double the performance that I am now getting. I not running XGL/Beryl right now, and I on display 0:0, so that&#347; not the problem. So how can I fix this performance issue?


Thanks for any help given!

---

### Post by Melcar on 2006-10-01
Did you removed your old .deb files (the ones from the older driver)?

---

### Post by squimmy on 2006-10-01
Damn it, just realised i said 2D performance. I mean 3D performance! :(

Anyway, no I didn´t remove any of the debs. How would I now remove the current fglrx installation? I think I should try an uninstall-reinstall.

---

### Post by tseliot on 2006-10-01
> **squimmy said:**
> Damn it, just realised i said 2D performance. I mean 3D performance! :(


I have edited the title of the thread. Now it says 3d instead of 2d

---

### Post by squimmy on 2006-10-01
Thanks! :)

---

### Post by squimmy on 2006-10-01
Does anybody know how to uninstall fglrx? It can be that hard! I´m getting desperate!

---

### Post by mygom on 2006-10-01
Well, there is the /usr/share/fglrx/fglrx-uninstall.sh script.

---

### Post by posey on 2006-10-01
The current ATI drivers are buggy, which is the cause of your poor 3D performance.

---

### Post by squimmy on 2006-10-03
Well, I found some ati entries in synaptic and removed them. Now X refuses to start the GUI, instead preferring to show me an ugly command line interface.

I tried editing the xorg.conf file and changing the driver section from fglrx to ati, radeon and vesa. All to no avail.

God X can be a pain.

---

### Post by Aikon- on 2006-10-03
If you've uninstalled the ATI drivers through synaptic, then of course X won't be able to find them; try changing the driver to "VESA" and see if that will let you boot into X again (though it won't have 3D acceleration).

---

