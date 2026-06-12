---
title: "Possible to get dual monitors + 3d accleration with Intel GMA900?"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Fox5 on 2007-11-13
My laptop has a gma900 graphics chip in it, and with a single screen 3d acceleration was working fine with the intel experimental modesetting drivers. However, these drivers apparently did not give an option for dual monitor output. I switched to the i810 drivers instead, however they don't seem to support 3d acceleration. Anyway to get both?

---

### Post by petay on 2007-11-13
I have the same problem on my dell laptop with internal intel graphics card. I am using the 810i driver and have got compiz-fusion working to a fair level (it gets a bit slow with a transparent 3d cube!!) I tried messing with the screens and gaphics tool yesterday to try and enable dual screen, works fantastic on clone, but as soon as i try to enable the second screen as an extended desktop it screws everything up. after much flickering and console messages it gives me an 600x400 screen on the laptop screen with a message telling me that ubuntu is running in low graphics mode. just if anyone needs it here is my graphics card.
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Im sure there is a way to get this working, but it seems the screens and graphics dialogue is struggling, or the intel driver aint up to it.

---

### Post by aj_cheema69 on 2007-11-25
Hey guys I'm by no means an expert but I was able to clone with an external monitor from my laptop, but thats the best I can do. To get back to your original screen resolution petay you can type in the following to reconfigure your /etc/X11/xorg.conf file. Simply type the following into terminal.

sudo dpkg-reconfigure -phigh xserver-xorg

If you run that you should be able to reconfigure xserver. But I have had no luck with extended desktop. I hope that helped.

---

### Post by Fox5 on 2007-11-25
> **aj_cheema69 said:**
> Hey guys I'm by no means an expert but I was able to clone with an external monitor from my laptop, but thats the best I can do. To get back to your original screen resolution petay you can type in the following to reconfigure your /etc/X11/xorg.conf file. Simply type the following into terminal.

sudo dpkg-reconfigure -phigh xserver-xorg

If you run that you should be able to reconfigure xserver. But I have had no luck with extended desktop. I hope that helped.

It's a shame too, dual monitors are really nice but the driver that supports them (i810) has horrible 2d and 3d performance.

---

