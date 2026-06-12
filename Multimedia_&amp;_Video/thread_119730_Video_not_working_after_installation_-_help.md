---
title: "Video not working after installation - help"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by rich.za on 2006-01-20
Hey,

I have a Gigabyte 19 inch LCD flat screen. I have installed breezy but when it goes to the desktop the screen just displays lots of colours. Have tried different resolutions, nothing has helped.

The video card I am using is a GeforceFX 6600.

Anyone know what i am doing wrong?

How do I upgrade the video drivers when I can't see anything? 
Or boot into the non-graphical interface?

Thanks,
Rich

---

### Post by hashimoto on 2006-01-20
You can boot to the rescue mode from grub. Press esc during boot to get there. In rescue mode you will be root.

You can reconfigure your Xserver thru console with
```
dpkg -reconfigure xserver-xorg
```

Have your monitor details at hand (resolutions, refresh rates etc)

Can't help with installing drivers for your video card.

---

