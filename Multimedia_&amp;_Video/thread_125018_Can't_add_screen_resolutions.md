---
title: "Can't add screen resolutions"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by leach on 2006-02-02
Hello, I'm having a bit of a problem and I know questions about increasing your screen resolution get posted all the time but for some reason running "dpkg-reconfigure xserver-xorg" never works. I've gone through it many times and have looked and given it the exact horiz and vert refresh rates for my monitor and everything, Still anything higher than 800x600 is unavalible.
I know my graphics card and monitor can support higher is there anyway to force it to use a higher screen resolution? Thanks.

---

### Post by mishranurag on 2006-02-02
When you go through the process of reconfiguring, the system asks you about the resolutions your monitor can support. Mark "only" the highest possible resolution, your monitor can support.

Anurag

---

### Post by leach on 2006-02-02
I just tried it and rebooted, it had no effect at all.

---

### Post by mishranurag on 2006-02-02
Does your monitor need nvidia drivers? If yes, you might need to install that.
Also, when you reconfigure the system, what options do you get for screen resolution? Remember to select a resolution you need space bar and same to deselect. You need to select "only" the highest one your monitor can support (1280 x 1024). If others are selected by default, deselect them.

Anurag
[quote=leach]I just tried it and rebooted, it had no effect at all.[/quote]

---

### Post by aysiu on 2006-02-02
[This](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has every trick and tip to get screen resolution fixed.

---

### Post by leach on 2006-02-03
I think I may have an integrated intel graphics chip but I'm not sure, I know my motherboard is an intel made, regardless- Most of these solutions (thank you by the way for the link aysiu) involve use of the program 855resolution however when I try to run the specified command "sudo 855resolution -l" I get the error- 

> Chipset: Unknown (0x71928086)
Unknow VBIOS structure

and that's it, is there something I'm missing? Thanks Again.

---

### Post by leach on 2006-02-09
I was finally able to achieve a higher resolution by setting my color depth to 16. The only problem is that now everything appears to be squished, for example, instead of 1280x1024 it is 1280x800 what would cause this?

---

