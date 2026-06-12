---
title: "1024 x 768 is all I can get"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by arthur on 2006-05-27
My problem:
**The screen shows clearly at 1024x768, but all resolutions beyond that are unreadable.**

I am using an HP Pavilion ZT3115EA Laptop with an ATI Radeon 9200 card, together with a Samsung 913V TFT Monitor.

I have tried to install the ATI-specific driver following this how-to (found in our forums):
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

but now everything is messed up. Session opens normally, but an error screen is displayed telling me "Not an optimum config ...", and then the screen simply goes black.

Have tried to install through EasyUbuntu, but no luck (the application simply closes).

Automatix does not include ATI drivers.

The monitor is 2 hours old, and I would hate to be forced to use Windblows ( picture quality is amazing here at resolutions way beyond 1024x768 ).

Can anybody help?

](*,)

---

### Post by IYY on 2006-05-27
There's a file you need to edit. In the terminal, run

```
sudo nano /etc/X11/xorg.conf
```

Be careful, if you mess this file up, you wouldn't have to log back in graphical mode until you fix it. So, first back it up:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

In the "Monitor" section, you'll need to set your HorizSync and VertRefresh rates. These can be found in your monitor's manual (it's new, so you should have one).

IN the "Screen" section, there's a list of resolutions. Add the ones you want to the subsection you are using (defined by the DefaultDepth variable, usually 24).

---

### Post by arthur on 2006-05-27
Absolutely! :D 
How could it be so simple? I thought there was much more to it than the good old video conf. file.
Many thanks, it all looks beautiful now at a whopping 1280x1024 resolution. Beautiful, not just readable :KS .

Many thanks!

---

