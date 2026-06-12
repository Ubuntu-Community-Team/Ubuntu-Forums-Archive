---
title: "Default Resolution"
date: 2009-07-09
forum: Multimedia Software
---

### Post by hsachdevah on 2009-07-09
Hi,

I have HP DV6502 notebook.
After installing Ubuntu 9.04, it told me to update drivers for my nVedia graphics card.
This was a gud thing as now I was able to use the resulution of 1280x800.

But the problem is that whenever I restart ubuntu, it goes back in default 800x600 resolution.

Any suggestions on how to fix it?

---

### Post by overdrank on 2009-07-09
> **hsachdevah said:**
> Hi,

I have HP DV6502 notebook.
After installing Ubuntu 9.04, it told me to update drivers for my nVedia graphics card.
This was a gud thing as now I was able to use the resulution of 1280x800.

But the problem is that whenever I restart ubuntu, it goes back in default 800x600 resolution.

Any suggestions on how to fix it?

Hi and welcome, if you use the alt, F2 keys and enter the command ```
gksu nvidia-settings
``` Then set your resolution and save to the xorg. Then you should be good to go on the next reboot. :)

---

### Post by hsachdevah on 2009-07-09
I tried it but of no use. 
This time I get a big nvedia logo during reboot, but the resolution is still 800x600.
I have to change it manually?

When I clicked save to x cofiguration file, there was a checkbox selected. Merge with existing file. Do I have to uncheck it?

---

### Post by overdrank on 2009-07-09
> **hsachdevah said:**
> I tried it but of no use. 
This time I get a big nvedia logo during reboot, but the resolution is still 800x600.
I have to change it manually?

When I clicked save to x cofiguration file, there was a checkbox selected. Merge with existing file. Do I have to uncheck it?

Hi and yes you can select the resolution you want in the nvidia settings and then save to the xorg and you can merge with existing file.

---

