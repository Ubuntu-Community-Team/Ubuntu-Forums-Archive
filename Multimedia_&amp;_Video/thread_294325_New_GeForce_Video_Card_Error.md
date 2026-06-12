---
title: "New GeForce Video Card Error"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by Sierra_Dave on 2006-11-06
Hi,
I upgraded from ATI RAGE Pro to Nvidia Geforce TI 64mb and everything went fine except I get xserver error and cant get gnome running.  I am running an older Compaq Deskpro 600 Mhz MB agp2.  It still shows ati card in the window and then defaults to command prompt.

Should I have intalled the Nvidia driver then installed the card?  Or is there a way to get the system running using a generic driver?  How do I switch at this stage:

bob@desktop:$

Thanks for any guidance!

---

### Post by Joe_CoT on 2006-11-06
You're still using the ati driver.
```
sudo nano -w /etc/X11/xorg.conf
```

look for
```

Section "Device"
Identifier  "blah"
Driver      "blah"

```

I don't know what your identifier or driver will be (ati, or radeon, or fglrx), but change the driver to nvidia and you should start fine.

---

### Post by Sierra_Dave on 2006-11-06
Well, that almost worked but I dont have the nvidia driver module,which when I rebooted the xserver error screen reported.

Can I download that onto a floppy and add it? using nano editor?

Thanks!

---

### Post by Joe_CoT on 2006-11-06
Sorry, should be nv to use the open-source one (by bad).

If that doesn't work (which may happen), vesa will definately work, just not give you all the bells and whistles you want. You can install the nvidia binary later once you actually have X.

---

### Post by Sierra_Dave on 2006-11-06
Wooohooooooooo Thanks Joe!  Worked!

---

