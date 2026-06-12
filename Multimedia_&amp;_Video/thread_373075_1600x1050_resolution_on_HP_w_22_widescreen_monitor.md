---
title: "1600x1050 resolution on HP w 22 widescreen monitor"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by pn8830 on 2007-02-28
Hello,

I'm trying to configure an HP w 22 widescreen monitor with 1600x1050 resolution. The Screen Resolution tool have maximum of 1024x768. How can I configure that?

I tried adding it to xorg.conf but did not seem to work.

        SubSection "Display"
                Depth           24
                Modes           "1600x1050" "1024x768" "800x600" "640x480"
        EndSubSection

Thank You,
PN.

---

### Post by pn8830 on 2007-02-28
Checked /var/log/Xorg.0.log
Found this:


(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce 7500 LE found
(II) resource ranges after xf86ClaimFixedResources() call:
...
(II) NV(0): Monitor name: HP w22
(II) NV(0): Serial No: CNT641Z14K

It looks like it's detecting the card and the monitor.

---

### Post by pn8830 on 2007-03-01
Actually I made a mistake in the subject. The desired resolution is 1680x1050.
I tried removing xorg.conf and I it working at 1600x1000 but it's not what the optimal resolution is. The optimal is 1680x1050.


anyone?

---

### Post by pn8830 on 2007-03-02
I managed to overcome this problem by installing the proprietary driver 1.0-9746 from nVidia site.

PN.

---

### Post by warjowuch on 2007-03-02
Nice you've got it working!
But... you removed your whole xorg.conf?? Did your X even start?? Seems very odd to me!

---

### Post by pn8830 on 2007-03-02
Yes it does sound odd but it works and not for the first time for me.

I discovered it long ago and I'm not really sure why it works. It was just a desperate attempt to bring up X on other PC. X does start without xorg.conf and sometimes it with better results. Like in this case it came up with 1600x1000 resolution with the original driver, not the optimal one for this monitor but still better then 1024x768. Probably it does some probing that gives better results then configured in xorg.conf.

BTW the other question that I could not resolve is that how to find out the configuration that X generates running without xorg.conf. That might help in the future.

---

